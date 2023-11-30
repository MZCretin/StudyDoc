## 1、前言

电话区号信息查询接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能实现获取世界电话区号列表。这个接口的特点是数据会经常更新。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=6

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 世界电话区号列表

- 接口地址： https://www.mxnzp.com/api/phone_code/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/phone_code/list?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取世界电话区号列表

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "zhCn": "中国",
              "enUs": "China",
              "phoneCode": "+86"
          },
          {
              "zhCn": "澳门",
              "enUs": "Macao",
              "phoneCode": "+853"
          },
          {
              "zhCn": "阿富汗",
              "enUs": "Afghanistan",
              "phoneCode": "+93"
          }
        	...这里只显示了三条数据...
      ]
  }
  ```

