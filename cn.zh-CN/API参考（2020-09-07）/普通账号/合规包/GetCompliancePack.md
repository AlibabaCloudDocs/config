# GetCompliancePack

调用GetCompliancePack接口查询合规包详情。

本文将提供一个示例，查询合规包`cp-fdc8626622af00f9****`的详情。返回结果显示，合规包名称为`等保三级预检合规包`、合规包状态为`ACTIVE`（正常）、合规包中规则的风险等级为`1`（高风险）等。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetCompliancePack&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetCompliancePack|要执行的操作，取值：**GetCompliancePack**。 |
|CompliancePackId|String|是|cp-a8a8626622af0082\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|CompliancePack|Object| |合规包信息。 |
|Status|String|ACTIVE|合规包状态。取值：

 -   ACTIVE：正常。
-   CREATING：创建中。 |
|CompliancePackId|String|cp-a8a8626622af0082\*\*\*\*|合规包ID。 |
|RiskLevel|Integer|1|合规包中规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|Description|String|基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。|合规包描述。 |
|ConfigRules|Array of ConfigRules| |合规包中启用的规则详情。 |
|ManagedRuleIdentifier|String|eip-bandwidth-limit|托管规则标识。 |
|ConfigRuleName|String|弹性IP实例带宽满足最低要求|托管规则名称。 |
|ConfigRuleId|String|cr-a260626622af0005\*\*\*\*|规则ID。 |
|ConfigRuleParameters|Array of ConfigRuleParameters| |规则参数信息。 |
|Required|Boolean|true|规则中参数是否必填。取值：

 -   true
-   false |
|ParameterName|String|bandwidth|规则参数名称。 |
|ParameterValue|String|10|规则参数值。 |
|CompliancePackName|String|等保三级预检合规包|合规包名称。 |
|AccountId|Long|100931896542\*\*\*\*|合规包归属的阿里云账号ID。 |
|CompliancePackTemplateId|String|ct-5f26ff4e06a300c4\*\*\*\*|合规包模板ID。 |
|CreateTimestamp|Long|1624245766000|创建合规包的时间戳。单位：毫秒。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetCompliancePack
&CompliancePackId=cp-a8a8626622af0082****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetCompliancePackResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<CompliancePack>
		<CompliancePackId>cp-a8a8626622af0082****</CompliancePackId>
		<Status>ACTIVE</Status>
		<AccountId>100931896542****</AccountId>
		<CompliancePackName>等保三级预检合规包</CompliancePackName>
		<Description>基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。</Description>
		<ConfigRules>
			<ConfigRuleId>cr-a260626622af0005****</ConfigRuleId>
			<ConfigRuleName>弹性IP实例带宽满足最低要求</ConfigRuleName>
			<ManagedRuleIdentifier>eip-bandwidth-limit</ManagedRuleIdentifier>
			<ConfigRuleParameters>
				<ParameterValue>10</ParameterValue>
				<Required>true</Required>
				<ParameterName>bandwidth</ParameterName>
			</ConfigRuleParameters>
		</ConfigRules>
		<CompliancePackTemplateId>ct-5f26ff4e06a300c4****</CompliancePackTemplateId>
		<RiskLevel>1</RiskLevel>
		<CreateTimestamp>1624245766000</CreateTimestamp>
	</CompliancePack>
</GetCompliancePackResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "CompliancePack" : {
    "CompliancePackId" : "cp-a8a8626622af0082****",
    "Status" : "ACTIVE",
    "AccountId" : "100931896542****",
    "CompliancePackName" : "等保三级预检合规包",
    "Description" : "基于等保2.0三级标准，提供持续检测合规性的建议模板，帮助您提前自检并修复问题，以便快速通过正式检测。",
    "ConfigRules" : [ {
      "ConfigRuleId" : "cr-a260626622af0005****",
      "ConfigRuleName" : "弹性IP实例带宽满足最低要求",
      "ManagedRuleIdentifier" : "eip-bandwidth-limit",
      "ConfigRuleParameters" : [ {
        "ParameterValue" : "10",
        "Required" : true,
        "ParameterName" : "bandwidth"
      } ]
    } ],
    "CompliancePackTemplateId" : "ct-5f26ff4e06a300c4****",
    "RiskLevel" : 1,
    "CreateTimestamp" : 1624245766000
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

