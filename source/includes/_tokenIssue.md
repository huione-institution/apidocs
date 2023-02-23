# **发币**
## **发币**


`POST api/v1/token/create`

**请求参数**



| **参数**      | **是否必须** | **类型** | **说明**                                            |
|----------------------| ------------ | -------- | --------------------------------------------------- |
|accountId|true       |String |账户id，具有唯一性|
|addr|true|String|用户的HuiOne链地址|
|name|true|String|代币名称|
|symbol|true|String|代币标识|
|decimal|true|int|小数位（0-18）|
|minter|true|String|minter地址|
|operator|true|String|操作员地址|
|amount|true|bigInt|初始发币数量|
|receiver|true|String|接收地址|
|cap|true|bigInt|代币可发行总量：0:表示无限增发|
|type|true|int|代币模型：1、SIMPLE 2、SNAPSHOT 3、VOTES 4、FLASHMINT 5、BURNABLE 6、CAPPED 7、DEFLATION|
|iconAddress|false|String|代币icon地址（完整url地址）|
|taxFee|false|int|手续费-百万分之（适用通缩、闪电贷两种代币模型）|
|bonueFee|false|int|分红比例-百万分之（适用通缩模型）|


**返回参数**

| **参数**      | **类型** | **说明**                                            |
|---------------------- | -------- | --------------------------------------------------- |
|orderId|String|订单号（通过订单号查询发币结果）|
## **查询发币状态**

`GET api/v1/token/status`

**请求参数**

| **参数**      | **是否必须** | **类型** | **说明**                                            |
|----------------------| ------------ | -------- | --------------------------------------------------- |
|accountId|true|String|账户id，具有唯一性|
|orderId|true|String|订单ID|
**返回参数**

| **参数**      | **类型** | **说明**                                            |
|---------------------- | -------- | --------------------------------------------------- |
|tokenAddress|String|代币地址（代币地址为空表示还在处理中或者出错了，错误信息查看：message）|
## **查询发币订单详情**

`GET api/v1/token/order/detail`


**请求参数**

| **参数**      | **是否必须** | **类型** | **说明**                                            |
|----------------------| ------------ | -------- | --------------------------------------------------- |
|accountId|true|String|账户id，具有唯一性|
|orderId|true|String|订单ID|
**返回参数**

| **参数**      | **类型** | **说明**                                            |
|---------------------- | -------- | --------------------------------------------------- |
|tokenType|int|代币标准；默认1:ERC20；2:ERC721；3:ERC1155|
|holders|int|持币地址数|
|accountId|String|账户id，发币请求唯一ID|
|decimal|int|小数位|
|minter|String|有权增发代币的地址|
|operator|String|代币操作员|
|amount|bigInt|出售发币数量|
|receiver|String|初始发币接受地址|
|icon|String|代币icon地址|
|contract|String|代币合约地址|
|status|int|订单状态（0:创建；4:发币成功；5:发币失败）|
|reason|String|失败原因|
|createTime|long|记录创建时间|
|updateTime|long|记录更新时间|
|name|String|代币名称|
|symbol|String|代币标识|
|model|int|代币模型1:基础模型；2:快照模型；3:治理投票模型；4:闪电贷模型；5:燃烧模型；6:增发模型；7；通缩模型|
|taxFee|int|闪电贷模型代表贷款费率；通缩模型代表通缩费率；基数都是一百万|
|bonusFee|int|通缩代币，代币分红比例|
|paused|boolean|代币是否被平台设置成暂停状态|
|totalSupply|bigInt|流通量|
|cap|bigInt|代币可发行总量|
|remainMint|bigInt|代币剩余可发行量|
|blockNumber|long|区块高度|
|blockPaused|boolean|代币当前是否被项目方设置为区块暂停|
## **查询发币记录**

`GET api/v1/token/order/list`

**请求参数**

| **参数**      | **是否必须** | **类型** | **说明**                                            |
|----------------------| ------------ | ------- | --------------------------------------------------- |
|accountId|true|String|账户id，具有唯一性|
**返回参数**

| **参数**      | **类型** | **说明**                                            |
|---------------------- | -------- | --------------------------------------------------- |
|orderId|String|订单ID|
|name|String|代币名称|
|symbol|String|代币标识|
|status|int|订单状态（0:创建；4:发币成功；5:发币失败）|
|createTime|long|创建时间|

