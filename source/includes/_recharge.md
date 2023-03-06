# 3充值功能

## 31获取充值地址

`GET api/v1/account/depositAddress`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**            |
| --------- | ------------ | -------- | ------------------- |
| accountId | true         | string   | 账户 id，具有唯一性 |
| network   | true         | string   | 转账网络            |

**返回参数**

| **参数**     | **类型** | **说明** |
| ------------ | -------- | -------- |
| chainAddress | string   | 地址     |

> 返回示例

```javascript
{
	"code": 0,
    "data": "0xF976F480a1c4b6F082f6867870B906A1CbB10D16"
}

```

>

```javascript
{
    "code": 6,
    "message": "该账户未注册或不属于您的机构"
}

```

## 32充值回调 

`POST api/v1/setting/callback`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**            |
| --------- | ------------ | -------- | ------------------- |
| callbackUrl | true         | string   | 回调地址，最好是https地址 |
| publicKey   | true         | string   | 使用Rsa加密            |

**返回参数**

| **参数**     | **类型** | **说明**                                   |
| ------------ | -------- |------------------------------------------|
| Ok | string   | 无意义，请参考code，成功为0，无视data字段，失败请参考message内容 |

> 返回示例

```javascript
{
  "code": 0,
    "data": "Ok"
}

```

>

```javascript
{
  "code": 1,
    "message": "输入参数有误"
}

```
