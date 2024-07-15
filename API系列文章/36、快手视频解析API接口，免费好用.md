## 1、前言

快手视频解析API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，解析快手链接，获取视频Mp4下载链接，即可下载视频到本地。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=40

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 解析快手视频链接

- 接口地址： https://www.mxnzp.com/api/ks/video

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/ks/video?url=aHR0cHM6Ly92Lmt1YWlzaG91LmNvbS9KN0lEMlA=&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 解析快手视频链接获取去水印MP4下载链接

- 请求参数说明：

  | 名称 | 类型   | 说明                                                         |
  | :--- | ------ | ------------------------------------------------------------ |
  | url  | 字符串 | 快手视频链接再base64，例如：https://v.kuaishou.com/J7ID2P 再进行base64加密 |

- 返回参数说明：

  | 名称           | 类型   | 说明                                       |
  | -------------- | ------ | ------------------------------------------ |
  | title          | 字符串 | 视频标题                                   |
  | cover          | 字符串 | 视频封面                                   |
  | duration       | 长整型 | 视频时长                                   |
  | durationFormat | 字符串 | 视频时长格式化                             |
  | width          | 整型   | 视频宽度                                   |
  | height         | 整型   | 视频高度                                   |
  | quality        | 字符串 | 视频质量                                   |
  | url            | 字符串 | 视频下载链接，这个链接有时效性，请尽快使用 |

- 返回示例：

  ```json
  {
    "code": 1,
    "msg": "数据返回成功！",
    "data": {
      "title": "是奶奶从路边把我抱回家养大成人，今天回老家，在柜子里翻出奶奶留下的遗物，瞬间泪奔，奶奶我想您了 ?#泪奔#奶奶",
      "cover": "https://p2.a.yximgs.com/upic/2024/05/29/17/BMjAyNDA1MjkxNzIyMTdfMzQ4MTExOTk3NF8xMzM1OTAzMjA2NTRfMl8z_B73a22e4283e5e96127c28fae13ec0b09.jpg?tag=1-1720879536-xpcwebdetail-0-l0zeov0ezt-05a5b313a83b2e38&clientCacheKey=3xgcin2kfvtnksm.jpg&di=88a2456&bp=10004",
      "duration": 7400,
      "url": "https://v1.kwaicdn.com/ksc2/sbsQ5hERF52REquisaRrj4uawQ7LYPVuZDT0TCJrZgrOgvCDItY9N4VmgZMaj3kqjqT2tqchNVNwqmcHFpWKHugPMCUf30PqO91bVoQjA5hK94ZwE8K-QQZ8GtE7mzmISQSXZVhivgvdnKj1SlQ4TcfK59gUJdeY49i6TVbVUIzw55fwBAJZ87-9ImGBoREN.mp4?pkey=AAX21m2b9WrdqxivxhNp4YR8DV_OzJemwqooq2-KLrKdv9XgVwsuwvQpFWKuwb5woOpAfhdeh8A6HZjzW7XM6UB4tgTBPHp8OJbn3ejMn8XlkDbWTbKnn8q4jtPpFGY0usc&tag=1-1720879536-unknown-0-k2hcykqujb-442506548feff460&clientCacheKey=3xgcin2kfvtnksm_b.mp4&di=88a2456&bp=10004&tt=b&ss=vp",
      "width": 720,
      "height": 1280,
      "quality": "720p"
    }
  }
  ```

  
