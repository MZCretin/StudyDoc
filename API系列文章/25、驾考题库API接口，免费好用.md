## 1、前言

驾考题库API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，公安部最新驾照考试题库，分小车、客车、货车、摩托车4类，科目一和科目四2种。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=28

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 获取驾考题目列表

- 接口地址： https://www.mxnzp.com/api/driver_exam/question/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/driver_exam/question/list?page=1&rank=1&type=1&app_id=pyraqokgn2oftnaf&app_secret=N01MV3l6NDFpcmkvSXRrN2JMamtVZz09

- 接口备注： 获取驾考题库中指定交通工具的科一/科四考题

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 3592,
          "totalPage": 360,
          "limit": 10,
          "list": [
              {
                  "type": 1,
                  "id": 30413,
                  "rank": 1,
                  "title": "当驾驶车辆行经两侧有行人且有积水的路面时，按照防御性驾驶技术要求，要引人注意，鸣喇叭示意行人有车辆通过注意避让，要留有余地，预测行人可能做的行动，___。",
                  "op1": "A、加速通过",
                  "op2": "B、正常行驶",
                  "op3": "C、减速慢行",
                  "op4": "D、连续鸣喇叭",
                  "titleType": 1,
                  "titlePic": ""
              },
              {
                  "type": 1,
                  "id": 30408,
                  "rank": 1,
                  "title": "如图这种情况下，遇到路口对面有车辆直行，怎么做是正确的？",
                  "op1": "A、如果已经越过停止线就可以加速向左转弯",
                  "op2": "B、不用考虑对面车辆直接向左转弯",
                  "op3": "C、只要不影响对面车辆直行就可以向左转弯",
                  "op4": "D、等待对面车辆直行通过后再向左转弯",
                  "titleType": 1,
                  "titlePic": "https://sucimg.itc.cn/sblog/jd5YYHxo1HE"
              },
              {
                  "type": 1,
                  "id": 30402,
                  "rank": 1,
                  "title": "以下哪个步骤目前无法通过“快处易赔”完成？",
                  "op1": "A、协商定责",
                  "op2": "B、保险报案",
                  "op3": "C、线上定损",
                  "op4": "D、拍照挪车",
                  "titleType": 1,
                  "titlePic": ""
              },
          	... 这里只显示了三条
          ]
      }
  }
  ```

### 2.1 获取驾考题目的答案和解析

- 接口地址： https://www.mxnzp.com/api/driver_exam/answer/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/driver_exam/answer/list?ids=9759,9758,9757&app_id=pyraqokgn2oftnaf&app_secret=N01MV3l6NDFpcmkvSXRrN2JMamtVZz09

- 接口备注： 获取驾考题库指定考题的答案和解析

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "id": 9759,
              "explain": "转向灯操作：上右下左。",
              "answer": "B"
          },
          {
              "id": 9758,
              "explain": "此处为雾灯的控制。顺便回忆一下，哪个控制前雾灯，哪个控制后雾灯。下边的控制前雾灯，上边的控制后雾灯。",
              "answer": "false"
          },
          {
              "id": 9757,
              "explain": "此为控制左右转向灯。顺便回忆一下转向灯操作：上右下左。",
              "answer": "true"
          }
      ]
  }
  ```

  
