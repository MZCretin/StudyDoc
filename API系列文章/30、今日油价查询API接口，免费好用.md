## 1、前言

今日油价查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，可查询指定省份的今日油价信息。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=34

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是**临时秘钥**，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 今日油价查询

- 接口地址： https://www.mxnzp.com/api/oil/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/oil/search?province=广东&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 查找对应省份的今日油价信息

- 返回示例：

  ```json
  {
      "code":1,
      "msg":"数据返回成功！",
      "data":{
          "province":"广东",
          "t0":"7.64",
          "t89":"7.42",
          "t92":"7.99",
          "t95":"8.65",
          "t98":"9.79"
      }
  }
  ```
