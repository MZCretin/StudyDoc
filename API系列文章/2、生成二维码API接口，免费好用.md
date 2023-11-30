## 1、前言

生成二维码接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，能实现生成单一二维码和生成带logo的二维码功能。这个接口的主要特点是，能定制二维码的宽高，可返回二维码的下载链接或者base64的字符串。

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 生成单一二维码

- 接口地址： https://www.mxnzp.com/api/qrcode/create/single

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/qrcode/create/single?content=你好&size=500&type=0&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 根据传入的内容生成二维码，可以选择获取二维码下载链接，也可以直接获取图片的Base64字符串自己解析（注：Base64字符串前面默认添加了“data:image/jpg;base64,”，取值的时候请根据需要对这个内容进行处理）。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "qrCodeUrl": "http://www.mxnzp.com/api_file/qrcode/7/2/d/d/0/9/a/e/327588b1ddb44cf7a95e43d7ad2f5b90.png",
          "content": "你好",
          "type": 0,
          "qrCodeBase64": null
      }
  }
  ```

### 2.2 生成带logo二维码

- 接口地址： https://www.mxnzp.com/api/qrcode/create/logo

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/qrcode/create/logo?content=你好&size=600&logo_size=500&type=0&logo_img=logo图片&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 根据传入的内容生成带logo的二维码，可以选择获取二维码下载链接，也可以直接获取图片的Base64字符串自己解析（注：Base64字符串前面默认添加了“data:image/jpg;base64,”，取值的时候请根据需要对这个内容进行处理）。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "date": "2018-01-01",
              "weekDay": 1,
              "yearTips": "丁酉",
              "type": 2,
              "chineseZodiac": "鸡",
              "solarTerms": "冬至后",
              "avoid": "出行.安葬.修坟.开市",
              "lunarCalendar": "11-15",
              "typeDes" : "元旦",
              "suit": "祭祀.塑绘.开光.裁衣.冠笄.嫁娶.纳采.拆卸.修造.动土.竖柱.上梁.安床.移徙.入宅.安香.结网.捕捉.畋猎.伐木.进人口.放水",
              "dayOfYear": 1,
              "weekOfYear": 1,
              "constellation": "天蝎座",
              "indexWorkDayOfMonth": 1
          },
          ...这个地方只显示了一条
      ]
  }
  ```