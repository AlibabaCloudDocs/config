# GetConfigRulesReport

调用GetConfigRulesReport接口下载规则列表中所有规则的评估报告。

**说明：** 调用本接口下载评估报告之前，您需要先调用GenerateConfigRulesReport接口生成最新评估报告。更多信息，请参见[GenerateConfigRulesReport](~~263601~~)。

本文将提供一个示例，下载规则列表中所有规则的评估报告。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetConfigRulesReport&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetConfigRulesReport|要执行的操作，取值：**GetConfigRulesReport**。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|ConfigRulesReport|Object| |规则列表中所有规则的评估报告。 |
|ReportStatus|String|CREATING|规则列表中所有规则的评估报告状态。取值：

 -   NONE：未创建。
-   CREATING：创建中。
-   COMPLETE：完成。 |
|ReportUrl|String|https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/ConfigRuleReports/100931896542\*\*\*\*/rules/100931896542\*\*\*\*-rules-report-202106221125.zip?Expires=162433\*\*\*\*&OSSAccessKeyId=LTAIs86R8H59\*\*\*\*&Signature=yT8jn6ZQSX3dyCwVKL5EOJhGJ\*\*\*\*|规则列表中所有规则的评估报告下载地址。 |
|AccountId|Long|100931896542\*\*\*\*|规则归属的阿里云账号ID。 |
|ReportCreateTimestamp|Long|1614687022000|创建评估报告的时间戳。单位：毫秒。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetConfigRulesReport
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetConfigRulesReportResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<ConfigRulesReport>
		<AccountId>100931896542****</AccountId>
		<ReportUrl>https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/ConfigRuleReports/100931896542****/rules/100931896542****-rules-report-202106221125.zip?Expires=162433****&amp;OSSAccessKeyId=LTAIs86R8H59****&amp;Signature=yT8jn6ZQSX3dyCwVKL5EOJhGJ****</ReportUrl>
		<ReportCreateTimestamp>1614687022000</ReportCreateTimestamp>
		<ReportStatus>CREATING</ReportStatus>
	</ConfigRulesReport>
</GetConfigRulesReportResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "ConfigRulesReport" : {
    "AccountId" : "100931896542****",
    "ReportUrl" : "https://cloud-config-compliance-report.oss-cn-shanghai.aliyuncs.com/ConfigRuleReports/100931896542****/rules/100931896542****-rules-report-202106221125.zip?Expires=162433****&OSSAccessKeyId=LTAIs86R8H59****&Signature=yT8jn6ZQSX3dyCwVKL5EOJhGJ****",
    "ReportCreateTimestamp" : 1614687022000,
    "ReportStatus" : "CREATING"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

