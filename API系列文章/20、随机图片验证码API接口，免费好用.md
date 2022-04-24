## 1、前言

随机图片验证码接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，可生成随机图片验证码，并返回图片给你。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=24

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 生成随机图片验证码

- 接口地址： https://www.mxnzp.com/api/verifycode/code

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/verifycode/code?len=5&type=0&app_id=wnnbfresnwjmb0sx&app_secret=dEgzNDFmVGNYVE9YdDNZblJLQlVOZz09

- 接口备注： 生成随机长度的图片验证码。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "verifyCode": "GYJ4R",
          "verifyCodeImgUrl": "http://www.mxnzp.com/api_file/varitycode/8/e/d/1/f/9/2/e/d843f4db9c4c4e94a1a75d5f15e57433.jpg",
          "verifyCodeBase64": null,
          "whRatio": "225,80"
      }
  }
  ```
