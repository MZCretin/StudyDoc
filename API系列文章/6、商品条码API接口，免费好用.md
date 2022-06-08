## 1、前言

商品条码接口，这个是RollToolsApi通用系列接口的其中一个，内部包含了2个小接口，能实现生成指定编码信息的条形码和根据条形码code值获取商品信息。这个接口的主要特点是，能够免费获取商品信息。

查看接口完整信息：https://www.mxnzp.com/doc/detail?id=6

RollToolsApi通用系列接口包含多很多免费通用的API接口，利用这些接口可以帮你实现去开发出很多功能丰富，服务稳定的小程序，APP或者网页，无论是练手还是实战都是不错的选择。所有接口的列表可以在此查看 https://www.mxnzp.com/doc/list

## 2、接口明细

注意：app_id和app_secret是临时秘钥，如果真正使用，需要去https://www.mxnzp.com申请属于自己的专属秘钥。

### 2.1 生成指定条形码

- 接口地址： https://www.mxnzp.com/api/barcode/create

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/barcode/create?content=6902538005141&width=500&height=300&type=0&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 根据内容生成指定的条形码。

- 返回示例：

  ```json
    {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "barCodeUrl": "http://127.0.0.1:8080/api_file/barcode/d/e/7/c/e/d/8/9ed3dda9026d4be2a4e9a71c7e235314.png",
          "content": "1232344122342",
          "type": 0,
          "barCodeBase64": null
      }
  ```

### 2.2 获取条形码对应的商品信息

- 接口地址： https://www.mxnzp.com/api/barcode/goods/details

- 返回格式： JSON

- 请求方式： GET

- 请求示例： https://www.mxnzp.com/api/barcode/goods/details?barcode=6902538005141&app_id=ixssxqertpltndez&app_secret=QUF5S2JLZkNqSHdyeVVLczdCNSt1QT09

- 接口备注： 根据条形码中对应的商品code获取对应的商品信息。

- 返回示例：

  ```json
  {
      "code": 1,
      "msg": "数据返回成功",
      "data": {
          "goodsName": "脉动维生素饮料（水蜜桃口味）600ml",
          "barcode": "6902538005141",
          "price": "3.80",
          "brand": "达能",
          "supplier": "达能(中国)食品饮料有限公司",
          "standard": "600ml"
      }
  }
  ```



