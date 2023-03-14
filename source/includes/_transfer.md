# 6转账

## 61执行内部转账

`POST /v1/internalTransfer`

```javascript
//示例
{
    "transfers":[
        {
            "fromAccount":"0I7vnKT5NsEm7vx",
            "toAccount":"4GKwHjNnECcatkc",
            "thirdId":"testorder1",
            "token":"trx",
            "amount":"2",
            "callBack":"http://gateway-service/notify",
            "ext":""
        }
    ],
    "isSync":true,
    "isTransaction":false
}
```

**请求参数**

| **参数名**            | **是否必填** | **参数类型** | **描述说明**       |
| --------------------- | ------------ | ------------ | ------------------ |
| transfers             | true         | String       | 请求转账结构体数组 |
| transfers.fromAccount | true         | String       | 转出账号           |
| transfers.toAccount   | true         | String       | 转入账号           |
| transfers.thirdId     | true         | String       | 三方订单id         |
| transfers.token       | true         | String       | 币种               |
| transfers.amount      | true         | String       | 转账数量           |
| transfers.callBack    | false        | String       | 回调地址           |
| transfers.ext         | false        | String       | 透传参数           |
| isSync                | true         | Boolean      | 是否同步执行       |
| isTransaction         | true         | Boolean      | 是否是事务         |

```javascript
{
	"code": 0,
	"msg": "ok",
	"data": [
		{
			"orderId": "",
			"thirdId": "testorder1",
			"message": "代币未开启内部转账",
			"sucess": false
		}
	]
}
```
**返回参数**

| **参数名**    | **参数类型** | **描述说明** |
| ------------- | ------------ | ------------ |
| code          | Integer      | 0表示已处理  |
| msg           | String       | 信息         |
| data          | Array        | 相应数据     |
| data.order_id | String       | 内部订单 id  |
| data.third_id | String       | 三方订单 id  |
| data.sucess   | Boolean      | 处理状态     |



## 62充值提现转账历史记录


`POST /v1/internalTransferHistory`

```javascript
{
  "params": [
    {
      "thirdId": "",
      "orderId": "H01167670851755400026"
    },
    {
      "thirdId": "0x3b70684aa49092608c339043907e60eba24afafa2f6745e4a84d45343436c868",
      "orderId": "H01167636934007600037"
    }
  ]
}
```

**请求参数**

| **参数名**     | **是否必填** | **参数类型** | **描述说明**                  |
| -------------- | ------------ | ------------ | ----------------------------- |
| params         | true         | Array        | 查询数组一次最多支持查询100条 |
| params.thirdId | true         | String       | 三方订单 id                   |
| params.orderId | true         | String       | 内部订单 id                   |

```javascript
{
    "code": 0,
    "msg": "ok",
    "data": [
        {
            "orderId": "H01167670851755400026",
            "orderType": 1,
            "from": "0xee3feff2b426c118c7878be4ff16d11ba894e344",
            "to": "0xcca6461cfee45e103ad261427de459657190c616",
            "txHash": "0x82121c92228a12994a384dd86cce3e541d29569074b",
            "status": 1,
            "message": "",
            "thirdId": "0x82121c92228a12994a384dd86cce3e541d29569074b",
            "createTime": 1676708517555,
            "updateTime": 1676708517564,
            "callBack": "",
            "ext": "",
            "fromUid": "",
            "toUid": "638844470107",
            "amount": "2",
            "symbol": "TDC2",
            "chain": "HUI"
        }
    ]
}
```

**返回参数**                 |

| **名**          | **参数类型** | **描述说明**                     |
| --------------- | ------------ | -------------------------------- |
| code            | Integer      | 0标识已处理                      |
| msg             | String       | 信息                             |
| data            | Array        | 查询数据                         |
| data.orderId    | String       | 订单 id                          |
| data.orderType  | Integer      | 1:充值订单 2:转账订单 3:提现订单 |
| data.from       | String       | 转出链上地址                     |
| data.to         | String       | 转入链上地址                     |
| data.txHash     | String       | 链上交易 hash                    |
| data.status     | Integer      | 0 处理中 1 处理成功 2 处理出错   |
| data.message    | String       | 信息                             |
| data.thirdId    | String       | 三方订单 id                      |
| data.createTime | Integer      | 创建时间                         |
| data.updateTime | Integer      | 更新时间                         |
| data.callBack   | String       | 回调地址                         |
| data.ext        | String       | 透传参数                         |
| data.fromUid    | String       | 转出uid                          |
| data.toUid      | String       | 转入uid                          |
| data.amount     | String       | 数量                             |
| data.symbol     | String       | 币种                             |
| data.chain      | String       | 链名称                           |
