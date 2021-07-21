# ListAggregateConfigRules

调用ListAggregateConfigRules接口查询指定账号组内的规则列表。

本文将提供一个示例，查询账号组`ca-f632626622af0079****`内的规则列表。返回结果显示，规则列表中规则总数为1条，评估资源数为2条，评估结果为`COMPLIANT`（合规）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListAggregateConfigRules&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAggregateConfigRules|要执行的操作，取值：**ListAggregateConfigRules**。 |
|ConfigRuleState|String|否|ACTIVE|规则运行状态。取值：

 -   ACTIVE：应用中。
-   DELETING：删除中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|ComplianceType|String|否|COMPLIANT|规则合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|RiskLevel|Integer|否|1|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ConfigRuleName|String|否|弹性IP实例带宽满足最低要求|规则名称。 |
|AggregatorId|String|是|ca-f632626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|PageSize|Integer|否|10|分页时每页显示的数据行数。

 取值范围：1~100。起始值：1。默认值：10。 |
|PageNumber|Integer|否|1|页码。

 起始值：1。默认值：1。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|22EF8287-2C9A-4F1F-80A6-CEFA7612689D|请求ID。 |
|ConfigRules|Object| |规则列表。 |
|ConfigRuleList|Array of ConfigRule| |规则列表详细信息。 |
|RiskLevel|Integer|1|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|SourceOwner|String|ALIYUN|规则来源的归属。取值：

 -   CUSTOM\_FC：自定义规则。
-   ALIYUN：托管规则。 |
|AccountId|Long|100931896542\*\*\*\*|规则归属的企业管理账号ID。 |
|ConfigRuleState|String|ACTIVE|规则运行状态。取值：

 -   ACTIVE：应用中。
-   DELETING：删除中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|Compliance|Object| |合规包。 |
|ComplianceType|String|COMPLIANT|规则合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|Count|Integer|2|规则评估的资源数。 |
|SourceIdentifier|String|eip-bandwidth-limit|规则标识符。

 -   如果是托管规则，该参数为托管规则标识。
-   如果是自定义规则，该参数为函数ARN。 |
|ConfigRuleArn|String|acs:config::100931896542\*\*\*\*:rule/cr-fdc8626622af00f9\*\*\*\*|规则ARN。 |
|Description|String|弹性IP实例可用带宽大于等于指定参数值，视为“合规”。默认值：10 MB。|规则描述。 |
|CreateBy|Object| |创建规则的信息。 |
|CompliancePackId|String|cp-fdc8626622af00f9\*\*\*\*|合规包ID。 |
|AggregatorName|String|Test\_Group|账号组名称。 |
|CompliancePackName|String|等保三级预检合规包|合规包名称。 |
|CreatorName|String|Alice|创建规则的企业管理账号名称。 |
|CreatorType|String|AGGREGATOR|创建规则的类型。仅支持AGGREGATOR（账号组）。 |
|CreatorId|String|100931896542\*\*\*\*|创建规则的企业管理账号ID。 |
|AggregatorId|String|ca-f632626622af0079\*\*\*\*|账号组D。 |
|AutomationType|String|OOS|修正类型。仅支持OOS（运维编排）。 |
|ConfigRuleName|String|弹性IP实例带宽满足最低要求|规则名称。 |
|ConfigRuleId|String|cr-fdc8626622af00f9\*\*\*\*|规则ID。 |
|PageSize|Integer|10|分页时每页显示的数据行数。 |
|PageNumber|Integer|1|页码。 |
|TotalCount|Long|1|规则总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAggregateConfigRules
&AggregatorId=ca-f632626622af0079****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAggregateConfigRulesResponse>
	<RequestId>22EF8287-2C9A-4F1F-80A6-CEFA7612689D</RequestId>
	<ConfigRules>
		<TotalCount>1</TotalCount>
		<PageSize>10</PageSize>
		<PageNumber>1</PageNumber>
		<ConfigRuleList>
			<ConfigRuleId>cr-fdc8626622af00f9****</ConfigRuleId>
			<AccountId>100931896542****</AccountId>
			<Description>弹性IP实例可用带宽大于等于指定参数值，视为“合规”。默认值：10 MB。</Description>
			<Compliance>
				<ComplianceType>COMPLIANT</ComplianceType>
				<Count>2</Count>
			</Compliance>
			<ConfigRuleArn>acs:config::100931896542****:rule/cr-fdc8626622af00f9****</ConfigRuleArn>
			<SourceOwner>ALIYUN</SourceOwner>
			<SourceIdentifier>eip-bandwidth-limit</SourceIdentifier>
			<CreateBy>
				<CompliancePackId>cp-fdc8626622af00f9****</CompliancePackId>
				<AggregatorName>Test_Group</AggregatorName>
				<CompliancePackName>等保三级预检合规包</CompliancePackName>
				<CreatorId>100931896542****</CreatorId>
				<CreatorType>AGGREGATOR</CreatorType>
				<CreatorName>Alice</CreatorName>
				<AggregatorId>ca-f632626622af0079****</AggregatorId>
			</CreateBy>
			<ConfigRuleName>弹性IP实例带宽满足最低要求</ConfigRuleName>
			<RiskLevel>1</RiskLevel>
			<ConfigRuleState>ACTIVE</ConfigRuleState>
		</ConfigRuleList>
	</ConfigRules>
</ListAggregateConfigRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "22EF8287-2C9A-4F1F-80A6-CEFA7612689D",
  "ConfigRules" : {
    "TotalCount" : 1,
    "PageSize" : 10,
    "PageNumber" : 1,
    "ConfigRuleList" : [ {
      "ConfigRuleId" : "cr-fdc8626622af00f9****",
      "AccountId" : "100931896542****",
      "Description" : "弹性IP实例可用带宽大于等于指定参数值，视为“合规”。默认值：10 MB。",
      "Compliance" : {
        "ComplianceType" : "COMPLIANT",
        "Count" : 2
      },
      "ConfigRuleArn" : "acs:config::100931896542****:rule/cr-fdc8626622af00f9****",
      "SourceOwner" : "ALIYUN",
      "SourceIdentifier" : "eip-bandwidth-limit",
      "CreateBy" : {
        "CompliancePackId" : "cp-fdc8626622af00f9****",
        "AggregatorName" : "Test_Group",
        "CompliancePackName" : "等保三级预检合规包",
        "CreatorId" : "100931896542****",
        "CreatorType" : "AGGREGATOR",
        "CreatorName" : "Alice",
        "AggregatorId" : "ca-f632626622af0079****"
      },
      "ConfigRuleName" : "弹性IP实例带宽满足最低要求",
      "RiskLevel" : 1,
      "ConfigRuleState" : "ACTIVE"
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

