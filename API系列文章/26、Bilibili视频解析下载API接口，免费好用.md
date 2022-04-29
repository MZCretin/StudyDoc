## 1、前言

Bilibili视频解析API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，解析哔哩哔哩链接，获取视频Mp4下载链接，即可下载视频到本地。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=30

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 解析哔哩哔哩视频链接

- 接口地址： https://www.mxnzp.com/api/bilibili/video

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/bilibili/video?url=aHR0cHM6Ly93d3cuYmlsaWJpbGkuY29tL3ZpZGVvL0JWMUdxNHkxMzdrSw==&app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 解析哔哩哔哩视频链接获取MP4下载链接

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "title": "小超梦：你觉得哥的火龙诺手会因为你满血就放过你吗？",
          "desc": "小超梦直播间：https://www.huya.com/257085\n求三连",
          "cover": "http://i1.hdslb.com/bfs/archive/c6e8def2035a8c52969e94afd3acbb289933afb7.jpg",
          "list": [
              {
                  "title": "201",
                  "duration": 333,
                  "durationFormat": "00:05:33",
                  "width": 1920,
                  "height": 1080,
                  "accept": [
                      "高清 1080P"
                  ],
                  "url": "https://upos-sz-mirrorkodo.bilivideo.com/upgcxcode/46/41/439354146/439354146-1-208.mp4?e=ig8euxZM2rNcNbhjnWdVhwdlhzTHhwdVhoNvNC8BqJIzNbfq9rVEuxTEnE8L5F6VnEsSTx0vkX8fqJeYTj_lta53NCM=&uipk=5&nbs=1&deadline=1636644051&gen=playurlv2&os=kodobv&oi=837344524&trid=05332e5cdbe9487f8e2ba071110dbc07T&platform=html5&upsig=de7a47b59909e092b1d56e80b7f3017b&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,platform&mid=0&bvc=vod&nettype=0&bw=369013&orderid=0,1&logo=80000000"
              }
          ]
      }
  }
  ```
