## 1、前言

美女图片福利查询接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能获取一些青春靓女的图片，拿来做一些demo非常合适。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=15

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 随机获取福利图片

- 接口地址： https://www.mxnzp.com/api/image/girl/list/random

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/image/girl/list/random?app_id=gpugljnjsnipsihq&app_secret=OGV3dDcxVVRRS2ZTR0orakVIcDNoZz09

- 接口备注： 随机获取福利图片。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "imageUrl": "https://tvax3.sinaimg.cn/large/005BYqpggy1g28fwh5g7oj31hc0u0u0x.jpg",
              "imageSize": "1920x1080",
              "imageFileLength": 376155
          },
          ...这里只显示一条数据...
      ]
  }
  
  
  ```

### 2.2 获取福利图片列表

- 接口地址： https://www.mxnzp.com/api/image/girl/list/random

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/image/girl/list/random?app_id=gpugljnjsnipsihq&app_secret=OGV3dDcxVVRRS2ZTR0orakVIcDNoZz09

- 接口备注： 随机获取福利图片。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "imageUrl": "https://tvax3.sinaimg.cn/large/005BYqpggy1g28fwh5g7oj31hc0u0u0x.jpg",
              "imageSize": "1920x1080",
              "imageFileLength": 376155
          },
          ...这里只显示一条数据...
      ]
  }
  ```

## 3、demo

为此我还专门写了个demo，为了看下靓女，舒缓一下心情。

![681649902651_.pic_hd](/images/681649902651_.pic_hd.jpg)
