# GetResourceComplianceByPack

调用GetResourceComplianceByPack接口查询合规包中资源的合规结果。

本文将提供一个示例，查询合规包`cp-541e626622af0087****`中资源的合规结果。返回结果显示，资源总数为10个，不合规资源数为7个。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceComplianceByPack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceComplianceByPack|要执行的操作，取值：**GetResourceComplianceByPack**。 |
|CompliancePackId|String|是|cp-541e626622af0087\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ResourceComplianceResult|Object| |合规包中资源的合规结果。 |
|CompliancePackId|String|cp-541e626622af0087\*\*\*\*|合规包ID。 |
|NonCompliantCount|Integer|7|不合规资源数。 |
|TotalCount|Integer|10|资源总数。 |
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetResourceComplianceByPack
&CompliancePackId=cp-541e626622af0087****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetResourceComplianceByPackResponse>
    <ResourceComplianceResult>
        <CompliancePackId>cp-541e626622af0087****</CompliancePackId>
        <NonCompliantCount>7</NonCompliantCount>
        <TotalCount>10</TotalCount>
    </ResourceComplianceResult>
    <RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
</GetResourceComplianceByPackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ResourceComplianceResult" : {
    "CompliancePackId" : "cp-541e626622af0087****",
    "NonCompliantCount" : 7,
    "TotalCount" : 10
  },
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

