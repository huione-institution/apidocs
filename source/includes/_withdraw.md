# 5提现功能

## 51执行提现

`POST api/v1/assets/withdraw`

**请求参数**

| **参数** | **是否必填** | **参数类型** | **描述说明** |
| -------- | ------------ | ------------ | ------------ |
| thirdId  | true         | String       | 三方订单 id  |
| accout   | true         | String       | 提现账户 id  |
| symbol   | true         | String       | token        |
| amount   | true         | String       | 数量         |
| chain    | true         | String       | 链名称       |
| addr     | true         | String       | 提现地址     |
| isSync   | true         | Boolean      | 是否同步执行 |

> 示例请求

```javascript
{
    "thirdId": "11111",
    "accout": "123",
    "symbol": "HUI",
    "amount": "20",
    "chain": "hui",
    "addr": "0xAb41dEdC0B7333fD76A0619A145a4Aa3492cB017",
    "isSync": true
}
```

**返回参数**

| **参数**    | **是否必填** | **参数类型** | **描述说明**       |
| ----------- | ------------ | ------------ | ------------------ |
| code        | true         | Integer      | 0 为 ok 其余为错误 |
| msg         | true         | String       | 错误描述           |
| data        | true         | Object       |                    |
| dataOrderId | true         | String       | 订单 id            |
| dataThirdId | true         | String       | 三方订单 id        |
| dataSucess  | true         | Boolean      | 是否成功           |

> 返回示例

```javascript
{"code":-1000,"msg":"notify withdrawl fail","data":{"orderId":"","thirdId":"11111","sucess":false}}
```
