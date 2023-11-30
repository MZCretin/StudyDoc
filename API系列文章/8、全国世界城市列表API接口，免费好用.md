## 1、前言

全国/世界城市列表接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了3个小接口，能实现获取全国城市列表，搜索全国城市列表和获取世界级国家城市列表。这个接口的主要特点是，数据比较新。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=6

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 全国城市列表

- 接口地址： https://www.mxnzp.com/api/address/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/address/list?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取全国城市列表信息

- 返回示例：

  ```json
  {
      "code":1,
      "msg":"数据返回成功",
      "data":[
          {
              "code":"130000",
              "name":"河北省",
              "pchilds":[
                  {
                      "code":"130100",
                      "name":"石家庄市",
                      "cchilds":[
                          {
                              "code":"130101",
                              "name":"市辖区"
                          },
                          {
                              "code":"130102",
                              "name":"长安区"
                          },
                          ...这里只显示了两个区...
                      ]
                  },
                  {
                      "code":"130200",
                      "name":"唐山市",
                      "cchilds":[
                          {
                              "code":"130201",
                              "name":"市辖区"
                          },
                          {
                              "code":"130202",
                              "name":"路南区"
                          },
                          ...这里只显示了两个区...
                      ]
                  },
                  ...这里只显示了两个市...
              ]
          }
          ...这里只显示了一个省...
      ]
  }
  ```

### 2.2 搜索全国城市列表

- 接口地址： https://www.mxnzp.com/api/address/search

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/address/search?type=1&value=深圳&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 搜索全国城市列表信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "code": "440000",
              "name": "广东省",
              "pchilds": [
                  {
                      "code": "440300",
                      "name": "深圳市",
                      "cchilds": [
                          {
                              "code": "440301",
                              "name": "市辖区"
                          },
                          {
                              "code": "440303",
                              "name": "罗湖区"
                          },
                          ...这里只显示了两个区...
                      ]
                  }
              ]
          }
      ]
  }
  ```

### 2.3 世界级国家城市列表

- 接口地址： https://www.mxnzp.com/api/address/v2/list

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/address/v2/list?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取世界级国家城市列表（2019年05月15日新增接口）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": [
          {
              "name": "中国",
              "code": "1",
              "clist": [
                  {
                      "code": "110000",
                      "name": "北京市",
                      "pchilds": [
                          {
                              "code": "110100",
                              "name": "市辖区",
                              "cchilds": [
                                  {
                                      "code": "110101",
                                      "name": "东城区"
                                  },
                                  {
                                      "code": "110102",
                                      "name": "西城区"
                                  },
                                  ...这里只显示了两个区...
                              ]
                          }
                      ]
                  }
                	...这里只显示了一个省/市...
               ]
          },
        	{
      				"name": "阿尔巴尼亚",
      				"code": "ALB",
      				"clist": [
          				{
              				"code": "",
              				"name": "市辖区",
              				"pchilds": [
                  				{
                      				"code": "EL",
                      				"name": "爱尔巴桑",
                      				"cchilds": null
                  				},
                  				{
                      				"code": "DI",
                      				"name": "迪勃拉",
                      				"cchilds": null
                  				}
                   				...这里只显示了一个省/市... 
                      ]
                  }
          		]
          }
       ]
  }
  ```

  
