# GetAggregateConfigRuleComplianceByPack

调用GetAggregateConfigRuleComplianceByPack接口查询指定账号组内指定合规包中规则的合规结果。

本文将提供一个示例，查询账号组`ca-04b3fd170e340007****`内合规包`cp-541e626622af0087****`中规则的合规结果。返回结果显示规则总数`1`个，不合规规则数`0`个。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateConfigRuleComplianceByPack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateConfigRuleComplianceByPack|要执行的操作，取值：**GetAggregateConfigRuleComplianceByPack**。 |
|CompliancePackId|String|是|cp-541e626622af0087\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListAggregateCompliancePacks](~~262059~~)。 |
|AggregatorId|String|是|ca-04b3fd170e340007\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C6B0C0A8-3245-48F1-AEAB-BC1A446E99D0|请求ID。 |
|ConfigRuleComplianceResult|Object| |合规包中规则的合规结果。 |
|CompliancePackId|String|cp-541e626622af0087\*\*\*\*|合规包ID。 |
|NonCompliantCount|Integer|0|不合规规则数。 |
|ConfigRuleCompliances|Array of ConfigRuleCompliances| |规则合规包列表。 |
|ComplianceType|String|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ConfigRuleName|String|弹性IP实例带宽满足最低要求|合规包中的规则名称。 |
|ConfigRuleId|String|cr-fdc8626622af00f9\*\*\*\*|合规包中的规则ID。 |
|TotalCount|Integer|1|规则总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateConfigRuleComplianceByPack
&CompliancePackId=cp-541e626622af0087****
&AggregatorId=ca-04b3fd170e340007****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateConfigRuleComplianceByPackResponse>
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
</GetAggregateConfigRuleComplianceByPackResponse>
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
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

