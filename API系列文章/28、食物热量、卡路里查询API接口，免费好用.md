## 1、前言

食物热量、卡路里查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了4个小接口，查询食物热量，卡路里和其他很多元素含量查询。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=32

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 获取食物的分类列表

- 接口地址： https://www.mxnzp.com/api/food_heat/type/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/food_heat/type/list?app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 获取食物的分类列表

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": [
          {
              "id": 1,
              "name": "主食类",
              "icon": "http://static-res.cretinzp.com/static-img/icons/1_v1.png?md5=Mp5v5iIL8mx2IhFck24aAA&expires=1638887628"
          },
          {
              "id": 2,
              "name": "肉蛋类",
              "icon": "http://static-res.cretinzp.com/static-img/icons/2_v1.png?md5=t6Zkxi0rSkiw6zJRZW1KtQ&expires=1638887628"
          },
          {
              "id": 3,
              "name": "大豆及制品",
              "icon": "http://static-res.cretinzp.com/static-img/icons/3_v1.png?md5=Dkse7BnQSviVXyrbiasvPg&expires=1638887628"
          },
          这里只显示了3条。。。
      ]
  }
                 
  ```

### 2.2 获取分类下的食物列表

- 接口地址： https://www.mxnzp.com/api/food_heat/food/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/food_heat/food/list?id=1&page=1&app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 根据分类id获取分类下的食物列表

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 5307,
          "totalPage": 531,
          "limit": 10,
          "list": [
              {
                  "foodId": "befa2163948534a9",
                  "name": "鲜玉米",
                  "healthLevel": 1,
                  "calory": "112.0"
              },
              {
                  "foodId": "de8d83813b3c389e",
                  "name": "燕麦片",
                  "healthLevel": 1,
                  "calory": "338.0"
              },
              {
                  "foodId": "dc50e88e9fa67955",
                  "name": "煮面条",
                  "healthLevel": 1,
                  "calory": "107.0"
              },
              这里只显示4条。。。
          ]
      }
  }
  ```

### 2.3 搜索食物

- 接口地址： https://www.mxnzp.com/api/food_heat/food/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/food_heat/food/search?keyword=苹果&page=1&app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 根据关键字搜索食物

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "page": 1,
          "totalCount": 186,
          "totalPage": 19,
          "limit": 10,
          "list": [
              {
                  "foodId": "5a4aa4442b9f5d97",
                  "name": "苹果",
                  "healthLevel": 1,
                  "calory": "53.0"
              },
              {
                  "foodId": "da7e701ff97310ce",
                  "name": "苹果梨",
                  "healthLevel": 1,
                  "calory": "53.0"
              },
              {
                  "foodId": "b2d252e6742cf803",
                  "name": "伏苹果",
                  "healthLevel": 1,
                  "calory": "48.0"
              },
              这里只显示3条。。。
          ]
      }
  }
  ```

  

### 2.4 获取食物详情

- 接口地址： https://www.mxnzp.com/api/food_heat/food/details

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/food_heat/food/details?foodId=befa2163948534a9&page=1&app_id=hfpghjeevqzgfafl&app_secret=Q1FHdGUvMENRcEcvbWFoMjBrU2pwQT09

- 接口备注： 根据foodId获取食物详情

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "foodId": "befa2163948534a9",
          "name": "鲜玉米",
          "calory": "112.0",
          "caloryUnit": "千卡",
          "joule": "468.61",
          "jouleUnit": "千焦",
          "protein": "4.0",
          "proteinUnit": "克",
          "fat": "1.2",
          "fatUnit": "克",
          "saturatedFat": "0.0",
          "saturatedFatUnit": "克",
          "fattyAcid": "",
          "fattyAcidUnit": "克",
          "mufa": "0.0",
          "mufaUnit": "克",
          "pufa": "0.0",
          "pufaUnit": "克",
          "cholesterol": "0.0",
          "cholesterolUnit": "毫克",
          "carbohydrate": "22.8",
          "carbohydrateUnit": "克",
          "sugar": "",
          "sugarUnit": "克",
          "fiberDietary": "2.9",
          "fiberDietaryUnit": "克",
          "natrium": "1.1",
          "natriumUnit": "毫克",
          "alcohol": "0.0",
          "alcoholUnit": "%vol",
          "vitaminA": "0.0",
          "vitaminAUnit": "微克RAE",
          "carotene": "0.0",
          "caroteneUnit": "微克",
          "vitaminD": "0.0",
          "vitaminDUnit": "微克",
          "vitaminE": "0.0",
          "vitaminEUnit": "微克",
          "vitaminK": "0.0",
          "vitaminKUnit": "微克",
          "thiamine": "0.16",
          "thiamineUnit": "毫克",
          "lactoflavin": "0.11",
          "lactoflavinUnit": "毫克",
          "vitaminB6": "0.0",
          "vitaminB6Unit": "毫克",
          "vitaminB12": "0.0",
          "vitaminB12Unit": "微克",
          "vitaminC": "16.0",
          "vitaminCUnit": "毫克",
          "niacin": "1.8",
          "niacinUnit": "毫克",
          "folacin": "31.9",
          "folacinUnit": "微克",
          "pantothenic": "0.0",
          "pantothenicUnit": "毫克",
          "biotin": "0.0",
          "biotinUnit": "微克",
          "choline": "0.0",
          "cholineUnit": "毫克",
          "phosphor": "117.0",
          "phosphorUnit": "毫克",
          "kalium": "238.0",
          "kaliumUnit": "毫克",
          "magnesium": "32.0",
          "magnesiumUnit": "毫克",
          "calcium": "0.0",
          "calciumUnit": "毫克",
          "iron": "1.1",
          "ironUnit": "毫克",
          "zinc": "0.9",
          "zincUnit": "毫克",
          "iodine": "1.1",
          "iodineUnit": "微克",
          "selenium": "1.63",
          "seleniumUnit": "微克",
          "copper": "0.09",
          "copperUnit": "毫克",
          "fluorine": "",
          "fluorineUnit": "毫克",
          "manganese": "0.22",
          "manganeseUnit": "毫克",
          "healthLight": 1,
          "healthTips": "绿灯食物",
          "healthSuggest": "推荐食用",
          "glycemicInfoData": {
              "gi": {
                  "value": "55.0",
                  "label": "中GI"
              },
              "gl": {
                  "value": "10.9",
                  "label": "中GL"
              }
          }
      }
  }
  ```

  
