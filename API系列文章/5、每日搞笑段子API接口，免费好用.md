## 1、前言

每日搞笑段子接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，能实现获取随机段子信息。这个接口的主要特点是，数据来源于我维护的另一款APP《段子乐》，段子乐中包含纯文本，图片和视频数据，出于成本考虑，目前仅开放纯文本的数据出来，后续等我找到一份更高薪的工作之后再考虑共享图片和视频段子数据。

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 分页获取笑话段子列表

- 接口地址： https://www.mxnzp.com/api/jokes/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/jokes/list?page=1&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 分页获取笑话段子列表，此接口的数据来源是我的另外一个产品【段子乐】，目前Android客户端已经在各大应用市场上架，定期更新数据到此服务。本服务目前只开放纯文本段子，后期看情况开放搞笑短视频和搞笑图片的接口。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "page": 2,
          "totalCount": 9590,
          "totalPage": 959,
          "limit": 10,
          "list": [
              {
                  "content": "儿子:“爸爸，为什么王叔叔那么喜欢吃辣”爸爸:“你怎么知道王叔叔喜欢吃辣？”儿子:“别人都叫我妈妈为辣妈，我经常看到王叔叔抱着我妈妈又亲又啃”爸爸:“尼玛”",
                  "updateTime": "2018-11-03 09:45:28"
              },
              ...这里只显示了一条数据...
          ]
      }
  }
  ```

### 2.2 随机获取笑话段子列表

- 接口地址： https://www.mxnzp.com/api/jokes/list/random

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/jokes/list/random?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 随机获取笑话段子列表，此接口的数据来源是我的另外一个产品【段子乐】，目前Android客户端已经在各大应用市场上架，定期更新数据到此服务。本服务目前只开放纯文本段子，后期看情况开放搞笑短视频和搞笑图片的接口。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "content": "朋友问我，如果在这个时代做个普通人，你最想做什么样的。我说，我想做个皇城根底下的社会闲散人员，好吃懒做，游手好闲，靠着祖上的余荫收点租子过日子。",
              "updateTime": "2018-04-30 13:45:44"
          },
          ...这里只显示了一条数据...
      ]
  }
  
  ```




