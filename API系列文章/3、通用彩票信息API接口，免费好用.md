## 1、前言

通用彩票信息接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了5个小接口，能实现获取指定7大彩种的中奖信息。这个接口的主要特点是，能够实时同步开奖信息，还提供中奖结果计算的接口。

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 指定期号通用中奖号码

- 接口地址： https://www.mxnzp.com/api/lottery/common/aim_lottery

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/lottery/common/aim_lottery?expect=18135&code=ssq&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定期号的通用获奖号码信息

- 返回示例：

  ```json
  {
      "openCode": "01,03,06,10,11,29+16",
      "code": "ssq",
      "expect": "18135",
      "name": "双色球",
      "time": "2018-11-18 21:18:20"
  }
  ```

### 2.2 最新通用中奖号码信息

- 接口地址： https://www.mxnzp.com/api/lottery/common/latest

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/lottery/common/latest?code=ssq&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取最新通用中奖号码信息

- 返回示例：

  ```json
  {
      "openCode": "10,12,15,25,26,27+14",
      "code": "ssq",
      "expect": "18136",
      "name": "双色球",
      "time": "2018-11-20 21:18:20"
  }
  ```

### 2.3 最近历史开奖数据

- 接口地址： https://www.mxnzp.com/api/lottery/common/history

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/lottery/common/history?code=ssq&size=10&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取最近历史开奖数据

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "openCode": "01,04,12,13,30,32+08",
              "code": "ssq",
              "expect": "19100",
              "name": "双色球",
              "time": "2019-08-27 21:18:20"
          },
          ...这里只展示了一条...
      ]
  }
  ```

### 2.4 获取彩种信息

- 接口地址： https://www.mxnzp.com/api/lottery/common/types

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/lottery/common/types?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取系统支持的彩种类型详细信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "typeName": "双色球",
              "typeCode": "ssq",
              "openTime": "每周二、四、日开奖",
              "startTime": "2003年2月16日",
              "ruleDesc": "一等奖（6+1）：浮动。二等奖（6+0）：浮动。三等奖（5+1）：单注奖金固定为3000元。四等奖（5+0、4+1）：单注奖金固定为200元。五等奖（4+0、3+1）：单注奖金固定为10元。六等奖（2+1、1+1、0+1）：单注奖金固定为5元。"
          },
          ...这里只显示了一条...
      ]
  }
  
  ```

### 2.5 中奖结果计算

- 接口地址： https://www.mxnzp.com/api/lottery/common/check

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/lottery/common/check?code=cjdlt&expect=19090&lotteryNo=13,19,28,30,33@02,12&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取彩票的中奖结果，根据投注的彩票号码及期数判断是否中奖，暂只支持双色球、大乐透、七乐彩和七星彩；结果根据一定算法进行计算，如有偏差，请以官方为准！

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "resultList": [
              {
                  "num": "13",
                  "lottery": true,
                  "blue": false
              },
              ...这里只展示一条...
          ],
          "resultDetails": "一等奖，奖金跟随奖池浮动",
          "resultDesc": "5+2",
          "openCode": "13,19,28,30,33+02+12",
          "checkedCode": "13,19,28,30,33@02,12",
          "expect": "19090",
          "code": "cjdlt",
          "codeValue": "超级大乐透"
      }
  }
  ```

