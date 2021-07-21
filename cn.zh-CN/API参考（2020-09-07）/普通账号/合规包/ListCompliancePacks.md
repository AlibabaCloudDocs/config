# ListCompliancePacks

调用ListCompliancePacks接口查询合规包列表。

本文将提供一个示例，查询合规包列表。返回结果显示有一条合规包记录`cp-fdc8626622af00f9****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListCompliancePacks&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListCompliancePacks|要执行的操作，取值：**ListCompliancePacks**。 |
|Status|String|否|ACTIVE|合规包状态。取值：

 -   ACTIVE：正常。
-   CREATING：创建中。 |
|PageSize|Integer|否|10|分页时每页显示的数据行数。

 取值范围：1~100。起始值：1。默认值：10。 |
|PageNumber|Integer|否|1|页码。

 起始值：1。默认值：1。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|CompliancePacksResult|Object| |合规包列表查询结果。 |
|CompliancePacks|Array of CompliancePacks| |合规包列表。 |
|Status|String|ACTIVE|合规包状态。取值：

 -   ACTIVE：正常。
-   CREATING：创建中。 |
|CompliancePackId|String|cp-fdc8626622af00f9\*\*\*\*|合规包ID。 |
|RiskLevel|Integer|1|合规包中托管规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|Description|String|基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。|合规包描述。 |
|CompliancePackName|String|等保三级预检合规包|合规包名称。 |
|AccountId|Long|120886317861\*\*\*\*|合规包归属的阿里云账号ID。 |
|CompliancePackTemplateId|String|ct-5f26ff4e06a300c4\*\*\*\*|合规包模板ID。 |
|CreateTimestamp|Long|1621325046000|创建合规包的时间戳。单位：毫秒。 |
|PageSize|Integer|10|分页时每页显示的数据行数。 |
|PageNumber|Integer|1|页码。 |
|TotalCount|Long|1|合规包总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListCompliancePacks
&Status=ACTIVE
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListCompliancePacksResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<CompliancePacksResult>
		<TotalCount>1</TotalCount>
		<PageSize>10</PageSize>
		<PageNumber>1</PageNumber>
		<CompliancePacks>
			<Status>ACTIVE</Status>
			<CompliancePackId>cp-fdc8626622af00f9****</CompliancePackId>
			<Description>基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。</Description>
			<CompliancePackName>等保三级预检合规包</CompliancePackName>
			<AccountId>120886317861****</AccountId>
			<CompliancePackTemplateId>ct-5f26ff4e06a300c4****</CompliancePackTemplateId>
			<RiskLevel>1</RiskLevel>
		</CompliancePacks>
	</CompliancePacksResult>
</ListCompliancePacksResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "CompliancePacksResult" : {
    "TotalCount" : 1,
    "PageSize" : 10,
    "PageNumber" : 1,
    "CompliancePacks" : [ {
      "Status" : "ACTIVE",
      "CompliancePackId" : "cp-fdc8626622af00f9****",
      "Description" : "基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。",
      "CompliancePackName" : "等保三级预检合规包",
      "AccountId" : "120886317861****",
      "CompliancePackTemplateId" : "ct-5f26ff4e06a300c4****",
      "RiskLevel" : 1
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

