## 1、前言

成语大全查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了3个小接口，可查询成语信息，包含成语的拼音，释义，引用和使用实例信息。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=35

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是**临时秘钥**，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 查询成语信息

- 接口地址： https://www.mxnzp.com/api/idiom/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/idiom/search?key=一心一意&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 根据内容查询成语信息，可使用至少两个字进行模糊查询，也可以使用成语拼音首字母进行模糊查询

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "pinyin": "yī xīn yī yì",
              "word": "一心一意",
              "explanation": "只有一个心眼儿，没有别的考虑。",
              "derivation": "《三国志·魏志·杜恕传》免为庶人，徙章武郡，是岁嘉平元年。”裴松之注引《杜氏新书》故推一心，任一意，直而行之耳。”",
              "example": "所以彭官保便～的料理防守事宜，庄制军便～料理军需器械。★清·张春帆《宦海》第四回"
          }
      ]
  }
  ```

### 2.2 成语接龙查询

- 接口地址： https://www.mxnzp.com/api/idiom/head

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/idiom/head?head_key=父&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 根据成语首个汉字或者首字母进行成语接龙查询

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "pinyin": "fù cí zǐ xiào",
              "word": "父慈子孝",
              "explanation": "父指父母；子子女。父母对子女慈爱，子女对父母孝顺。",
              "derivation": "《礼记·礼运》何谓人义？父慈，子孝，兄良，弟悌，夫义，妇听，长惠，幼顺，君仁，臣忠。”",
              "example": "无"
          },
          {
              "pinyin": "fù mǔ ēn qín",
              "word": "父母恩勤",
              "explanation": "指父母养育子女的恩惠和辛劳。",
              "derivation": "《诗经·豳风·鸱鸮》恩斯勤斯，鬻子之闵斯。”",
              "example": "～，养我身兮。★明·归有光《招张贞女辞》"
          },
          {
              "pinyin": "fù mǔ zhī bāng",
              "word": "父母之邦",
              "explanation": "指祖国。",
              "derivation": "《论语·微子》枉道而事人，何必去父母之邦。”",
              "example": "无"
          }
  	...这里只展示三条
      ]
  }
  ```

### 2.3 随机返回一个成语

- 接口地址： https://www.mxnzp.com/api/idiom/random

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/idiom/random?app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 随机返回一个成语的信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  {
              "pinyin": "fù cí zǐ xiào",
              "word": "父慈子孝",
              "explanation": "父指父母；子子女。父母对子女慈爱，子女对父母孝顺。",
              "derivation": "《礼记·礼运》何谓人义？父慈，子孝，兄良，弟悌，夫义，妇听，长惠，幼顺，君仁，臣忠。”",
              "example": "无"
          }
  }
  ```

  
