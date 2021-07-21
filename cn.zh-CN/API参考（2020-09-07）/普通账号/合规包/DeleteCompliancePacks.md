# DeleteCompliancePacks

调用DeleteCompliancePacks接口删除合规包。

本文将提供一个示例，删除合规包`cp-541e626622af0087****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DeleteCompliancePacks&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCompliancePacks|要执行的操作，取值：**DeleteCompliancePacks**。 |
|CompliancePackIds|String|是|cp-541e626622af0087\*\*\*\*|合规包ID。多个合规包ID之间用半角逗号（,）分隔。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |
|ClientToken|String|否|AAAAAdDWBF2\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|OperateCompliancePacksResult|Object| |删除合规包的操作结果。 |
|OperateCompliancePacks|Array of OperateCompliancePacks| |删除合规包的列表。 |
|CompliancePackId|String|cp-541e626622af0087\*\*\*\*|合规包ID。 |
|ErrorCode|String|CompliancePackAlreadyPending|错误码。

 -   当您删除合规包成功时，该参数为空。
-   当您删除合规包失败时，该参数显示错误码。错误码详情，请参见[错误中心](https://error-center.aliyun.com/status/product/Config)。 |
|Success|Boolean|true|操作是否成功。取值：

 -   true：成功。
-   false：失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteCompliancePacks
&CompliancePackIds=cp-541e626622af0087****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteCompliancePacksResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<OperateCompliancePacksResult>
		<OperateCompliancePacks>
			<CompliancePackId>cp-541e626622af0087****</CompliancePackId>
			<ErrorCode></ErrorCode>
			<Success>true</Success>
		</OperateCompliancePacks>
	</OperateCompliancePacksResult>
</DeleteCompliancePacksResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "OperateCompliancePacksResult" : {
    "OperateCompliancePacks" : [ {
      "CompliancePackId" : "cp-541e626622af0087****",
      "ErrorCode" : "",
      "Success" : true
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.CompliancePackIds.SizeExceed|The maximum number of CompliancePackIds is 5.|合规包ID不能超过5个。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

