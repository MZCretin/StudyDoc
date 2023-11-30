## 1、前言

URL生成短链接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，可将长链接生成短链，方便分发和推广。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=26

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 URL生成短链接

- 接口地址： https://www.mxnzp.com/api/shortlink/create

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/shortlink/create?url=aHR0cHM6Ly93d3cubXhuenAuY29tL2FwaS9zaG9ydGxpbmsvY3JlYXRlP3VybD1hSFIwY0hNNkx5OTNkM2N1YlhodWVuQXVZMjl0THc9PSZhcHBfaWQ9amdybXlxamNpYnhoc25xZCZhcHBfc2VjcmV0PWNtdFFSRVEyUmt0aFEyczRiVnBPUjBSNmRHSkRRVDA5&app_id=jgrmyqjcibxhsnqd&app_secret=cmtQREQ2RkthQ2s4bVpOR0R6dGJDQT09

- 接口备注： 长url生成短连接

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "shortUrl": "https://mxnzp.com/sl/bpcL",
          "url": "https://www.mxnzp.com/api/shortlink/create?url=aHR0cHM6Ly93d3cubXhuenAuY29tLw==&app_id=jgrmyqjcibxhsnqd&app_secret=cmtQREQ2RkthQ2s4bVpOR0R6dGJDQT09"
      }
  }
  ```

