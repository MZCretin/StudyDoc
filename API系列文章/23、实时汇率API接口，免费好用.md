## 1、前言

实时汇率API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了3个小接口，支持汇率查询，汇率列表和特定货币汇率查询功能。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=27

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 支持的货币编号列表

- 接口地址： https://www.mxnzp.com/api/exchange_rate/configs

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/exchange_rate/configs?app_id=jgrmyqjcibxhsnqd&app_secret=cmtQREQ2RkthQ2s4bVpOR0R6dGJDQT09

- 接口备注： 获取支持的货币编号列表

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "name": "CNY",
              "desc": "人民币"
          },
          {
              "name": "USD",
              "desc": "美元"
          },
          {
              "name": "CAD",
              "desc": "加元"
          }
  	...这里只展示了三个
      ]
  }
  ```

### 2.2 获取汇率列表信息

- 接口地址： https://www.mxnzp.com/api/exchange_rate/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/exchange_rate/list?app_id=jgrmyqjcibxhsnqd&app_secret=cmtQREQ2RkthQ2s4bVpOR0R6dGJDQT09

- 接口备注： 获取热门汇率列表信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "name": "USD/CNY",
              "nameDesc": "美元/人民币",
              "from": "USD",
              "to": "CNY",
              "price": "6.4608"
          },
          {
              "name": "EUR/CNY",
              "nameDesc": "欧元/人民币",
              "from": "EUR",
              "to": "CNY",
              "price": "7.5552"
          },
          {
              "name": "100JPY/CNY",
              "nameDesc": "100日元/人民币",
              "from": "100JPY",
              "to": "CNY",
              "price": "5.8211"
          }
          ...这里只显示三条数据
      ]
  }
  ```

### 2.3 获取指定货币编号的汇率信息

- 接口地址： https://www.mxnzp.com/api/exchange_rate/aim

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/exchange_rate/aim?from=CNY&to=MXN&app_id=jgrmyqjcibxhsnqd&app_secret=cmtQREQ2RkthQ2s4bVpOR0R6dGJDQT09

- 接口备注： 查看指定货币编号的汇率信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "name": "CNY/MXN",
          "nameDesc": "人民币/墨西哥比索",
          "from": "CNY",
          "to": "MXN",
          "price": "3.1117"
      }
  }
  ```

