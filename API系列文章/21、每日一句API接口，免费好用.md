## 1、前言

每日一句接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，可获取每日推荐精美语句，适合哲学情感类应用。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=25

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 每日推荐精美语句

- 接口地址： https://www.mxnzp.com/api/daily_word/recommend

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/daily_word/recommend?count=10&app_id=wnnbfresnwjmb0sx&app_secret=dEgzNDFmVGNYVE9YdDNZblJLQlVOZz09

- 接口备注： 每日推荐精美语句。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "content": "承君此诺，必守一生。",
              "author": "锦重"
          },
        	...这里只显示了一条...
      ]
  }
  ```
