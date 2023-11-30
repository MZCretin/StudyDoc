## 1、前言

抖音视频解析下载API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，解析抖音视频，去水印后获取视频下载链接。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=31

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 解析抖音视频链接

- 接口地址： https://www.mxnzp.com/api/douyin/video

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/douyin/video?url=aHR0cHM6Ly92LmRvdXlpbi5jb20vUlBLWXQyYy8=&app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 解析抖音视频链接获取去水印MP4下载链接

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "title": "买大G的小伙#车知识分享计划 #汽车人共创计划 #评车打卡挑战 #用车有妙招 #好车推荐官 #dou来拍车",
          "cover": "https://p26-sign.douyinpic.com/tos-cn-p-0000/31ee3aecff7949229d3dbcf05d53c3bc~c5_300x400.jpeg?x-expires=1637838000&x-signature=58Gf7zgpI539Sv9p8FvYm7uipDs%3D&from=4257465056_large",
          "coverDynamic": "https://p3-sign.douyinpic.com/obj/tos-cn-p-0015/2a9c6ae6152342f3a4f1c0bed771d9be_1636531266?x-expires=1637838000&x-signature=pvRoyLC2a4%2FaiLR6jW9Uv%2B%2BBCA0%3D&from=4257465056_large",
          "url": "https://v99.douyinvod.com/5dd48c1b61876659abc9d04acd2d3bb0/618d0d0d/video/tos/cn/tos-cn-ve-15-alinc2/53f3170a4d4846b0b2ba9238174d19ee/?a=1128&br=752&bt=752&cd=0%7C0%7C0&ch=96&cr=0&cs=0&cv=1&dr=0&ds=6&er=&ft=5f4rKJmmnPEC2Th7ThWwkXAGfdH.CwT19BZc&l=2021111119305601019405713115078689&lr=all&mime_type=video_mp4&net=0&pl=0&qs=0&rc=M3Y3ZTc6ZmlxOTMzNGkzM0ApaTo5Zjc2NDwzNzQ1ZjppNmcpaHV2fWVuZDFwekBrbGJocjRfbDJgLS1kLS9zczIzMi9fYGAuNl4vLzEzYDE6Y29zYlxmK2BtYmJeYA%3D%3D&vl=&vr=",
          "accept": "540p",
          "width": 1080,
          "height": 1920,
          "duration": 13,
          "durationFormat": "00:00:13"
      }
  }
  ```
