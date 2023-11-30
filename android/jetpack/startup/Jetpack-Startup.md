> 新搭建的博客主站，更多文章请访问：[http://blog.mxnzp.com](http://blog.mxnzp.com/)

## 1、前言

可能做过一些SDK的朋友知道，为了让调用方爽，一般在定义SDK的方法的时候，都会尽量少让调用方传入Context参数，一来是是方法显得笨重，并且传给你的Context使用不当可能会内存泄漏，二来你可能永远猜不到调用方会在什么奇怪的地方调用你的方法，他可能为了给你这个Context，历经千辛万苦。所以我们一般会提供一个全局的Init方法，让调用方在Application的onCreate方法中初始化，传给我们Context，SDK内部存储。

### 1.1 带来的问题？

你会发现大一点的项目，Application的onCreate方法下会有很多很多的init方法，看着着实让人难受。那么针对这种情况有没有什么优化方案呢？

### 1.2 历史优化方案？

我们会通过注册ContentProvider来提前初始化SDK，自定义一个ContentProvider并让它继承自ContentProvider，然后我们在onCreate()方法中去初始化我们的SDK，并拿到Context，就不需要让用户自主初始化了，实现悄悄初始化的操作。这种操作看起来是不是很骚？但是其实有很多SDK都采用了这种方案，比如Facebook的库，Firebase的库，还有我们所熟知的WorkManager，Lifecycles等等。

### 1.3 已经到极致了吗？

通过ContentProvider的方式是解决了必须要显式初始化SDK的问题，但是它也带来了其他问题：

+ ContentProvider是一个很重的组件

  ContentProvider是Android四大组件之一，注册ContentProvider之后会拖慢整个APP的启动速度，对性能有影响，尤其是当每个SDK都采用这种方式的时候，性能损耗是成倍增加的，虽然有的SDK的初始化就只是为了拿一个Context。

+ 应用启动就初始化SDK

  有被各个应用市场的隐私协议支配过的朋友应该知道，如果你的SDK获取了用户的隐私信息，你是必须要用户同意隐私权限之后才能使用的，否则审核会被拒，那么使用ContentProvider这种方式就不合理了，我们需要由用户来决定什么时候初始化SDK。

所以，今天的主角来了，它就是Jetpack的Startup组件。

## 2、Startup是什么？能干什么？

### 2.1 Startup是什么？

**先来点官网介绍：**

> The App Startup library provides a straightforward, performant way to initialize components at application startup. Both library developers and app developers can use App Startup to streamline startup sequences and explicitly set the order of initialization.
>
> Instead of defining separate content providers for each component you need to initialize, App Startup allows you to define component initializers that share a single content provider. This can significantly improve app startup time.

**再来点有道翻译：**

> App Startup库提供了一种简单、高效的方法来在应用程序启动时初始化组件。库开发人员和应用程序开发人员都可以使用app Startup来简化启动序列，并显式设置初始化顺序。
>
> 与为需要初始化的每个组件定义单独的内容提供程序不同，App Startup允许定义共享单个内容提供程序的组件初始化程序。这可以显著提高应用启动时间。

**最后来点大白话：**

它就是通过开启一个ContentProvider来统一管理所有应用和SDK的初始化工作的管理中心，包括组件的立即初始化，延迟初始化，设置初始化顺序等，既能让SDK隐式初始化，还能减少多ContentProvider的初始化，提升整体性能。

### 2.2 Startup能干什么？

+ **它能隐式初始化SDK，给你Context**

  内部也是一个ContentProvider，不过无论有多少的SDK依赖了它，它也只会初始化一个ContentProvider，这就解决了之前初始化多ContentProvider带来的性能问题。

+ **它提供了延迟初始化功能**

  它提供了延迟初始化功能，当你不需要启动就立即初始化的时候，这个功能可以让你在任何位置手动初始化。

+ **保证单次初始化**

  它内部记录了SDK的初始化状态，防止多次调用重复初始化的问题。

+ **设置初始化顺序**

  每个SDK初始化的时候，都可以指定它依赖的其他SDK，并设置初始化顺序，达到先初始化依赖SDK再初始化自己的效果

## 3、Startup怎么用？

### 3.1 引入依赖

```groovy
dependencies {
    //最新版本请看官方文档：https://developer.android.com/reference/kotlin/androidx/startup/AppInitializer
    implementation "androidx.startup:startup-runtime:1.1.0" //这里目前最新的版本是1.1.0 
}
```

### 3.2 自定义组件

自定义组件实现Initializer接口，重写create()方法和dependencies()方法，在create()里面可以进行初始化，dependencies()是当前组件依赖的其他组件列表，如果返回一个非空列表，那么组件将会优先按顺序初始化其他组件，最后初始胡当前自定义组件。

```kotlin
class StartupLibInitializer : Initializer<Unit> {

    override fun create(context: Context) {
        StartupInit.init(context)
    }

    override fun dependencies(): MutableList<Class<out Initializer<*>>> {
        return mutableListOf()
    }
}
```

为了模拟SDK的实际开发流程，顺便写了一个StartupInit：

```kotlin
/**
 * 初始化
 */
@SuppressLint("StaticFieldLeak")
object StartupInit {

    //全局存储context
    private var context: Context? = null

    /**
     * 模拟初始化
     */
    fun init(context: Context): StartupInit {
        Log.e("HHHHHH","StartupInit被初始化了")
        this.context = context
        return this
    }
}
```

### 3.3 注册组件

Startup的本质是ContentProvider，所以需要在清单文件的application中注册：

```xml
<application>
  ...
  <provider
            tools:replace="android:authorities"
            android:name="androidx.startup.InitializationProvider"
            android:authorities="com.roll.startuplibrary.androidx-startup"
            android:exported="false"
            tools:node="merge">
    <meta-data  android:name="com.roll.startuplibrary.StartupLibInitializer"
               android:value="androidx.startup" />
  </provider>
</application>
```

可以先不关注其他的细节，大致就是在provider中使用meta-data注册你刚刚写的组件。

### 3.4 查看效果

启动App，将会打印如下内容：

```java
2021-10-27 14:19:06.275 17974-17974/com.roll.demo E/HHHHHH: StartupInit被初始化了
```

## 4、高级使用

### 4.1 注册组件的tools:node说明

tools:node有两个常用的可选值，一个是merge，一个是remove

+ tools:node="merge"

  这个常用于provider节点，确保清单合并工具正确地解决任何冲突项。

+ tools:node="remove"

  这个常用于meta-data节点，用于告知当前meta-data，我要删除这个meta-data，不使用默认启动就初始化的方式。打个比方，你集成了一个SDK，它是那种一启动就会初始化的，但是你不希望这样，你希望的是在某个特殊场景才需要初始化，那么你可以使用remove，将默认行为取消掉，这个SDK就不会自动初始化了。

### 4.2 依赖其他SDK

为了验证这个效果，我分别定义了4个组件，TestInitializer，Test1Initializer，Test2Initializer，Test3Initializer，分别如下，其中，要注意的是：

+ TestInitializer 依赖了Test1Initializer和Test2Initializer，**并且Test1Initializer是在Test2Initializer前面的**
+ Test1Initializer 没有依赖其他东西
+ Test2Initializer 依赖了Test3Initializer
+ Test3Initializer 没有依赖其他东西

```kotlin
class TestInitializer : Initializer<Unit> {

    override fun create(context: Context) {
        Log.e("HHHHH","TestInitializer触发")
    }

    override fun dependencies(): MutableList<Class<out Initializer<*>>> {
        return mutableListOf(Test1Initializer::class.java,Test2Initializer::class.java)
    }
}


class Test1Initializer : Initializer<Unit> {
    override fun create(context: Context) {
        Log.e("HHHHH","Test1Initializer初始化")
    }

    override fun dependencies(): MutableList<Class<out Initializer<*>>> {
        return mutableListOf()
    }
}

class Test2Initializer : Initializer<Unit> {
    override fun create(context: Context) {
        Log.e("HHHHH","Test2Initializer初始化")
    }

    override fun dependencies(): MutableList<Class<out Initializer<*>>> {
        return mutableListOf(Test3Initializer::class.java)
    }
}

class Test3Initializer : Initializer<Unit> {
    override fun create(context: Context) {
        Log.e("HHHHH","Test3Initializer初始化")
    }

    override fun dependencies(): MutableList<Class<out Initializer<*>>> {
        return mutableListOf()
    }
}
```

注册组件：

```xml
<application>
  ...
  <provider
            android:name="androidx.startup.InitializationProvider"
            android:authorities="${applicationId}.androidx-startup"
            android:exported="false"
            tools:node="merge"
            tools:replace="android:authorities">
    <meta-data
               android:name="${applicationId}.TestInitializer"
               android:value="androidx.startup" />
  </provider>
</application>
```

我们**只注册了**TestInitializer，但是因为他们各自的依赖关系，我们四个组件都会被注册，启动APP，打印如下：

```java
2021-10-27 14:41:29.479 20566-20566/com.roll.demo E/HHHHH: Test1Initializer初始化
2021-10-27 14:41:29.479 20566-20566/com.roll.demo E/HHHHH: Test3Initializer初始化
2021-10-27 14:41:29.479 20566-20566/com.roll.demo E/HHHHH: Test2Initializer初始化
2021-10-27 14:41:29.479 20566-20566/com.roll.demo E/HHHHH: TestInitializer触发
```

**说明：**

因为TestInitializer依赖了Test1Initializer和Test2Initializer，且Test1Initializer在前面，所有优先初始化Test1Initializer，Test2Initializer中依赖了Test3Initializer，所以初始化Test2Initializer的时候优先初始化Test3Initializer，之后再初始化Test2Initializer自己，最后初始化TestInitializer。

### 4.3 延迟初始化

如果我们的SDK不需要提前初始化，我们可以不在provider中注册，而使用手动注册的方式，手动注册的方式如下：

```kotlin
AppInitializer.getInstance(context)
    .initializeComponent(TestInitializer::class.java)
```

## 5、结语

虽然说Startup只是把我们之前的思想做了一层封装，但是效果还是很明显的，尤其在性能上做出了很大的优化，还是值得推荐的。

不过凡事都不是绝对的，比如你只是在做app应用层的业务，完全就没有必要使用Startup来进行初始化，得不偿失，相比较于库开发者，这个组件用处就会比较大。

项目地址：[https://github.com/MZCretin/JetpackStartup](https://github.com/MZCretin/JetpackStartup)


> 专业广告位：
> 欢迎访问我的个人主页：[https://www.mxnzp.com](https://www.mxnzp.com)
> 新搭建的博客主站：[http://blog.mxnzp.com](http://blog.mxnzp.com/)
> Github地址：https://github.com/MZCretin

