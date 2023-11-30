## 1、前言

节假日万年历接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了7个小接口，能实现查询指定日期/月份/年份/时间范围的节假日和万年历信息，万年历的信息包含农历信息，宜忌等信息。这个接口的主要特点是，返回某个节日是否是工作日，节日和节假日，其准确度和国务院每年的通知完全匹配。

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 获取指定日期的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday/single/{date}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/single/20181121?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定日期的节假日及万年历信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "date": "2018-11-21",
          "weekDay": 3,
          "yearTips": "戊戌",
          "type": 0,
          "typeDes": "工作日",
          "chineseZodiac": "狗",
          "solarTerms": "立冬后",
          "avoid": "嫁娶.安葬",
          "lunarCalendar": "十月十四",
          "suit": "破屋.坏垣.祭祀.余事勿取",
          "dayOfYear": 325,
          "weekOfYear": 47,
          "constellation": "天蝎座",
          "indexWorkDayOfMonth": 1
      }
  }
  ```

### 2.2 获取指定多个日期的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday/multi/{dates}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/multi/20180101,20181010,20181011?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定多个日期的节假日及万年历信息

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

### 2.3 获取指定月份的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday/list/month/{date}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/list/month/201802?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定月份的节假日及万年历信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "date": "2018-02-01",
              "weekDay": 4,
              "yearTips": "丁酉",
              "type": 0,
              "chineseZodiac": "鸡",
              "typeDes" : "工作日",
              "solarTerms": "大寒后",
              "avoid": "开仓.嫁娶.移徙.入宅",
              "lunarCalendar": "12-16",
              "suit": "祭祀.沐浴.祈福.斋醮.订盟.纳采.裁衣.拆卸.起基.竖柱.上梁.安床.入殓.除服.成服.移柩.启攒.挂匾.求嗣.出行.合帐.造畜椆栖",
              "dayOfYear": 32,
              "weekOfYear": 5,
              "constellation": "天蝎座",
              "indexWorkDayOfMonth": 1
          },
          ...只显示了一部分数据
      ]
  }
  ```

### 2.4 获取指定月份的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday/list/month/{date}/{type}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/list/month/201810/rest?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定月份的节假日及万年历信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "month": 10,
              "year": 2018,
              "days": [
                  {
                      "date": "2018-10-13",
                      "weekDay": 6,
                      "yearTips": "戊戌",
                      "type": 1,
                      "typeDes": "休息日",
                      "chineseZodiac": "狗",
                      "solarTerms": "寒露后",
                      "avoid": "开市.交易.祭祀.入宅.安葬",
                      "lunarCalendar": "九月初五",
                      "suit": "捕捉.畋猎.余事勿取",
                      "dayOfYear": 286,
                      "weekOfYear": 41,
                      "constellation": "天蝎座",
                      "indexWorkDayOfMonth": 1
                  },
                  ...中间隐藏了一部分的数据...
              ]
          }
      ]
  }
  ```

### 2.5 获取指定年份的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday//list/year/{date}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/list/year/2018?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定年份的节假日及万年历信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "month": 1,
              "year": 2018,
              "days": [
                  {
                      "date": "2018-01-01",
                      "weekDay": 1,
                      "yearTips": "丁酉",
                      "type": 2,
                      "chineseZodiac": "鸡",
                      "solarTerms": "冬至后",
                      "typeDes" : "元旦",
                      "avoid": "出行.安葬.修坟.开市",
                      "lunarCalendar": "11-15",
                      "suit": "祭祀.塑绘.开光.裁衣.冠笄.嫁娶.纳采.拆卸.修造.动土.竖柱.上梁.安床.移徙.入宅.安香.结网.捕捉.畋猎.伐木.进人口.放水",
                      "dayOfYear": 1,
                      "weekOfYear": 1,
                      "constellation": "天蝎座",
                      "indexWorkDayOfMonth": 1
                  },
                  ...中间隐藏了"2018-01-02"~"2018-01-30"的数据
              ]
          },
          ...中间隐藏了02月到11月的数据
      ]
  }
  ```

### 2.6 获取指定月份的节假日及万年历信息

- 接口地址： https://www.mxnzp.com/api/holiday/list/year/{date}/{type}

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/list/year/2018/rest?ignoreHoliday=false&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定月份的节假日及万年历信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功，域名已经成功备案，为了更优雅的调用，不久后将废弃8091端口，请尽快使用新域名直接调用，多有不便敬请谅解",
      "data": [
          {
              "month": 1,
              "year": 2018,
              "days": [
                  {
                      "date": "2018-01-06",
                      "weekDay": 6,
                      "yearTips": "丁酉",
                      "type": 1,
                      "typeDes": "休息日",
                      "chineseZodiac": "鸡",
                      "solarTerms": "小寒后",
                      "avoid": "嫁娶.开市.入宅.安床.破土.安葬",
                      "lunarCalendar": "冬月廿",
                      "suit": "祭祀.斋醮.纳财.捕捉.畋猎",
                      "dayOfYear": 6,
                      "weekOfYear": 1,
                      "constellation": "天蝎座",
                      "indexWorkDayOfMonth": 1
                  },
                  ...中间还有一些数据没有显示...
              ]
          },
          ...中间有2月到11月的数据没有展示...
      ]
  }
  ```

### 2.7 获取最近前后七个节日信息

- 接口地址： https://www.mxnzp.com/api/holiday/recent/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/holiday/recent/list?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取最近前后七个节日信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "date": "2019年07月07日",
              "lunarDate": "2019年06月05日",
              "holidayName": "国际合作节",
              "residueDays": -34,
              "lunarHoliday": false
          },
          ...这里只显示了一条
      ]
  }
  ```