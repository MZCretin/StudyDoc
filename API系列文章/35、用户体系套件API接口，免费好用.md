## 1、前言

用户体系套件查询API接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了10个小接口，可以实现用户的注册，登录，获取token，设置用户信息，获取用户信息，存储用户配置等等，可发真实验证码模拟真实注册场景。使用此套接口可以完全实现一套属于自己的用户体系，让应用更真实。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=39

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是**临时秘钥**，如果真正使用，需要去 https://www.mxnzp.com 申请属于自己的专属秘钥。

### 2.1 获取短信验证码

- 接口地址： https://www.mxnzp.com/api/cloud_user/code/get

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cloud_user/code/get?phone=1322729xxxx&type=0&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 获取不同类型短信验证码

- 返回示例：

  ```json
  {
      "code":1,
      "msg":"数据返回成功！",
      "data": null
  }
  ```

### 2.2 **用户手机号注册**

- 接口地址： https://www.mxnzp.com/api/cloud_user/register

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cloud_user/register?phone=1322729xxxx&code=123456&nickname=张三&password=xxx&sex=0&birthday=1707184960286&email=xxx&extra=xxx&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 通过手机号和验证码注册用户，请注意是POST请求

- 返回示例：

  ```json
  {
      "code":1,
      "msg":"数据返回成功！",
      "data": null
  }
  ```

### 2.3 账号密码登录

- 接口地址： https://www.mxnzp.com/api/cloud_user/login/psw

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cloud_user/login/psw?phone=1322729xxxx&password=xxx&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户通过手机号和密码登录（需要先注册）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "userId": "qpujpkjvoudsylho",
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJxcHVqcGtqdm91ZHN5bGhvIiwiZXhwIjoxNzA3NzkyNjgyfQ.J7KbjHMWXO3yxQBD8O8-5RWnkGTXkkM52_jxUmN-KCg",
          "tokenExpire": 1707792682785
      }
  }
  ```

### 2.4 验证码登录

- 接口地址： https://www.mxnzp.com/api/cloud_user/login/code

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cloud_user/login/code?phone=1322729xxxx&code=123456&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户通过手机号和验证码登录（需要先注册）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "userId": "qpujpkjvoudsylho",
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJxcHVqcGtqdm91ZHN5bGhvIiwiZXhwIjoxNzA3NzkyNjgyfQ.J7KbjHMWXO3yxQBD8O8-5RWnkGTXkkM52_jxUmN-KCg",
          "tokenExpire": 1707792682785
      }
  }
  ```

### 2.5 获取用户信息

- 接口地址： https://www.mxnzp.com/api/cloud_user/userinfo/get

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cloud_user/userinfo/get?app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户获取用户信息（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": {
          "userId": "qpujpkjvoudsylho",
          "nickname": "穆仙念",
          "sex": 0,
          "birthday": 0,
          "email": "",
          "extra": "测试配置"
      }
  }
  ```

### 2.6 更新用户信息

- 接口地址： https://www.mxnzp.com/api/cloud_user/userinfo/update

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cloud_user/userinfo/update?nickname=张三&sex=0&birthday=1707184960286&email=xxx&extra=xxx&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户更新用户信息-POST请求（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  null
  }
  ```

### 2.7 设置用户配置信息

- 接口地址： https://www.mxnzp.com/api/cloud_user/config/set

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cloud_user/config/set?key=aaa&config=bbb&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户设置用户配置信息-POST请求（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  null
  }
  ```

### 2.8 获取用户配置信息

- 接口地址： https://www.mxnzp.com/api/cloud_user/config/get

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cloud_user/config/set?key=aaa&config=bbb&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户获取用户配置信息-POST请求（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data": "1234"
  }
  ```

### 2.9 用户重置密码

- 接口地址： https://www.mxnzp.com/api/cloud_user/psw/rest

- 返回格式： JSON

- 请求方式： POST

- 请求示例： https://www.mxnzp.com/api/cloud_user/psw/reset?phone=1322729xxxx&code=123456&password=123456&app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户重置密码-POST请求，重置完需要重新登录（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  null
  }
  ```

### 2.10 用户退出登录

- 接口地址： https://www.mxnzp.com/api/cloud_user/logout

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/cloud_user/logout?app_id=不再提供请自主申请&app_secret=不再提供请自主申请

- 接口备注： 用户退出登录，退出后之前生成的token会过期，需要重新登录（请求头或者请求参数列表中需要放token信息，key是cloud_token，值是token信息）

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功！",
      "data":  null
  }
  ```

