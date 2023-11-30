## 1、前言

垃圾分类查询接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能实现查询指定垃圾的分类，可作为信息查询类的应用的一个新功能接入。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=14

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 查询垃圾分类信息

- 接口地址： https://www.mxnzp.com/api/rubbish/type

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/rubbish/type?name=西瓜&app_id=czpq0qfmlphehno1&app_secret=WkcwUW12TW11bkEzVnVBSjNFUGVCUT09

- 接口备注： 查询指定物品垃圾分类信息。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "aim": {
              "goodsName": "西瓜",
              "goodsType": "湿垃圾"
          },
          "recommendList": [
              {
                  "goodsName": "西瓜霜含片塑料铝箔包装",
                  "goodsType": "有害垃圾"
              },
              ...这里就显示了一个...
          ]
      }
  }
  
  
  ```
