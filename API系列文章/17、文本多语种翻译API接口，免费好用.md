## 1、前言

文本多语种翻译接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能进行多种语种之间的翻译工作，此接口的特点是支持多种主流语言之间的互相翻译功能。目前适用于多个工具类app中。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=21

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 文本翻译

- 接口地址： https://www.mxnzp.com/api/convert/translate

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/convert/translate?content=%E7%94%9F%E6%B4%BB%E5%B0%B1%E6%98%AF%E8%BF%99%E6%A0%B7%EF%BC%8C%E5%A4%84%E5%A4%84%E5%85%85%E6%96%A5%E7%9D%80%E6%97%A0%E5%A5%88&from=zh&to=en&app_id=niwguxhxmtjnqkwr&app_secret=SE9YWERRTEI0amtGT0RPVWlYaVUrZz09

- 接口备注： 将一种语种翻译成另外一种语种。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "origin": "生活就是这样，处处充斥着无奈",
          "result": "Life is like this, full of helplessness everywhere",
          "originLanguage": "zh",
          "resultLanguage": "en"
      }
  }
  ```

### 2.2 文本翻译【base64版本】

- 接口地址： https://www.mxnzp.com/api/convert/translate/base64

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/convert/translate/base64?content=55Sf5rS75bCx5piv6L+Z5qC377yM5aSE5aSE5YWF5pal552A5peg5aWI&from=zh&to=en&app_id=niwguxhxmtjnqkwr&app_secret=SE9YWERRTEI0amtGT0RPVWlYaVUrZz09

- 接口备注： 将一种语种翻译成另外一种语种【base64版本，优化版本】。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "origin": "生活就是这样，处处充斥着无奈",
          "result": "Life is like this, full of helplessness everywhere",
          "originLanguage": "zh",
          "resultLanguage": "en"
      }
  }
  ```

  
