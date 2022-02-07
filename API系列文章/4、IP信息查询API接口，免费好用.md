## 1、前言

IP信息查询接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，能实现获取访问者当前ip信息和指定信息ip信息。这个接口的主要特点是，能获取ip地址所在省市信息和运营商信息。

目前系统已经收录了两千多万条ip数据，如需获取库文件可通过个人网站中关于我中我的信息联系我~

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 获取访问者的ip地址信息

- 接口地址： https://www.mxnzp.com/api/ip/self

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/ip/self?app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取访问者的ip地址信息，先获取您的ip地址，再进行解析

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "ip": "119.123.72.166",
          "province": "广东省",
          "provinceId": 440000,
          "city": "深圳市",
          "cityId": 440300,
          "isp": "电信",
          "desc": "广东省深圳市 电信"
      }
  }
  ```

### 2.2 获取指定ip的ip地址信息

- 接口地址： https://www.mxnzp.com/api/ip/aim_ip

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/ip/aim_ip?ip=119.123.72.166&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 获取指定ip的ip地址信息

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "ip": "119.123.72.166",
          "province": "广东省",
          "provinceId": 440000,
          "city": "深圳市",
          "cityId": 440300,
          "isp": "电信",
          "desc": "广东省深圳市 电信"
      }
  }
  
  ```
