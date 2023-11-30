## 1、前言

域名ICP备案查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，可查询指定域名的备案信息。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=33

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 获取域名备案信息

- 接口地址： https://www.mxnzp.com/api/beian/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/beian/search?domain=bXhuenAuY29t&app_id=rkkpflimunbjzeki&app_secret=SHI3cDNEQTRXOHNnYmxiallNeEM3Zz09

- 接口备注： 查找对应域名的备案信息，请注意，domain参数需要base64后传入

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "domain": "mxnzp.com",
          "unit": "穆仙念",
          "type": "个人",
          "icpCode": "鄂ICP备17026449号-2",
          "name": "首页 - MXNZP.COM 穆仙念，人",
          "passTime": "2021-08-13"
      }
  }
                 
  ```
