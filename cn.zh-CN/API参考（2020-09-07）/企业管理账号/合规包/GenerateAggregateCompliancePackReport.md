# GenerateAggregateCompliancePackReport

调用GenerateAggregateCompliancePackReport接口为指定账号组内的指定合规包生成评估报告。

**说明：** 调用本接口仅生成最新评估报告，您还需要调用GetAggregateCompliancePackReport接口下载该评估报告。更多信息，请参见[GetAggregateCompliancePackReport](~~262699~~)。

本文将提供一个示例，为账号组`ca-f632626622af0079****`内的合规包`cp-fdc8626622af00f9****`生成评估报告。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GenerateAggregateCompliancePackReport&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GenerateAggregateCompliancePackReport|要执行的操作，取值：**GenerateAggregateCompliancePackReport**。 |
|CompliancePackId|String|是|cp-fdc8626622af00f9\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListAggregateCompliancePacks](~~262059~~)。 |
|ClientToken|String|否|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。 |
|AggregatorId|String|是|ca-f632626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CompliancePackId|String|cp-fdc8626622af00f9\*\*\*\*|合规包ID。 |
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GenerateAggregateCompliancePackReport
&CompliancePackId=cp-fdc8626622af00f9****
&AggregatorId=ca-f632626622af0079****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GenerateAggregateCompliancePackReportResponse>
	<CompliancePackId>cp-fdc8626622af00f9****</CompliancePackId>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
</GenerateAggregateCompliancePackReportResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "CompliancePackId" : "cp-fdc8626622af00f9****",
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|CompliancePackReportCreating|The compliance pack report is being created.|合规包报告正在创建中。|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

