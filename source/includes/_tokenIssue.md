# 7发币

## 71发币

`POST api/v1/token/create`

**请求参数**

| **参数**    | **是否必须** | **类型** | **说明**                                                                                 |
| ----------- | ------------ | -------- | ---------------------------------------------------------------------------------------- |
| accountId   | true         | string   | 账户 id，具有唯一性                                                                      |
| addr        | true         | string   | 用户的 HuiOne 链地址                                                                     |
| name        | true         | string   | 代币名称                                                                                 |
| symbol      | true         | string   | 代币标识                                                                                 |
| decimal     | true         | int      | 小数位（0-18）                                                                           |
| minter      | true         | string   | minter 地址                                                                              |
| operator    | true         | string   | 操作员地址                                                                               |
| amount      | true         | bigInt   | 初始发币数量                                                                             |
| receiver    | true         | string   | 接收地址                                                                                 |
| cap         | true         | bigInt   | 代币可发行总量：0:表示无限增发                                                           |
| type        | true         | int      | 代币模型：1、SIMPLE 2、SNAPSHOT 3、VOTES 4、FLASHMINT 5、BURNABLE 6、CAPPED 7、DEFLATION |
| iconAddress | false        | string   | 代币 icon 地址（完整 url 地址）                                                          |
| taxFee      | false        | int      | 手续费-百万分之（适用通缩、闪电贷两种代币模型）                                          |
| bonusFee    | false        | int      | 分红比例-百万分之（适用通缩模型）                                                        |

**返回参数**

| **参数** | **类型** | **说明**                         |
| -------- | -------- | -------------------------------- |
| orderId  | String   | 订单号（通过订单号查询发币结果） |

> 返回示例

```javascript
{
  "code": 0,
    "msg": null,
    "data": {
    "orderId": "fd6a6944-a0aa-4bdc-8cfd-3cd962083c27"
  },
  "success": true
}

```

## 72查询发币状态

`GET api/v1/token/status`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**            |
| --------- | ------------ | -------- | ------------------- |
| accountId | true         | String   | 账户 id，具有唯一性 |
| orderId   | true         | String   | 订单 ID             |

**返回参数**

| **参数**     | **类型** | **说明**                                                                |
| ------------ | -------- | ----------------------------------------------------------------------- |
| tokenAddress | String   | 代币地址（代币地址为空表示还在处理中或者出错了，错误信息查看：message） |

> 返回示例

```javascript
{
  "code": 0,
    "msg": null,
    "data": {
    "tokenAddress": "0x2bd3aaadc599c59e57f638ec6a31b96a23105f7f"
  },
  "success": true
}


```

## 73查询发币订单详情

`GET api/v1/token/order/detail`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**            |
| --------- | ------------ | -------- | ------------------- |
| accountId | true         | String   | 账户 id，具有唯一性 |
| orderId   | true         | String   | 订单 ID             |

**返回参数**

| **参数**    | **类型** | **说明**                                                                                           |
| ----------- | -------- | -------------------------------------------------------------------------------------------------- |
| tokenType   | int      | 代币标准；默认 1:ERC20；2:ERC721；3:ERC1155                                                        |
| holders     | int      | 持币地址数                                                                                         |
| accountId   | String   | 账户 id，发币请求唯一 ID                                                                           |
| decimal     | int      | 小数位                                                                                             |
| minter      | String   | 有权增发代币的地址                                                                                 |
| operator    | String   | 代币操作员                                                                                         |
| amount      | bigInt   | 出售发币数量                                                                                       |
| receiver    | String   | 初始发币接受地址                                                                                   |
| icon        | String   | 代币 icon 地址                                                                                     |
| contract    | String   | 代币合约地址                                                                                       |
| status      | int      | 订单状态（0:创建；4:发币成功；5:发币失败）                                                         |
| reason      | String   | 失败原因                                                                                           |
| createTime  | long     | 记录创建时间                                                                                       |
| updateTime  | long     | 记录更新时间                                                                                       |
| name        | String   | 代币名称                                                                                           |
| symbol      | String   | 代币标识                                                                                           |
| model       | int      | 代币模型 1:基础模型；2:快照模型；3:治理投票模型；4:闪电贷模型；5:燃烧模型；6:增发模型；7；通缩模型 |
| taxFee      | int      | 闪电贷模型代表贷款费率；通缩模型代表通缩费率；基数都是一百万                                       |
| bonusFee    | int      | 通缩代币，代币分红比例                                                                             |
| paused      | boolean  | 代币是否被平台设置成暂停状态                                                                       |
| totalSupply | bigInt   | 流通量                                                                                             |
| cap         | bigInt   | 代币可发行总量                                                                                     |
| remainMint  | bigInt   | 代币剩余可发行量                                                                                   |
| blockNumber | long     | 区块高度                                                                                           |
| blockPaused | boolean  | 代币当前是否被项目方设置为区块暂停                                                                 |

> 返回示例

```javascript
{
  "code": 0,
    "msg": null,
    "data": {
    "tokenType": 1,
      "holders": 0,
      "uid": "LDgtR1ZQdFiCbBY",
      "decimal": 3,
      "minter": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "operator": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "amount": "10007700000000000",
      "receiver": "0x4c47DEAfe0C5b5632636eeBdc71909C45aa2ED23",
      "contract": "0x2bd3aaadc599c59e57f638ec6a31b96a23105f7f",
      "status": 4,
      "reason": null,
      "createTime": 1677747355000,
      "updateTime": 1677747359000,
      "name": "3月2日通缩代币0712",
      "symbol": "sdkt",
      "model": 7,
      "taxFee": 35500,
      "bonusFee": 0,
      "paused": false,
      "totalSupply": "10007699999881253",
      "cap": "10607800000000000",
      "remainMint": "10607800000000000",
      "blockNumber": "3590801",
      "blockPaused": false,
      "addr": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "orderId": "fd6a6944-a0aa-4bdc-8cfd-3cd962083c27",
      "iconAddress": "https://images.pexels.com/photos/10768835/pexels-photo-10768835.jpeg"
  },
  "success": true
}

```

## 74查询发币记录

`GET api/v1/token/order/list`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**            |
| --------- | ------------ | -------- | ------------------- |
| accountId | true         | String   | 账户 id，具有唯一性 |

**返回参数**

| **参数**   | **类型** | **说明**                                   |
| ---------- | -------- | ------------------------------------------ |
| orderId    | String   | 订单 ID                                    |
| name       | String   | 代币名称                                   |
| symbol     | String   | 代币标识                                   |
| status     | int      | 订单状态（0:创建；4:发币成功；5:发币失败） |
| createTime | long     | 创建时间                                   |

> 返回示例

```javascript
{
  "code": 0,
    "msg": null,
    "data": [
    {
      "tokenType": 1,
      "holders": 0,
      "uid": "LDgtR1ZQdFiCbBY",
      "decimal": 3,
      "minter": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "operator": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "amount": "10007700000000000",
      "receiver": "0x4c47DEAfe0C5b5632636eeBdc71909C45aa2ED23",
      "contract": "0x2bd3aaadc599c59e57f638ec6a31b96a23105f7f",
      "status": 4,
      "reason": null,
      "createTime": 1677747355000,
      "updateTime": 1677747359000,
      "name": "3月2日通缩代币0712",
      "symbol": "sdkt",
      "model": 7,
      "taxFee": 35500,
      "bonusFee": 0,
      "paused": false,
      "totalSupply": "10007700000000000",
      "cap": "10607800000000000",
      "remainMint": "10607800000000000",
      "blockNumber": "3588633",
      "blockPaused": false,
      "addr": "0x8E93ed5792a279DC3Ac72C5bC24FE24Da7d9B5d0",
      "orderId": "fd6a6944-a0aa-4bdc-8cfd-3cd962083c27",
      "iconAddress": "https://images.pexels.com/photos/10768835/pexels-photo-10768835.jpeg"
    }
  ],
    "success": true
}

```
