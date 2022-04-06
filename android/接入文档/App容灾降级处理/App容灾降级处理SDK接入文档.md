## 1、背景

基于上次应用上线，打开探索页面必然崩溃的事故，开发了此崩溃容灾降级SDK。当配置特定页面之后，可以实现即使抛出致命异常应用不会闪退，当异常次数达到配置的次数时，还能实现跳转安全页面，引导用户下载最新的bug修复包。

它最大的用处是能减少应用线上的崩溃率。

## 2、接入步骤

### 2.1 引入sdk

这一块后面写，还没上传到maven仓库

### 2.2 初始化sdk

#### 2.2.1 全局初始化

```kotlin
fun init(context: Application, config: CrashHelperConfig)
```

#### 2.2.2 config配置项说明

| 方法名称                  | 参数类型            | 参数说明                                                     | 方法备注                                                     |
| ------------------------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| setBaseUrl                | 字符串              | 说明：目前debug和release环境下都可以使用：http://log.mxnzp.com/pro_api/ | 设置获取bug修复包信息的接口url                               |
| setDebug                  | boolean             | 设置debug模式                                                | debug模式下会自动输出操作日志，TAG为CMCrashHelper            |
| setOtherPageCrashMaxCount | int                 | 设置不在白名单内的页面的最大崩溃次数                         | 达到次数之后会跳转安全页面                                   |
| setNoticeActivityClass    | Activity的Class对象 | 你自定义的安全页面Activity                                   | 设置安全页面的Activity 必须继承自 CMCrashHelperActivity      |
| addPageConfig             | PageConfig          | 页面配置信息，PageConfig有三个成员变量<br/>className 页面名称<br/>type 崩溃处理类型<br/>     PageHandlerTypeCrashUntilSafe 达到次数之前一直崩溃 <br/>    PageHandlerTypeIgnoreUtilSafe 达到次数之前一直忽略错误 <br/>times 次数阈值 | 这些页面信息将会加入白名单                                   |
| addCrashCallback          | 回调接口            | 回调信息包括Throwable和Thread                                | 这里会回调项目中所有未被捕获的异常信息，可以在这里进行日志的处理和上传操作 |
| addLogDataCallback        | 回调接口            | 回调信息为日志信息                                           | 可以在此查看日志和处理日志，跟环境无关                       |



#### 2.2.3 代码示例

```kotlin
CMCrashHelper.init(this, CrashHelperConfig.create().apply {
            //设置提交BASE_URL
            setBaseUrl("http://log.mxnzp.com/pro_api/")
            //设置debug
            setDebug(true)
            //设置不在白名单内的页面的最大崩溃次数
            setOtherPageCrashMaxCount(5)
            //设置安全页面的Activity 必须继承自 CMCrashHelperActivity
            setNoticeActivityClass(NoticeActivity::class.java)
            //设置页面白名单配置
            addPageConfig(
                PageConfig(
                    MainActivity::class.java.simpleName,
                    PageHandlerType.PageHandlerTypeIgnoreUtilSafe,
                    5
                )
            )
            addPageConfig(
                PageConfig(
                    SecondActivity::class.java.simpleName,
                    PageHandlerType.PageHandlerTypeCrashUntilSafe,
                    5
                )
            )
            addPageConfig(
                PageConfig(
                    TestFragment::class.java.simpleName,
                    PageHandlerType.PageHandlerTypeIgnoreUtilSafe,
                    3
                )
            )
            //添加异常信息捕获
            addCrashCallback { e, t ->

            }
            //添加日志回调
            addLogDataCallback {

            }
        })
```

### 2.3 混淆处理

```properties
-keep class com.codemao.cmcrashhelper.bean.UpdateInfoResp
```

## 3、如何定制安全页面

安全页面是崩溃次数达到一定值之后跳转的说明页面，旨在给用户一些提示信息，顺便在给用户提供更新apk的入口，在这个页面

```kotlin
import android.content.Intent
import android.net.Uri
import android.view.View
import android.widget.Button
import com.codemao.cmcrashhelper.ui.CMCrashHelperActivity

class NoticeActivity : CMCrashHelperActivity() {

    //设置当前页面的布局文件
    override fun getLayoutId(): Int = R.layout.activity_notice

    override fun afterSetContentView() {
        //getLastCrashInfo这个方法可以获取最近一次崩溃的信息 方便你上传或者是展示给用户
        getLastCrashInfo { e, t ->
            //do something
        }

        //伪代码 在这里先检测系统有么有版本更新
        CMUpdateHelper.checkUpdate() { hasUpdate ->
            if (!hasUpdate) {
                //getUpdateInfo 是基类 CMCrashHelperActivity 提供的 getUpdateInfo的第一个参数是包名，不传入sdk会自动获取包名
                getUpdateInfo("com.roll.codemao") { hasUpdate, apkUrl, response ->
                    if (hasUpdate) {
                        //这是页面中的去更新按钮
                        findViewById<Button>(R.id.btn_click).apply {
                            //显示此按钮
                            this.visibility = View.VISIBLE
                            //点击跳转浏览器下载apk
                            this.setOnClickListener {
                                val uri: Uri = Uri.parse(apkUrl)
                                val intent = Intent(Intent.ACTION_VIEW, uri)
                                startActivity(intent)
                            }
                        }
                    }
                }
            }
        }
    }
}
```

