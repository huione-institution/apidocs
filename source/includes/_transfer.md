# 转账

## 执行内部转账

`POST /v1/internalTransfer`

**请求参数**

| **参数名** | **是否必填** | **参数类型** | **描述说明** |
| ----------| ----------- | ---------- | ----------- |
| transfers | 是 |            | 请求转账结构体数组 |
| transfersFromAccout | 是 | String | 转出账户 |
| transfersToAccout | 是 | String | 转入账户 |
| transfersThirdId | 是 | String | 外部订单id(重复不处理) |
| transfersSymbol | 是 | String | 代币名称 |
| transfersAmount | 是 | String | 转账金额 |
| transfersCallBack | 否 | String | 转账成功回调地址 |
| transfersExt | 否 | String | 透传参数 |
| isSync | 是 | Boolean | 是否同步执行 |
| isTransaction | 是 | Boolean | 是否整体做为事务 |

```javascript
//示例
{
    "transfers":[
        {
            "from_accout":"10",
            "to_accout":"12",
            "third_id":"1",
            "token":"hui",
            "amount":"1",
            "call_back":"",
            "ext":""
        },
         {
            "from_accout":"10",
            "to_accout":"12",
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

**返回参数**

| **参数名** | **参数类型** | **描述说明** |
| ---------- | ---------- | ----------- |
| code | Integer | 状态码0为处理成功其余为错误 |
| msg | String | 错误信息提示 |
| data | Array | 结果数组 |
| dataOrderId | String | 内部订单id |
| dataThirdId | String | 三方订单id |
| dataSuccess | Boolean | 是否成功 |

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

## 充值提现转账历史记录

`POST /v1/internalTransferHistory`

**请求参数**

| **参数名** | **是否必填** | **参数类型** | **描述说明** |
| ----------| ----------- | ---------- | ----------- |
| params | 是 | Array | 查询数组一次最多支持查询100条 |
| paramsThirdId | 是 | String | 三方订单id |
| paramsOrderId | 是 | String | 内部订单id |

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

**返回参数**

| **名** | **是否必填** | **参数类型** | **描述说明** |
| ----------| ----------- | ---------- | ----------- |
| code | 是 | Integer | 状态码0为正常 |
| msg | 是 | String | 信息 |
| Data | 是 | Array |  |
| DataOrderId | 是 | String | 订单id |
| DataOrderType | 是 | Integer | 订单类型1充值订单2转账订单3提现订单 |
| DataFrom | 是 | String | 链上转出地址 |
| DataTo | 是 | String | 链上转入地址 |
| DataTxHash | 是 | String | 链上交易hash |
| DataStatus | 是 | Integer | 0处理中1处理成功 2处理出错3处理中 |
| DataMessage | 是 | String |  |
| DataThirdId | 是 | String | 三方订单id |
| DataCreateTime | 是 | Integer | 创建时间 |
| DataUpdateTime | 是 | Integer | 更新时间 |
| DataCallBack | 是 | String | 回调url |
| DataExt | 是 | String | 透传参数 |
| DataFromUid | 是 | String | 转出内部id |
| DataToUid | 是 | String | 转入内部id |
| DataAmount | 是 | String | 金额 |
| DataSymbol | 是 | String | 代币名称 |
| DataChain | 是 | String | 链名称 |

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
