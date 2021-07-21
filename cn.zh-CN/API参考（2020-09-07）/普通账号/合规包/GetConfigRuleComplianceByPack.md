# GetConfigRuleComplianceByPack

调用GetConfigRuleComplianceByPack接口查询合规包中规则的合规结果。

本文将提供一个示例，查询合规包`cp-541e626622af0087****`中规则的合规结果。返回结果显示规则总数为1个，不合规规则数为0个。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetConfigRuleComplianceByPack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetConfigRuleComplianceByPack|要执行的操作，取值：**GetConfigRuleComplianceByPack**。 |
|CompliancePackId|String|是|cp-541e626622af0087\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|ConfigRuleComplianceResult|Object| |合规包中规则的合规结果。 |
|CompliancePackId|String|cp-541e626622af0087\*\*\*\*|合规包ID。 |
|NonCompliantCount|Integer|0|不合规规则数。 |
|ConfigRuleCompliances|Array of ConfigRuleCompliances| |合规包中的规则及合规结果列表。 |
|ComplianceType|String|COMPLIANT|规则合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ConfigRuleName|String|弹性IP实例带宽满足最低要求|合规包中的规则名称。 |
|ConfigRuleId|String|cr-fdc8626622af00f9\*\*\*\*|合规包中的规则ID。 |
|TotalCount|Integer|1|合规包中的规则总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetConfigRuleComplianceByPack
&CompliancePackId=cp-541e626622af0087****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetConfigRuleComplianceByPackResponse>
	<RequestId>C6B0C0A8-3245-48F1-AEAB-BC1A446E99D0</RequestId>
	<ConfigRuleComplianceResult>
		<CompliancePackId>cp-541e626622af0087****</CompliancePackId>
		<ConfigRuleCompliances>
			<ConfigRuleId>cr-fdc8626622af00f9****</ConfigRuleId>
			<ComplianceType>COMPLIANT</ComplianceType>
			<ConfigRuleName>弹性IP实例带宽满足最低要求</ConfigRuleName>
		</ConfigRuleCompliances>
		<TotalCount>1</TotalCount>
		<NonCompliantCount>0</NonCompliantCount>
	</ConfigRuleComplianceResult>
</GetConfigRuleComplianceByPackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "C6B0C0A8-3245-48F1-AEAB-BC1A446E99D0",
  "ConfigRuleComplianceResult" : {
    "CompliancePackId" : "cp-541e626622af0087****",
    "ConfigRuleCompliances" : [ {
      "ConfigRuleId" : "cr-fdc8626622af00f9****",
      "ComplianceType" : "COMPLIANT",
      "ConfigRuleName" : "弹性IP实例带宽满足最低要求"
    } ],
    "TotalCount" : 1,
    "NonCompliantCount" : 0
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

