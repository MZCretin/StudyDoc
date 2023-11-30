## 1、前言

全国天气查询接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，能实现获取特定城市今日及未来三天的天气。这个接口的主要特点是，数据更新延迟低。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=6

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 获取特定城市今日天气

- 接口地址： https://www.mxnzp.com/api/weather/current/{城市名}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/weather/current/深圳市?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取特定城市今日天气信息

- 返回示例：

  ```json
   {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "address": "广东省 深圳市",
          "cityCode": "440300",
          "temp": "18℃",
          "weather": "小雨",
          "windDirection": "东北",
          "windPower": "≤3级",
          "humidity": "92%",
          "reportTime": "2018-11-27 22:40:53"
      }
  }
  ```

### 2.2 获取特定城市今天及未来天气

- 接口地址： https://www.mxnzp.com/api/weather/forecast/{城市名}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/weather/forecast/深圳市?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取特定城市今天及未来天气信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "address": "广东省 深圳市",
          "cityCode": "440300",
          "reportTime": "2018-11-27 22:40:53",
          "forecasts": [
              {
                  "date": "2018-11-27",
                  "dayOfWeek": "2",
                  "dayWeather": "阵雨",
                  "nightWeather": "小雨",
                  "dayTemp": "22℃",
                  "nightTemp": "17℃",
                  "dayWindDirection": "无风向",
                  "nightWindDirection": "无风向",
                  "dayWindPower": "≤3级",
                  "nightWindPower": "≤3级"
              },
              ...这里只显示了一条数据...
          ]
      }
  }
  ```
