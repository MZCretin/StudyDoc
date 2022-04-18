## 1、前言

简繁转换接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能进行汉字简体与繁体的转换工作，之前开发的翻译系统中就使用了此功能。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=20

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 简体与繁体的转换

- 接口地址： https://www.mxnzp.com/api/convert/zh

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/convert/zh?content=当你老了&type=1&app_id=niwguxhxmtjnqkwr&app_secret=SE9YWERRTEI0amtGT0RPVWlYaVUrZz09

- 接口备注： 简体与繁体的相互转换

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "originContent": "当你老了",
          "convertContent": "當你老了"
      }
  }
  ```

