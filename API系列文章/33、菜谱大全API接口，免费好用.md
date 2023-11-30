## 1、前言

菜谱大全查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了6个小接口，可使用该接口制作一个菜谱小应用。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=36

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是**临时秘钥**，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 用关键字搜索菜谱信息

- 接口地址： https://www.mxnzp.com/api/cookbook/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cookbook/search?keyword=酸辣土豆丝&page=1&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 搜索菜谱信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 2082,
          "totalPage": 209,
          "limit": 10,
          "list": [
              {
                  "id": 322605,
                  "name": "酸辣汤",
                  "desc": "",
                  "ingredient": [
                      {
                          "name": "鸡蛋"
                      },
                      {
                          "name": "番茄?"
                      },
                      {
                          "name": "金针菇"
                      },
                      {
                          "name": "胡萝卜丝"
                      },
                      {
                          "name": "火腿肠丝"
                      },
                      {
                          "name": "木耳"
                      },
                      {
                          "name": "香菜"
                      },
                      {
                          "name": "豆腐皮"
                      },
                      {
                          "name": "淀粉"
                      },
                      {
                          "name": "白胡椒粉"
                      },
                      {
                          "name": "盐"
                      },
                      {
                          "name": "醋"
                      }
                  ],
                  "cover": "http://power-api.cretinzp.com:8000/cookbook_file/1/f/6/d/7/f/b/c/d25f72b748684af2b328d4e9433c8d38.jpg"
              },
              ...这里只显示一条数据
          ]
      }
  }
  ```

### 2.2 获取食谱分类信息

- 接口地址： https://www.mxnzp.com/api/cookbook/category

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cookbook/category?category_id=3&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 获取菜谱分类信息，大分类分类id传-1，二级和三级分类传父分类id就好了

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "id": 1,
              "name": "热门专题",
              "floor": 1
          },
          {
              "id": 44,
              "name": "烘焙甜品饮料",
              "floor": 1
          },
          {
              "id": 69,
              "name": "肉类",
              "floor": 1
          }
  	...这里只显示三条
      ]
  }
  ```

### 2.3 根据菜谱分类id获取菜谱列表

- 接口地址： https://www.mxnzp.com/api/cookbook/list/category

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cookbook/list/category?category_id=3&page=1&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 根据菜谱分类id获取菜谱列表

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 44620,
          "totalPage": 4462,
          "limit": 10,
          "list": [
              {
                  "id": 100086,
                  "name": "干锅花菜",
                  "desc": "",
                  "ingredient": [
                      {
                          "name": "花菜"
                      },
                      {
                          "name": "干辣椒"
                      },
                      {
                          "name": "五花肉"
                      },
                      {
                          "name": "生抽"
                      },
                      {
                          "name": "盐"
                      },
                      {
                          "name": "鸡精"
                      },
                      {
                          "name": "豆瓣酱"
                      },
                      {
                          "name": "蚝油"
                      },
                      {
                          "name": "蒸鱼豉油"
                      },
                      {
                          "name": "韭菜"
                      },
                      {
                          "name": "孜然粉"
                      }
                  ],
                  "cover": "http://power-api.cretinzp.com:8000/cookbook_file/6/b/8/d/3/3/7/c/26f89936c833479398ec7132db8ce7c0.jpg"
              },
              ...这里只显示一条数据
          ]
      }
  }
  ```

### 2.4 获取菜谱详细信息

- 接口地址： https://www.mxnzp.com/api/cookbook/details

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cookbook/details?id=100086&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 获取菜谱详细信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "id": 100086,
          "name": "干锅花菜",
          "tips": "辣度根据个人口味。怕辣就不要放干辣椒哦",
          "difficulty": "容易做",
          "instruction": [
              {
                  "text": "准备一颗花菜洗净，切掉根部 ",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/8/3/0/0/9/2/2/ed1649e322b840629f243c4065cb41a5.jpg",
                  "step": "第1步"
              },
              {
                  "text": "准备一个小碗。分别倒入一勺豆瓣酱，一勺蚝油，一勺生抽，半勺蒸鱼豉油，再加入一点鸡精。搅匀备用。",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/b/0/a/6/9/f/4/5/6e6f3e6874fe43ed901a3bf34a9a854d.jpg",
                  "step": "第2步"
              },
              {
                  "text": "锅中倒入五花肉，慢慢煸炒炒出油脂出来。",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/7/0/f/5/c/7/b/4/cc811a91a7454ec8b40c4ba89a5346f7.jpg",
                  "step": "第3步"
              },
              {
                  "text": "再倒入干辣椒和蒜末 炒出香味",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/4/a/4/9/3/4/0/6/02e9a7ddb3ad4d83b0e951b0e2df5fea.jpg",
                  "step": "第4步"
              },
              {
                  "text": "最后倒入花菜和刚刚调好的料汁继续翻炒至花菜炒熟。中间如果干了可以少量多次加适量水。",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/d/d/1/a/1/c/e/a/d818bfd4e6ac406986fbdda77dfc2592.jpg",
                  "step": "第5步"
              },
              {
                  "text": "快熟时加入点韭菜或者大蒜叶都可以。然后撒点孜然粉和适量盐 翻炒后就可以出锅啦。",
                  "url": "http://power-api.cretinzp.com:8000/cookbook_file/8/8/7/d/8/f/e/4/0a22d51249af412abdf8442e6e7912fe.jpg",
                  "step": "第6步"
              }
          ],
          "duration": "15分钟左右",
          "commentCount": 0,
          "ingredient": [
              {
                  "name": "花菜",
                  "amount": "半个"
              },
              {
                  "name": "干辣椒",
                  "amount": "4-6个"
              },
              {
                  "name": "五花肉",
                  "amount": "200克"
              },
              {
                  "name": "生抽",
                  "amount": "1勺"
              },
              {
                  "name": "盐",
                  "amount": "适量"
              },
              {
                  "name": "鸡精",
                  "amount": "四分之一勺"
              },
              {
                  "name": "豆瓣酱",
                  "amount": "1勺"
              },
              {
                  "name": "蚝油",
                  "amount": "1勺"
              },
              {
                  "name": "蒸鱼豉油",
                  "amount": "半勺"
              },
              {
                  "name": "韭菜",
                  "amount": "100克"
              },
              {
                  "name": "孜然粉",
                  "amount": "三分之一勺"
              }
          ]
      }
  }
  ```

### 2.5 添加菜谱的评论信息

- 接口地址： https://www.mxnzp.com/api/cookbook/comment/add

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cookbook/comment/add?id=100086&name=大哥大&content=我是评论内容&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 添加菜谱对应的评论信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！"
  }
  ```

### 2.6 获取菜谱对应的评论信息

- 接口地址： https://www.mxnzp.com/api/cookbook/comment/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cookbook/comment/add?id=100086&page=1&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 获取菜谱对应的评论信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 1,
          "totalPage": 1,
          "limit": 10,
          "list": [
              {
                  "id": 4,
                  "name": "大哥大",
                  "content": "我是评论信息",
                  "time": "2023-10-12 23:33:17"
              }
          ]
      }
  }
  ```

