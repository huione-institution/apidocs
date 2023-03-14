# 介绍

**API Key/Secret 说明**

- 所有接口均需要API Key和Secret加密信息才可以正常访问。
- **请妥善保管您的API key和secret**

**账户说明**

- 业务层通过提供用户唯一标识来申请支付账户。

**调用方式**

所有Api调用都需要在业务字段之外附加三个握手字段，go代码如下：

> go 代码如下

```go
ApiKey   string `json:"apiKey" binding:"required" example:"1233210123"`
Nonce    string `json:"nonce" binding:"required" example:"198964"`
Verified string `json:"verified" binding:"required" example:"BASE198964"`
```

> json 数据示例

```javascript
{
"apiKey": "gX3bWaCYWXx7",
"nonce": "123123",
"verified": "ABCD09123",
"otherBusinessFields": "..."
}
```

apiKey 就是您的申请到的 ApiKey

nonce 代表唯一的请求，避免被抓包重放。您可以用自增数字，也可以随便用随机数，只要保证近期不重复即可。即使业务上需要重试操作，nonce 也要变，认证握手和业务无关

verified 是校验字段，需要用到申请时给的 ApiSecret 来加密，具体的加密方式有提供 Javascript/Java 系列/Python/Go/Rust 等各种语言的样例可供参考，猛戳↓这里拿代码

**代码在这**

- golang示例 [下载](https://hwwallet.s3.ap-northeast-1.amazonaws.com/v1/api_demo/demo_go.zip)
- java示例 [下载](https://hwwallet.s3.ap-northeast-1.amazonaws.com/v1/api_demo/demo_jvm.zip)
- js示例 [下载](https://hwwallet.s3.ap-northeast-1.amazonaws.com/v1/api_demo/demo_js.zip)
- python示例 [下载](https://hwwallet.s3.ap-northeast-1.amazonaws.com/v1/api_demo/demo_py.zip)
- rust示例 [下载](https://hwwallet.s3.ap-northeast-1.amazonaws.com/v1/api_demo/demo_rs.zip)

**调用环境**

| **环境**      | **域名** | **api key申请** |
|-------------|--------|---------------|
| 测试环境 | https://api.alpha.huiwang.io   | <a href="https://t.me/+1VFnuoY1dfs0ZWRl" target="_blank">API Key申请</a>|
| 正式环境   | 待定   |               |
