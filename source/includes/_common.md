# 4所有链-所有币

## 41获取所有链

`GET api/v1/config/chain/list`

> 返回示例:

```javascript
{
  "code": 0,
    "message": "",
    "data": [
    {
      "chain": "hui",
      "confirmationNumber": 6
    }
  ]
}
```
**返回参数:**

| **字段**           | **类型** | **描述**   |
| ------------------ | -------- | ---------- |
| confirmationNumber | int      | 区块确认数 |
| chain              | string   | 链名称     |



## 42获取所有币

> 返回示例:


`GET api/v1/config/token/list?chain=`

```javascript
{
  "code": 0,
    "message": "",
    "data": [
    {
      "chain": "hui",
      "symbol": "hui",
      "mappedSymbol": "hui",
      "decimals": 18
    },
    {
      "chain": "hui",
      "symbol": "tsc111",
      "mappedSymbol": "tsc111",
      "decimals": 18
    }
  ]
}
```

**请求参数:**

| **字段** | **类型** | **描述** |
| -------- | -------- | -------- |
| chain    | string   | 链名称   |

**返回参数:**

| **字段**     | **类型** | **描述**            |
| ------------ | -------- | ------------------- |
| chain        | string   | 链名称              |
| decimals     | int      | 精度                |
| mappedSymbol | string   | huione 链内代币符号 |
| symbol       | string   | 代币符号            |



## 43所有币配置

`GET api/v1/config/token/config`

> 返回示例:

```javascript
{
  "code": 0,
    "message": "",
    "data": [
    {
      "chain": "hui",
      "symbol": "TSC111",
      "allowInterTransfer": true,
      "allowWithdraw": true,
      "allowPay": true,
      "minWithdraw": "2",
      "minPay": "4"
    }
  ]
}
```

**返回参数:**

| **字段**           | **类型** | **描述**         |
| ------------------ | -------- | ---------------- |
| chain              | string   | 链名称           |
| symbol             | string   | 代币符号         |
| allowPay           | bool     | 是否允许充值     |
| allowWithdraw      | bool     | 是否允许提现     |
| allowInterTransfer | bool     | 是否允许内部转账 |
| minWithdraw        | float64  | 最低提现额度     |
| minPay             | float64  | 最低充值额度     |



## 44获取提现Gas费

`POST api/v1/config/token/fee`

> 返回示例:

```javascript
{
  "code": 0,
    "message": "",
    "data": "0"
}
```

**请求参数:**

| **字段** | **类型** | **描述** |
| -------- | -------- | -------- |
| amount   | float    | 提现金额 |
| symbol   | string   | 代币名称 |
| chain    | string   | 链名称   |

**返回参数:**

| **字段** | **类型** | **描述** |
| -------- | -------- | -------- |
| data     | float    | Gas费   |


