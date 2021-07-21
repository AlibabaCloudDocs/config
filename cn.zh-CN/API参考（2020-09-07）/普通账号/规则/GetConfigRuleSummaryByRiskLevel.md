# GetConfigRuleSummaryByRiskLevel

调用GetConfigRuleSummaryByRiskLevel接口查询不同风险等级规则的合规概要。

本文将提供一个示例，查询不同风险等级规则的合规概要。返回结果显示，在高风险的规则中，有3条合规，有1条不合规。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetConfigRuleSummaryByRiskLevel&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetConfigRuleSummaryByRiskLevel|要执行的操作，取值：**GetConfigRuleSummaryByRiskLevel**。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A3CED98C-DE65-46AC-B2D2-04A4A9AB5B36|请求ID。 |
|ConfigRuleSummaries|Array of Data| |不同风险等级规则的合规概要。 |
|RiskLevel|Integer|1|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|CompliantCount|Integer|3|合规规则数。 |
|NonCompliantCount|Integer|1|不合规规则数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetConfigRuleSummaryByRiskLevel
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetConfigRuleSummaryByRiskLevelResponse>
    <RequestId>A3CED98C-DE65-46AC-B2D2-04A4A9AB5B36</RequestId>
    <ConfigRuleSummaries>
        <RiskLevel>1</RiskLevel>
        <CompliantCount>3</CompliantCount>
        <NonCompliantCount>1</NonCompliantCount>
    </ConfigRuleSummaries>
</GetConfigRuleSummaryByRiskLevelResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A3CED98C-DE65-46AC-B2D2-04A4A9AB5B36",
  "ConfigRuleSummaries" : [ {
    "RiskLevel" : 1,
    "CompliantCount" : 3,
    "NonCompliantCount" : 1
  } ]
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

