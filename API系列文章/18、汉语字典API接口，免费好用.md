## 1、前言

汉语字典接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了1个小接口，能查询单个汉字的读音和含义，适用于查询类应用。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=22

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 查询单个汉字的读音和含义

- 接口地址： https://www.mxnzp.com/api/convert/dictionary

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/convert/dictionary?content=穆&app_id=gwytpwfqthfkor6i&app_secret=R0FHQm0veXdxaXVORDdVYzErL1hxUT09

- 接口备注： 查询单个汉字的读音和含义

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "word": "穆",
              "traditional": "穆",
              "pinyin": "mù",
              "radicals": "禾",
              "explanation": "穆 
  
   (形声。本义禾名)
  
   同本义 
  
   穆,禾也。--《说文》。段玉裁注盖禾有名穆者也。”
  
   古时宗庙制度,父居左为昭,子居右为穆。参见昭穆” 
  
   辩庙祧之昭穆。--《周礼·小宗伯》。注父曰昭,子曰穆。”
  
   代指右边 
  
   只见贾府人分了昭穆,排班立定。--《红楼梦》
  
   又如昭穆(左边和右边)
  
   姓
  
   穆 
  
   恭敬 
  
   于穆清庙。--《诗·周颂·清庙》
  
   穆穆皇皇。--《诗·大雅·假乐》
  
   我其为王穆卜。--《书·金滕》。传
  
   穆mù
  
   ⒈和畅，美好～如清风。
  
   ⒉和睦不～。
  
   ⒊恭敬，严肃静～。肃～。～ ～皇皇（皇皇美好的样子）。",
              "strokes": 16
          }
      ]
  }
  ```
