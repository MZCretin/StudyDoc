## 1、前言

歇后语大全查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，可查询歇后语信息。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=36

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是**临时秘钥**，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 查询歇后语信息

- 接口地址： https://www.mxnzp.com/api/xiehouyu/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/xiehouyu/search?key=小葱拌豆腐&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 根据内容查询歇后语信息，可使用至少两个字的模糊查询

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "riddle": "小葱拌豆腐",
              "answer": "一清（青）二白"
          }
      ]
  }
  
  ```

### 2.2 随机返回一个歇后语

- 接口地址： https://www.mxnzp.com/api/xiehouyu/random

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/xiehouyu/random?app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 随机返回一个歇后语的信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  {
              "riddle": "小葱拌豆腐",
              "answer": "一清（青）二白"
       }
  }
  ```

