# UpdateCompliancePack

调用UpdateCompliancePack接口修改合规包信息。

本文将提供一个示例，将合规包`cp-a8a8626622af0082****`中托管规则`eip-bandwidth-limit`的参数值修改为`20`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=UpdateCompliancePack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateCompliancePack|要执行的操作，取值：**UpdateCompliancePack**。 |
|CompliancePackId|String|是|cp-a8a8626622af0082\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |
|Description|String|否|基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。|合规包描述。

 关于如何获取合规包描述，请参见[ListCompliancePacks](~~263332~~)。 |
|RiskLevel|Integer|否|1|合规包中托管规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ConfigRules|Array|否| |合规包中启用的托管规则详情。 |
|ManagedRuleIdentifier|String|否|eip-bandwidth-limit|托管规则标识。

 关于如何获取托管规则标识，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ConfigRuleParameters|Array|否| |托管规则参数信息。 |
|ParameterName|String|否|bandwidth|托管规则参数名称。

 关于如何获取托管规则参数名称，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ParameterValue|String|否|20|托管规则参数值。

 关于如何获取托管规则参数值，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ClientToken|String|否|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CompliancePackId|String|cp-a8a8626622af0082\*\*\*\*|合规包ID。 |
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateCompliancePack
&CompliancePackId=cp-a8a8626622af0082****
&ConfigRules=[{"ManagedRuleIdentifier":"eip-bandwidth-limit","ConfigRuleParameters":[{"ParameterName":"bandwidth","ParameterValue":"20"}]}]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateCompliancePackResponse>
    <CompliancePackId>cp-a8a8626622af0082****</CompliancePackId>
    <RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
</UpdateCompliancePackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "CompliancePackId" : "cp-a8a8626622af0082****",
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|400|CompliancePackExceedMaxCount|The maximum number of compliance pack is exceeded.|合规包不能超过5个。|
|400|Invalid.ConfigRules.Empty|You must specify ConfigRules.|合规包中规则不能为空。|
|400|Invalid.ConfigRules.Value|The specified ConfigRules is invalid.|合规包规则中参数输入错误。|
|400|ConfigRuleExceedMaxRuleCount|The maximum number of config rules is exceeded.|超过最大的规则创建条数。|
|400|CompliancePackAlreadyPending|The compliance pack has a pending operation and cannot be updated.|如果合规包状态非“正常”，不能被更新。|
|400|CompliancePackExists|The compliance pack already exists.|合规包名称重复。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

