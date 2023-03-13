# 8代币管理 token

## 81查询已发代币列表

查询某个账户 ID 下所发代币的代币列表

> 返回的数据示例如下

`GET api/v1/coin-manage/tokenList`


```javascript
{
    "code": 0,
    "message": "success",
    "data":[{
        "BaseInfo": {
            "Id": "407",
            "Addr": "0x14b9f3762a6a99e02bf3032b6b4f494f4ba54e60",  //地址
            "Name": "3月1日基础代币01",  //名称
            "Symbol": "thira",
            "Decimals": "7",
            "Totoal_Supply": "1000010000000",
            "Create_Time": "2023-03-01 02:42:12"
        },
        "HolderCount": 1,
        "Status": 1
    }]
  }
```

**请求参数：**

| **参数**  | **是否必须** | **类型** | **说明** |
| --------- | ------------ | -------- | -------- |
| accountId | true         | string   | 账户 ID  |

**返回参数：**

| **参数** | **是否必须** | **类型** | **说明**                                                  |
| -------- | ------------ | -------- | --------------------------------------------------------- |
| code     | true         | string   | 0 为正确                                                  |
| message  | true         | string   | 成功或错误信息                                            |
| data     | true         | string   | json 字符串，可转化为代币数组，数组中每个元素是代币结构体 |

代币结构体如下定义

| BaseInfo    | struct | 代币基础详情                                      |
| ----------- | ------ | ------------------------------------------------- |
| HolderCount | int    | 代币持有者数量                                    |
| Status      | int    | 代币状态，是否被禁止交易（0-暂停交易 1-正常交易） |

代币基础详情结构体如下定义

| **参数**      | **类型** | **说明**     |
| ------------- | -------- | ------------ |
| Addr          | string   | 代币地址     |
| Name          | string   | 代币名称     |
| Symbol        | string   | 代币符号     |
| Decimals      | string   | 代币精度     |
| Totoal_Supply | string   | 代币总供应量 |



## 82查询代币详情

查询某个代币的代币详情

`GET api/v1/coin-manage/tokenDetail`

> 返回示例如下：

```javascript
{
    "code": 0,
    "message": "success",
    "data"{
        "Id": "413",
        "Addr": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
        "Name": "3月1日通缩代币07",
        "Symbol": "thirdf",
        "Decimals": "11",
        "Totoal_Supply": "10000700000000000",
        "Create_Time": "2023-03-01 02:59:47"
  }
}
```
**请求参数:**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                |
| -------- | ------------ | -------- | --------------------------------------- |
| code     | true         | string   | 0 为正确                                |
| message  | true         | string   | 成功或错误信息                          |
| data     | true         | string   | json 字符串，可转化为代币基础详情结构体 |

代币基础详情结构体同上


## 83查询代币的持有者信息

`GET api/v1/coin-manage/holderInfos`
```javascript
[
  {
    Id: "1063",
    Addr: "0x8e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    ContractAddr: "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    Balance: "10000700000000000",
    Height: "3534742",
    Balance_Origin: "",
  },
];
```
**请求参数:**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                            |
| -------- | ------------ | -------- | ----------------------------------- |
| code     | true         | string   | 0 为正确                            |
| message  | true         | string   | 成功或错误信息                      |
| data     | true         | string   | json 字符串，可以转换为持有者结构体 |



持有者结构体如下定义

| **参数**     | **类型** | **说明**                   |
| ------------ | -------- | -------------------------- |
| AccountAddr  | string   | 持币地址                   |
| ContractAddr | string   | 代币地址                   |
| Balance      | string   | 代币余额                   |
| Height       | string   | 更新代币余额所在的区块高度 |

## 84查询代币余额

`GET api/v1/coin-manage/tokenBalance`


```javascript
{
    "code": 0,
    "message": "success",
    "data": "10000700000000000"
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| accountId    | true         | string   | 账户 ID  |
| contractAddr | true         | string   | 代币地址 |

**返回参数:**

| **参数** | **类型** | **说明**               |
| -------- | -------- | ---------------------- |
| code     | string   | 0 为正确               |
| message  | string   | 成功或错误信息         |
| data     | string   | 代币余额（带精度截断） |



## 85查询账户下代币的状态

`POST api/v1/coin-manage/tokenStatus`
```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "accountId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数:**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |
| accountId    | true         | string   | 账户 ID  |

```javascript
{
    "IsBlack": false,
    "IsBlackIn": false,
    "IsBlackOut": false,
    "NowFrozenAmount": 0,
    "WaitFrozenAmount": 0
}
```

**返回参数:**

| **参数** | **类型** | **说明**                        |
| -------- | -------- | ------------------------------- |
| code     | string   | 0 为正确                        |
| message  | string   | 成功或错误信息                  |
| data     | string   | json 字符串，可转化为状态结构体 |



状态结构体如下定义

| **参数**         | **类型** | **说明**     |
| ---------------- | -------- | ------------ |
| IsBlack          | bool     | 是否是黑名单 |
| IsBlackIn        | bool     | 是否禁止转入 |
| IsBlackOut       | bool     | 是否禁止转出 |
| NowFrozenAmount  | Int      | 当前冻结数量 |
| WaitFrozenAmount | Int      | 等待冻结数量 |

## 86代币的模型查询

`POST api/v1/coin-manage/tokenModel`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

```javascript
{
    "code": 0,
    "message": "success",
    "data": "7"
}
```
**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**       |
| -------- | ------------ | -------- | -------------- |
| code     | true         | string   | 0 为正确       |
| message  | true         | string   | 成功或错误信息 |
| data     | true         | string   | 模型枚举值     |



模型枚举值定义如下：

| **参数**    | **类型** | **值** | **说明**         |
| ----------- | -------- | ------ | ---------------- |
| _SIMPLE_    | Int      | 1      | 简单模型         |
| _SNAPSHOT_  | Int      | 2      | 快照模型         |
| _VOTES_     | Int      | 3      | 投票模型         |
| _FLASHMINT_ | Int      | 4      | 闪电贷模型       |
| _BURNABLE_  | Int      | 5      | 可燃烧模型       |
| _CAPPED_    | Int      | 6      | 设置总量上限模型 |
| _DEFLATION_ | Int      | 7      | 通缩模型         |

## 87查询代币的交易费比例

`POST api/v1/coin-manage/taxFee`


```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```

**请求参数:**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |


```javascript
{
    "code": 0,
    "message": "success",
    "data": "35500"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                       |
| -------- | ------------ | -------- | ------------------------------ |
| code     | true         | string   | 0 为正确                       |
| message  | true         | string   | 成功或错误信息                 |
| data     | true         | string   | 返回值除以一万，就是交易费比例 |



## 88查询代币的奖励分红比例

`POST api/v1/coin-manage/bonusFee`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |


```javascript
{
    "code": 0,
    "message": "success",
    "data": "0"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                         |
| -------- | ------------ | -------- | -------------------------------- |
| code     | true         | string   | 0 为正确                         |
| message  | true         | string   | 成功或错误信息                   |
| data     | true         | string   | 返回值除以一万，就是奖励分红比例 |


## 89账户的代币交易记录查询

`GET api/v1/coin-manage/txHistory`

```javascript
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "Hash": "0x0e2c1ce50d07a61616fa63154b9aa4c17b73b4c75392c2d294ae2ee33faf17bc",
            "OpParams": {
                "op": "UnFrozen",
                "addr1": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
                "addr2": "",
                "value1": "20000700000000000",
                "value2": "10100699999998002",
                "value3": ""
            },
            "Amount": 0,
            "TxGeneral": {
                "Id": "5805",
                "TxType": "0",
                "From": "0x8e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
                "To": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
                "Hash": "0x0e2c1ce50d07a61616fa63154b9aa4c17b73b4c75392c2d294ae2ee33faf17bc",
                "Index": "0",
                "Value": "0",
                "Input": "0xe5df3dd00000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d000000000000000000000000000000000000000000000000000470e87dac25800",
                "Nonce": "32",
                "GasPrice": "7430083743",
                "GasLimit": "8000000",
                "GasUsed": "59267",
                "IsContract": "1",
                "IsContractCreate": "0",
                "BlockTime": "1677654630",
                "BlockNum": "3542264",
                "BlockHash": "0x63114bc8b390ddca5f9f1537717c2931217c7c37291ccad11dbb44f00f0dd96c",
                "ExecStatus": "1",
                "CreateTime": "2023-03-01 07:10:43",
                "BlockState": "0",
                "MaxFeePerGas": "0",
                "BaseFee": "0",
                "MaxPriorityFeePerGas": "0",
                "BurntFees": "0"
            }
        }
    ]
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**                      |
| ------------ | ------------ | -------- | ----------------------------- |
| accountId    | true         | string   | 账户 ID                       |
| contractAddr | true         | string   | 代币地址                      |
| beginTime    | true         | string   | 开始时间(unix 时间戳，单位秒) |
| endTime      | true         | string   | 结束时间(unix 时间戳，单位秒) |

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                          |
| -------- | ------------ | -------- | --------------------------------- |
| code     | true         | string   | 0 为正确                          |
| message  | true         | string   | 成功或错误信息                    |
| data     | true         | string   | json 字符串，可以转化为交易结构体 |


交易结构体定义如下

| **参数**  | **类型** | **说明**                                                                                                                       |
| --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Hash      | string   | 交易 hash                                                                                                                      |
| OpParams  | struct   | 交易参数结构体                                                                                                                 |
| Amount    | uint64   | 交易数量（如果非合约交易，amount=txGeneral 中的 value，如果是合约交易，那么 txGeneral 中 value 为 0，amount 为代币的交易数量） |
| TxGeneral | struct   | 交易详情结构体                                                                                                                 |

交易参数结构体定义：

| **参数** | **类型** | **说明**           |
| -------- | -------- | ------------------ |
| Op       | string   | 交易动作           |
| Addrs    | []string | 交易参数：地址数组 |
| Values   | []string | 交易参数：值数组   |

交易详情结构体定义：

| **参数**             | **类型**  | **说明**                                                             |
| -------------------- | --------- | -------------------------------------------------------------------- |
| TxType               | string    | 交易类型（0--LegacyTxType 1-- AccessListTxType 2--DynamicFeeTxType） |
| From                 | string    | 交易发送地址                                                         |
| To                   | string    | 交易接收地址                                                         |
| Hash                 | string    | 交易 hash                                                            |
| Index                | string    | 交易在收据中的索引                                                   |
| Value                | string    | 交易的值                                                             |
| Input                | string    | input 数据，如果是非合约交易，此项为空                               |
| Nonce                | string    | 交易的 nonce                                                         |
| GasPrice             | string    | 交易的 gasPrice                                                      |
| GasLimit             | string    | 交易的 gas                                                           |
| GasUsed              | string    | 交易使用的 gas                                                       |
| IsContract           | string    | 是否是合约交易                                                       |
| IsContractCreate     | string    | 是否是合约创建交易                                                   |
| BlockTime            | int       | 交易打包时间                                                         |
| BlockNum             | int       | 交易所在的区块高度                                                   |
| BlockHash            | string    | 交易所在的区块 hash                                                  |
| ExecStatus           | int       | 执行结果（0-失败 1-成功）                                            |
| CreateTime           | timestamp | 交易爬取的时间                                                       |
| BlockState           | int       | 区块状态（0-正常 1-失败 常用于回滚）                                 |
| MaxFeePerGas         | int       | 最高交易消费                                                         |
| BaseFee              | int       | base fee                                                             |
| MaxPriorityFeePerGas | int       | 最高有限消费                                                         |
| BurntFees            | int       | 燃烧的小费                                                           |

## 810查询账户的代币销毁数量

`GET api/v1/coin-manage/burnAmount`

```javascript
{
    "code": 0,
    "message": "success",
    "data": "0"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |
| accountId    | true         | string   | 账户 ID  |

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**       |
| -------- | ------------ | -------- | -------------- |
| code     | true         | string   | 0 为正确       |
| message  | true         | string   | 成功或错误信息 |
| data     | true         | string   | 销毁数量       |

## 811链的区块高度查询

`GET api/v1/coin-manage/height`

```javascript
{
    "code": 0,
    "message": "success",
    "data": "3536048"
}
```
**请求参数：**无

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**       |
| -------- | ------------ | -------- | -------------- |
| code     | true         | string   | 0 为正确       |
| message  | true         | string   | 成功或错误信息 |
| data     | true         | string   | 区块高度       |

## 812查询代币的初始供应量和增发历史

`GET api/v1/coin-manage/tokenHistory`

```javascript
{
    "init_coin_supply": "10000700000000000",
    "add_coin_history": ""
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                                                                                   |
| -------- | ------------ | -------- | ---------------------------------------------------------------------------------------------------------- |
| code     | true         | string   | 0 为正确                                                                                                   |
| message  | true         | string   | 成功或错误信息                                                                                             |
| data     | true         | string   | json 字符串，含有初始供应量和增发历史的键值对，例如：'{"init_coin_supply":"xxx","add_coin_history":"xxx"}' |


## 813加入黑名单

`POST api/v1/coin-manage/addBlack`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0xeb794dd70000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677642609",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677642609"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：


## 814移出黑名单

`POST api/v1/coin-manage/removeBlack`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0xd283859d0000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677642805",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677642805"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 815添加转入黑名单


`POST api/v1/coin-manage/addBlackIn`


```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0xf62554350000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643029",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643029"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 816移出转入黑名单

`POST api/v1/coin-manage/removeBlackIn`


```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x409de8910000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643129",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643129"
}
```
**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态



## 817添加转出黑名单

`POST api/v1/coin-manage/addBlackOut`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0xd0dba9440000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643214",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643214"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态



## 818移出转出黑名单


`POST api/v1/coin-manage/removeBlackOut`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |
| targetId     | true         | string   | 目标账户 ID   |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x8f9abdf90000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643287",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643287"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态



## 819冻结


`POST api/v1/coin-manage/frozen`


```javascript
{
    "amount":"1000",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**               |
| ------------ | ------------ | -------- | ---------------------- |
| amount       | true         | string   | 冻结的数量（带有精度） |
| contractAddr | true         | string   | 代币地址               |
| operatorId   | true         | string   | 操作者账户 ID          |
| targetId     | true         | string   | 目标账户 ID            |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x361737640000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d000000000000000000000000000000000000000000000000000000000000003e8",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643398",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643398"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 820解冻

`POST api/v1/coin-manage/unfrozen`

```javascript
{
    "amount":"1",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**               |
| ------------ | ------------ | -------- | ---------------------- |
| amount       | true         | string   | 冻结的数量（带有精度） |
| contractAddr | true         | string   | 代币地址               |
| operatorId   | true         | string   | 操作者账户 ID          |
| targetId     | true         | string   | 目标账户 ID            |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0xe5df3dd00000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d00000000000000000000000000000000000000000000000000000000000000001",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643485",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643485"
}
```
**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                                           |
| -------- | ------------ | -------- | ------------------------------------------------------------------ |
| code     | true         | string   | 0 为正确                                                           |
| message  | true         | string   | 成功或错误信息                                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"}交易发出成功提示 |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 821添加区块高度间交易黑名单

`POST api/v1/coin-manage/addBlackRange`

```javascript
{
    "startblock":"200",
    "endblock":"3000",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| startblock   | true         | string   | 起始区块高度  |
| endblock     | true         | string   | 终止区块高度  |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x46f903c600000000000000000000000000000000000000000000000000000000000000c80000000000000000000000000000000000000000000000000000000000000bb8",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643619",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643619"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 822移出区块高度间交易黑名单

`POST api/v1/coin-manage/removeBlackRange`

```javascript
{
    "index":"0",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| index        | true         | string   | 区间索引      |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x254cf7950000000000000000000000000000000000000000000000000000000000000000",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677643699",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677643699"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态



## 823铸造（增发）

`POST api/v1/coin-manage/mint`

```javascript
{
    "amount":"1000",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| amount       | true         | string   | 铸造的数量    |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x40c10f190000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d000000000000000000000000000000000000000000000000000005af3107a4000",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677651290",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677651290"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 824销毁

`POST api/v1/coin-manage/burn`

```javascript
{
    "amount":"10",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```

**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| amount       | true         | string   | 销毁的数量    |
| contractAddr | true         | string   | 代币地址      |
| operatorId   | true         | string   | 操作者账户 ID |

```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x42966c68000000000000000000000000000000000000000000000000000000000000000a",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677651387",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677651387"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态



## 825销毁指定账户下的代币

`POST api/v1/coin-manage/burnFrom`

```javascript
{
    "amount":"10",
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "operatorId":"LDgtR1ZQdFiCbBY",
    "targetId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**               |
| ------------ | ------------ | -------- | ---------------------- |
| amount       | true         | string   | 销毁的数量（带有精度） |
| contractAddr | true         | string   | 代币地址               |
| operatorId   | true         | string   | 操作者账户 ID          |
| targetId     | true         | string   | 目标账户 ID            |


```javascript
{
    "from": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
    "to": "0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "data": "0x79cc67900000000000000000000000008e93ed5792a279dc3ac72c5bc24fe24da7d9b5d0000000000000000000000000000000000000000000000000000000000000000a",
    "chainId": "0x22B8",
    "value": "0x0",
    "requestId": "1677651477",
    "uid": "LDgtR1ZQdFiCbBY",
    "uuid": "1677651477"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                           |
| -------- | ------------ | -------- | -------------------------------------------------- |
| code     | true         | string   | 0 为正确                                           |
| message  | true         | string   | 成功或错误信息                                     |
| data     | true         | string   | json 字符串，类似{"requestId":"xxx","uuid": "xxx"} |

**备注**：返回成功表示成功调用了合约交易，需要用返回的 data 中的 requestId 调用本页面的最后一个接口：查询合约交易的状态


## 826查询账户的冻结代币数量

`POST api/v1/coin-manage/forzenAmount`


```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "accountId":"LDgtR1ZQdFiCbBY",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明**      |
| ------------ | ------------ | -------- | ------------- |
| contractAddr | true         | string   | 代币地址      |
| accountId    | true         | string   | 操作者账户 ID |


```javascript
{
    "code": 0,
    "message": "success",
    "data": "999"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**       |
| -------- | ------------ | -------- | -------------- |
| code     | true         | string   | 0 为正确       |
| message  | true         | string   | 成功或错误信息 |
| data     | true         | string   | 冻结数量       |


## 827查询代币的总容量


`POST api/v1/coin-manage/cap`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

```javascript
{
    "code": 0,
    "message": "success",
    "data": "10000700000000000"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**       |
| -------- | ------------ | -------- | -------------- |
| code     | true         | string   | 0 为正确       |
| message  | true         | string   | 成功或错误信息 |
| data     | true         | string   | 总容量         |



## 828查询代币的闪电费用比例

`POST api/v1/coin-manage/flashFee`

```javascript
{
    "contractAddr":"0xa97a7e49930c91d7bba6a115f01a5c41a6218676",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |

```javascript
{
    "code": 0,
    "message": "success",
    "data": "20"
}
```

**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**         |
| -------- | ------------ | -------- | ---------------- |
| code     | true         | string   | 0 为正确         |
| message  | true         | string   | 成功或错误信息   |
| data     | true         | string   | 代币的闪电费比例 |



## 829查询代币的禁止交易区间

`POST api/v1/coin-manage/blackRange`

```javascript
{
    "contractAddr":"0x610e2ac7849720c9e89a5c50f81c3370987451c7",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**     | **是否必须** | **类型** | **说明** |
| ------------ | ------------ | -------- | -------- |
| contractAddr | true         | string   | 代币地址 |



**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                |
| -------- | ------------ | -------- | --------------------------------------- |
| code     | true         | string   | 0 为正确                                |
| message  | true         | string   | 成功或错误信息                          |
| data     | true         | string   | json 字符串，可转化为交易区间结构体数组 |

交易区间结构体定义如下：

| **参数**   | **是否必须** | **类型** | **说明** |
| ---------- | ------------ | -------- | -------- |
| BeginBlock | true         | string   | 起始区间 |
| EndBlock   | true         | string   | 结束区间 |

## 830查询合约交易的状态

`POST api/v1/coin-manage/txStatus`

```javascript
{
    "accountId":"LDgtR1ZQdFiCbBY",
    "requestId":"1677643398",
    "apiKey": "gX3bWaCYWXx7",
    "nonce": "{{nonce}}",
    "verified": "{{verify}}"
}
```
**请求参数：**

| **参数**  | **是否必须** | **类型** | **说明**                                   |
| --------- | ------------ | -------- | ------------------------------------------ |
| accountId | true         | string   | 账户 ID                                    |
| requestId | true         | string   | 合约交易成功发出后返回的字串中的 requestId |


```javascript
{
    "requestId": "1677643398",
    "hash": "0xa6530534ecc35f04f45002a27e112d4f14641f466868fa9542d555dfe2638ba0",
    "code": 0,
    "message": "ok",
    "status": 1,
    "tx_hash": "0xa6530534ecc35f04f45002a27e112d4f14641f466868fa9542d555dfe2638ba0"
}
```


**返回参数:**

| **参数** | **是否必须** | **类型** | **说明**                                                                                                                                                                                                                                                     |
| -------- | ------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| code     | true         | string   | 0 为正确                                                                                                                                                                                                                                                     |
| message  | true         | string   | 成功或错误信息(succes 或 fail)                                                                                                                                                                                                                               |
| data     | true         | string   | 任务的详情（"{\"requestId\":\"1677491187\",\"hash\":\"0x6c7308c10c9be1c43c212161fc2a84df3f8e79c374857032e71120cb25ab4d13\",\"code\":0,\"message\":\"ok\",\"status\":1,\"tx_hash\":\"0x6c7308c10c9be1c43c212161fc2a84df3f8e79c374857032e71120cb25ab4d13\"}"） |
