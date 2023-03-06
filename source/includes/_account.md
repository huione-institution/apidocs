# 2账户(account)

账户模块遵循[Api 调用规范](#45fa4e00db)，所以此处只提供调用需要的业务字段

## 21创建账户

该任务通过和业务方提前约定好的UserID信息为业务方用户生成accountID和链上地址

`POST api/v1/account/create`

**请求参数**

| **参数** | **是否必须** | **类型** | **说明**                                                                                                        |
| -------- | ------------ | -------- | --------------------------------------------------------------------------------------------------------------- |
| apiKey   | true         | string   |                                                                                                                 |
| userId   | true         | string   | 用户 ID，业务方自己生成并控制在自己范围内唯一，可以是手机或者邮箱等，但需要保持一致（始终用手机或者始终用邮箱） |

**返回参数**

| **参数**  | **类型** | **说明**            |
| --------- | -------- | ------------------- |
| userId    | string   |                     |
| accountId | string   | 账户 ID，具有唯一性 |
| eth       | string   | eth 系链地址        |
| btc       | string   | btc 链地址          |
| trx       | string   | trx 系链地址        |

## 22账户地址查询

`GET api/v1/account/query?accountId=XXX`

**请求参数**

| **参数**  | **是否必须** | **类型** | **说明**                |
| --------- | ------------ | -------- | ----------------------- |
| accountId | true         | string   | 账户 ID，具有全局唯一性 |

**返回参数**

| **参数**  | **类型** | **说明** |
| --------- | -------- | -------- |
| userId    | string   | 用户信息 |
| accountId | string   | 账户 ID  |
| eth       | string   | 链地址   |
| btc       | string   | 链地址   |
| trx       | string   | 链地址   |

## 23账户查询(通过用户名）

`GET api/v1/account/queryUser`

**请求参数**

| **参数** | **是否必须** | **类型** | **说明** |
| -------- | ------------ | -------- | -------- |
| apiKey   | true         | string   |          |
| userId   | true         | string   | 用户 ID  |

**返回参数**

| **参数**  | **类型** | **说明** |
| --------- | -------- | -------- |
| userId    | string   | 用户信息 |
| accountId | string   | 账户 ID  |
| eth       | string   | 链地址   |
| btc       | string   | 链地址   |
| trx       | string   | 链地址   |

## 24账户列表（翻页）

`GET api/v1/account/list`

**请求参数**

| **参数** | **是否必须** | **类型** | **说明**                     |
| -------- | ------------ | -------- | ---------------------------- |
| apiKey   | true         | string   |                              |
| start    | true         | int      | 账户注册的时间范围之起始时间 |
| end      | true         | int      | 账户注册的时间范围之结束时间 |
| page     | false        | int      | 页号                         |
| limit    | false        | int      | 一页多少条记录               |

**返回参数**

| **参数**       | **类型** | **说明** |
| -------------- | -------- | -------- |
| list>userId    | string   | 用户信息 |
| list>accountId | string   | 账户 ID  |
| list>eth       | string   | 链地址   |
| list>btc       | string   | 链地址   |
| list>trx       | string   | 链地址   |
