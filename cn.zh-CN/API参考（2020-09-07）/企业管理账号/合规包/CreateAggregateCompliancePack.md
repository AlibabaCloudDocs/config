# CreateAggregateCompliancePack

调用CreateAggregateCompliancePack接口为指定账号组创建合规包。

每个企业管理账号在每个账号组中最多创建5个合规包。

本文将提供一个示例，为账号组`ca-f632626622af0079****`创建一个合规包“等保三级预检合规包”，该合规包中有一条托管规则`eip-bandwidth-limit`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=CreateAggregateCompliancePack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAggregateCompliancePack|要执行的操作，取值：**CreateAggregateCompliancePack**。 |
|CompliancePackTemplateId|String|是|ct-5f26ff4e06a300c4\*\*\*\*|合规包模板ID。

 关于如何获取合规包模板ID，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|CompliancePackName|String|是|等保三级预检合规包|合规包名称。 |
|Description|String|是|基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。|合规包描述。 |
|RiskLevel|Integer|是|1|合规包中托管规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|AggregatorId|String|是|ca-f632626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|ConfigRules|Array|是| |合规包中启用的托管规则详情。 |
|ManagedRuleIdentifier|String|是|eip-bandwidth-limit|托管规则标识。

 关于如何获取托管规则标识，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ConfigRuleName|String|否|弹性IP实例带宽满足最低要求|托管规则名称。 |
|ConfigRuleParameters|Array|否| |托管规则参数信息。 |
|ParameterName|String|否|bandwidth|托管规则参数名称。

 关于如何获取托管规则参数名称，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ParameterValue|String|否|10|托管规则参数值。

 关于如何获取托管规则参数值，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|ClientToken|String|否|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CompliancePackId|String|cp-fc56626622af00f9\*\*\*\*|合规包ID。 |
|RequestId|String|CC0CE5EB-E51E-48EB-B4AB-9A9E131ECC0F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateAggregateCompliancePack
&CompliancePackTemplateId=ct-5f26ff4e06a300c4****
&CompliancePackName=等保三级预检合规包
&Description=基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。
&RiskLevel=1
&AggregatorId=ca-f632626622af0079****
&ConfigRules=[{"ManagedRuleIdentifier":"eip-bandwidth-limit","ConfigRuleName":"弹性IP实例带宽满足最低要求","ConfigRuleParameters":[{"ParameterName":"bandwidth","ParameterValue":"10"}]}]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateAggregateCompliancePackResponse>
	<CompliancePackId>cp-fc56626622af00f9****</CompliancePackId>
	<RequestId>CC0CE5EB-E51E-48EB-B4AB-9A9E131ECC0F</RequestId>
</CreateAggregateCompliancePackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "CompliancePackId" : "cp-fc56626622af00f9****",
  "RequestId" : "CC0CE5EB-E51E-48EB-B4AB-9A9E131ECC0F"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|CompliancePackExists|The compliance pack already exists.|合规包名称重复。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|400|CompliancePackExceedMaxCount|The maximum number of compliance pack is exceeded.|合规包不能超过5个。|
|400|Invalid.CompliancePackName.Value|The specified CompliancePackName is invalid.|合规包名称格式不符合要求。|
|400|Invalid.CompliancePackTemplateId.Value|The specified CompliancePackTemplateId does not exist.|合规包模板ID不存在。|
|400|Invalid.ConfigRules.Empty|You must specify ConfigRules.|合规包中规则不能为空。|
|400|Invalid.ConfigRules.Value|The specified ConfigRules is invalid.|合规包规则中参数输入错误。|
|400|ConfigRuleExceedMaxRuleCount|The maximum number of config rules is exceeded.|超过最大的规则创建条数。|
|403|AggregatorMemberNoPermission|The aggregator member is not authorized to perform the operation.|账号组内的成员账号无权限执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

