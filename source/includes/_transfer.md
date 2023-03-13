# 6转账

## 61执行内部转账

`POST /v1/internalTransfer`

```javascript
//示例
{
    "transfers":[
        {
            "from_account":"10",
            "to_account":"12",
            "third_id":"1",
            "token":"hui",
            "amount":"1",
            "call_back":"",
            "ext":""
        },
         {
            "from_account":"10",
            "to_account":"12",
            "third_id":"3",
            "token":"hui",
            "amount":"2",
            "call_back":"",
            "ext":""
        }
    ],
    "is_sync":false,
    "is_transaction":true
}
```
**请求参数**

| **参数名**          | **是否必填** | **参数类型** | **描述说明**            |
| ------------------- | ------------ | ------------ | ----------------------- |
| transfers           | true         | String       | 请求转账结构体数组      |
| transfersFromaccount | true         | String       | 转出账户                |
| transfersToaccount   | true         | String       | 转入账户                |
| transfersThirdId    | true         | String       | 外部订单 id(重复不处理) |
| transfersSymbol     | true         | String       | 代币名称                |
| transfersAmount     | true         | String       | 转账金额                |
| transfersCallBack   | false        | String       | 转账成功回调地址        |
| transfersExt        | false        | String       | 透传参数                |
| isSync              | true         | Boolean      | 是否同步执行            |
| isTransaction       | true         | Boolean      | 是否整体做为事务        |


```javascript
{
    "code": 0,
    "msg": "",
    "data": [
        {
            "order_id": "H02167628366229400160",
            "third_id": "1",
            "sucess": true
        },
        {
            "order_id": "H02167628366229500161",
            "third_id": "3",
            "sucess": true
        }
    ]
}
```
**返回参数**

| **参数名**  | **参数类型** | **描述说明**                  |
| ----------- | ------------ | ----------------------------- |
| code        | Integer      | 状态码 0 为处理成功其余为错误 |
| msg         | String       | 错误信息提示                  |
| data        | Array        | 结果数组                      |
| dataOrderId | String       | 内部订单 id                   |
| dataThirdId | String       | 三方订单 id                   |
| dataSuccess | Boolean      | 是否成功                      |



## 62充值提现转账历史记录


`POST /v1/internalTransferHistory`

```javascript
{
    "params": [
        {
            "third_id": "",
            "order_id": "H01167636933905400036"
        },
        {
            "third_id": "0x3b70684aa49092608c339043907e60eba24afafa2f6745e4a84d45343436c868",
            "order_id": ""
        }
    ]
}
```
**请求参数**

| **参数名**    | **是否必填** | **参数类型** | **描述说明**                    |
| ------------- | ------------ | ------------ | ------------------------------- |
| params        | true         | Array        | 查询数组一次最多支持查询 100 条 |
| paramsThirdId | true         | String       | 三方订单 id                     |
| paramsOrderId | true         | String       | 内部订单 id                     |


```javascript
{
	"code": 0,
	"msg": "ok",
	"Data": [
		{
			"order_id": "H01167636933905400036",
			"order_type": 1,
			"from": "0xee3feff2b426c118c7878be4ff16d11ba894e344",
			"to": "0xcca6461cfee45e103ad261427de459657190c616",
			"tx_hash": "0x9bd5181cec46cd36f9c27fde0144c70c477e32c89f3998a17b37c233864e3d37",
			"status": 1,
			"message": "",
			"third_id": "0x9bd5181cec46cd36f9c27fde0144c70c477e32c89f3998a17b37c233864e3d37",
			"create_time": 1676369339055,
			"update_time": 1676369339066,
			"call_back": "",
			"ext": "",
			"from_uid": "",
			"to_uid": "638844470107",
			"amount": "2000000000000000000",
			"symbol": "hui",
			"chain": "HUI"
		},
		{
			"order_id": "H01167636934007600037",
			"order_type": 1,
			"from": "0xee3feff2b426c118c7878be4ff16d11ba894e344",
			"to": "0xcca6461cfee45e103ad261427de459657190c616",
			"tx_hash": "0x3b70684aa49092608c339043907e60eba24afafa2f6745e4a84d45343436c868",
			"status": 1,
			"message": "",
			"third_id": "0x3b70684aa49092608c339043907e60eba24afafa2f6745e4a84d45343436c868",
			"create_time": 1676369340076,
			"update_time": 1676369340084,
			"call_back": "",
			"ext": "",
			"from_uid": "",
			"to_uid": "638844470107",
			"amount": "2",
			"symbol": "hui",
			"chain": "HUI"
		}
	]
}
```

**返回参数**

| **名**         | **是否必填** | **参数类型** | **描述说明**                              |
| -------------- | ------------ | ------------ | ----------------------------------------- |
| code           | true         | Integer      | 状态码 0 为正常                           |
| msg            | true         | String       | 信息                                      |
| Data           | true         | Array        |                                           |
| DataOrderId    | true         | String       | 订单 id                                   |
| DataOrderType  | true         | Integer      | 订单类型 1 充值订单 2 转账订单 3 提现订单 |
| DataFrom       | true         | String       | 链上转出地址                              |
| DataTo         | true         | String       | 链上转入地址                              |
| DataTxHash     | true         | String       | 链上交易 hash                             |
| DataStatus     | true         | Integer      | 0 处理中 1 处理成功 2 处理出错 3 处理中   |
| DataMessage    | true         | String       |                                           |
| DataThirdId    | true         | String       | 三方订单 id                               |
| DataCreateTime | true         | Integer      | 创建时间                                  |
| DataUpdateTime | true         | Integer      | 更新时间                                  |
| DataCallBack   | true         | String       | 回调 url                                  |
| DataExt        | true         | String       | 透传参数                                  |
| DataFromUid    | true         | String       | 转出内部 id                               |
| DataToUid      | true         | String       | 转入内部 id                               |
| DataAmount     | true         | String       | 金额                                      |
| DataSymbol     | true         | String       | 代币名称                                  |
| DataChain      | true         | String       | 链名称                                    |
