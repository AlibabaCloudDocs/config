# GetAggregateCompliancePackReport

调用GetAggregateCompliancePackReport接口下载指定账号组内指定合规包的评估报告。

**说明：** 调用本接口下载评估报告之前，您需要先调用GenerateAggregateCompliancePackReport接口生成最新评估报告。更多信息，请参见[GenerateAggregateCompliancePackReport](~~262687~~)。

本文将提供一个示例，下载账号组`ca-f632626622af0079****`内合规包`cp-fdc8626622af00f9****`的评估报告。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateCompliancePackReport&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateCompliancePackReport|要执行的操作，取值：**GetAggregateCompliancePackReport**。 |
|CompliancePackId|String|是|cp-fdc8626622af00f9\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListAggregateCompliancePacks](~~262059~~)。 |
|AggregatorId|String|是|ca-f632626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0D234DAC-1ABD-42E8-9475-BE317857E29B|请求ID。 |
|CompliancePackReport|Object| |合规包评估报告。 |
|ReportUrl|String|https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/CompliancePackReports/100931896542\*\*\*\*/cp-fdc8626622af00f9\*\*\*\*/100931896542\*\*\*\*-cp-fdc8626622af00f9\*\*\*\*-report-202106221050.zip?Expires=162433\*\*\*\*&OSSAccessKeyId=LTAIs86R8H59\*\*\*\*&Signature=RqvJZtaxQ2HfqRcl0Ic2HG8oo\*\*\*\*|合规包评估报告的下载地址。 |
|ReportStatus|String|COMPLETE|合规包评估报告的状态。取值：

 -   NONE：未创建。
-   CREATING：创建中。
-   COMPLETE：完成。 |
|CompliancePackId|String|cp-fdc8626622af00f9\*\*\*\*|合规包ID。 |
|AccountId|Long|100931896542\*\*\*\*|合规包归属的企业管理账号ID。 |
|ReportCreateTimestamp|Long|1624330246640|创建合规包评估报告的时间戳。单位：毫秒。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateCompliancePackReport
&CompliancePackId=cp-fdc8626622af00f9****
&AggregatorId=ca-f632626622af0079****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateCompliancePackReportResponse>
	<RequestId>0D234DAC-1ABD-42E8-9475-BE317857E29B</RequestId>
	<CompliancePackReport>
		<CompliancePackId>cp-fdc8626622af00f9****</CompliancePackId>
		<AccountId>100931896542****</AccountId>
		<ReportUrl>https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/CompliancePackReports/100931896542****/cp-fdc8626622af00f9****/100931896542****-cp-fdc8626622af00f9****-report-202106221050.zip?Expires=162433****&amp;OSSAccessKeyId=LTAIs86R8H59****&amp;Signature=RqvJZtaxQ2HfqRcl0Ic2HG8oo****</ReportUrl>
		<ReportStatus>COMPLETE</ReportStatus>
		<ReportCreateTimestamp>1624330246640</ReportCreateTimestamp>
	</CompliancePackReport>
</GetAggregateCompliancePackReportResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "0D234DAC-1ABD-42E8-9475-BE317857E29B",
  "CompliancePackReport" : {
    "CompliancePackId" : "cp-fdc8626622af00f9****",
    "AccountId" : "100931896542****",
    "ReportUrl" : "https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/CompliancePackReports/100931896542****/cp-fdc8626622af00f9****/100931896542****-cp-fdc8626622af00f9****-report-202106221050.zip?Expires=162433****&OSSAccessKeyId=LTAIs86R8H59****&Signature=RqvJZtaxQ2HfqRcl0Ic2HG8oo****",
    "ReportStatus" : "COMPLETE",
    "ReportCreateTimestamp" : 1624330246640
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

