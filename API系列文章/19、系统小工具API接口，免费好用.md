## 1、前言

系统小工具接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了3个小接口，可生成长短不重复id，可获取服务器标准时间。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=23

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 获取不重复长ID

- 接口地址： https://www.mxnzp.com/api/tools/no_repeat_id/long

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/tools/no_repeat_id/long?app_id=gwytpwfqthfkor6i&app_secret=R0FHQm0veXdxaXVORDdVYzErL1hxUT09

- 接口备注： 获取不重复长ID信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "id": "8a2a789976e64a1c9455ebd90853d4c6"
      }
  }
  ```

### 2.2 获取不重复短ID

- 接口地址： https://www.mxnzp.com/api/tools/no_repeat_id/short

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/tools/no_repeat_id/short?app_id=gwytpwfqthfkor6i&app_secret=R0FHQm0veXdxaXVORDdVYzErL1hxUT09

- 接口备注： 获取不重复短ID信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "id": "jlazntmtjrvcrpnb"
      }
  }
  ```

### 2.3 获取服务器时间

- 接口地址： https://www.mxnzp.com/api/tools/system/time

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/tools/system/time?app_id=gwytpwfqthfkor6i&app_secret=R0FHQm0veXdxaXVORDdVYzErL1hxUT09

- 接口备注： 获取服务器时间

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "time": 1562063265883
      }
  } 
  ```

  
