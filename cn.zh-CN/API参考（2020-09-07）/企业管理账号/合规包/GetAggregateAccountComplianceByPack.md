# GetAggregateAccountComplianceByPack

调用GetAggregateAccountComplianceByPack接口查询指定账号组内指定合规包中成员账号的合规结果。

本文将提供一个示例，查询账号组`ca-04b3fd170e340007****`内合规包`cp-541e626622af0087****`中成员账号的合规结果。返回结果显示，成员账号总数为2个，不合规成员账号数为0个。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateAccountComplianceByPack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateAccountComplianceByPack|要执行的操作，取值：**GetAggregateAccountComplianceByPack**。 |
|CompliancePackId|String|是|cp-541e626622af0087\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListAggregateCompliancePacks](~~262059~~)。 |
|AggregatorId|String|是|ca-04b3fd170e340007\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|AccountComplianceResult|Object| |合规包中成员账号的合规结果。 |
|CompliancePackId|String|cp-541e626622af0087\*\*\*\*|合规包ID。 |
|NonCompliantCount|Integer|0|不合规成员账号数。 |
|TotalCount|Integer|2|成员账号总数。 |
|AccountCompliances|Array of AccountCompliances| |成员账号的合规结果列表。 |
|ComplianceType|String|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|AccountId|Long|100931896542\*\*\*\*|账号组中的成员账号ID。 |
|AccountName|String|Alice|账号组中的成员账号名称。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateAccountComplianceByPack
&CompliancePackId=cp-541e626622af0087****
&AggregatorId=ca-04b3fd170e340007****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateAccountComplianceByPackResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<AccountComplianceResult>
		<CompliancePackId>cp-541e626622af0087****</CompliancePackId>
		<TotalCount>2</TotalCount>
		<NonCompliantCount>0</NonCompliantCount>
		<AccountCompliances>
			<AccountId>100931896542****</AccountId>
			<ComplianceType>COMPLIANT</ComplianceType>
			<AccountName>Alice</AccountName>
		</AccountCompliances>
		<AccountCompliances>
			<AccountId>171322098523****</AccountId>
			<ComplianceType>COMPLIANT</ComplianceType>
			<AccountName>Jim</AccountName>
		</AccountCompliances>
	</AccountComplianceResult>
</GetAggregateAccountComplianceByPackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "AccountComplianceResult" : {
    "CompliancePackId" : "cp-541e626622af0087****",
    "TotalCount" : 2,
    "NonCompliantCount" : 0,
    "AccountCompliances" : [ {
      "AccountId" : "100931896542****",
      "ComplianceType" : "COMPLIANT",
      "AccountName" : "Alice"
    }, {
      "AccountId" : "171322098523****",
      "ComplianceType" : "COMPLIANT",
      "AccountName" : "Jim"
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

