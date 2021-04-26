# ListConfigRules

调用ListConfigRules接口查询规则列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListConfigRules&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListConfigRules|要执行的操作，取值：**ListConfigRules**。 |
|ConfigRuleState|String|否|ACTIVE|规则的状态。取值：

 -   ACTIVE：应用中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|ComplianceType|String|否|COMPLIANT|规则的合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|RiskLevel|Integer|否|1|规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|MessageType|String|否|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|PageNumber|Integer|是|1|规则列表的页码。起始值：1。 |
|PageSize|Integer|是|20|分页查询时设置的每页行数。取值范围：1~100。 |
|MultiAccount|Boolean|否|true|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|ConfigRuleName|String|否|OSS合规管理最佳实践-OSS存储空间ACL禁止公共读访问|规则的名称。 |
|CompliancePackId|String|否|cp-8d5c6457e0d9002a\*\*\*\*|规则所属的合规包ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8195B664-9565-4685-89AC-8B5F04B44B92|请求ID。 |
|ConfigRules|Object| |规则列表。 |
|ConfigRuleList|Array of ConfigRule| |规则列表。 |
|CompliancePackId|String|cp-8d5c6457e0d9002a\*\*\*\*|规则所属的合规包ID。 |
|RiskLevel|Integer|1|规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|SourceOwner|String|ALIYUN|规则来源的归属。取值：

 -   CUSTOM\_FC：用户自定义函数。
-   ALIYUN：托管规则。 |
|AccountId|Long|987654321|该规则归属的阿里云账号ID。 |
|ConfigRuleState|String|ACTIVE|当前规则运行状态。取值：

 -   ACTIVE：应用中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|Compliance|Object| |规则合规情况统计。 |
|ComplianceType|String|COMPLIANT|规则合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|Count|Integer|161|该规则符合指定合规类型的资源数统计。 |
|SourceIdentifier|String|oss-bucket-public-read-prohibited|规则标识。

 -   如果规则使用了托管规则，则该参数为托管规则名称。
-   如果规则使用了自定义函数，则该参数为函数ARN。 |
|ConfigRuleArn|String|acs:config::120886317861\*\*\*\*:rule/cr-8d5c6457e0d9002a\*\*\*\*|规则ARN。 |
|Description|String|OSS存储空间的ACL策略禁止公共读访问，视为“合规”。|规则的描述信息。 |
|CreateBy|Object| |规则的创建信息。 |
|CompliancePackId|String|cp-8d5c6457e0d9002a\*\*\*\*|合规包ID。 |
|CompliancePackName|String|OSS合规管理最佳实践|合规包名称。 |
|AutomationType|String|LC|修正模板类型。取值：LC。

 **说明：** LC：逻辑编排（Logic Composer）。 |
|ConfigRuleName|String|OSS合规管理最佳实践-OSS存储空间ACL禁止公共读访问|规则名称。 |
|ConfigRuleId|String|cr-8d5c6457e0d9002a\*\*\*\*|规则ID。 |
|PageNumber|Integer|1|规则列表的页码。起始值：1。 |
|PageSize|Integer|20|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Long|1|规则总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListConfigRules
&PageNumber=1
&PageSize=20
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListConfigRulesResponse>
	<RequestId>8195B664-9565-4685-89AC-8B5F04B44B92</RequestId>
	<ConfigRules>
		<TotalCount>1</TotalCount>
		<PageSize>20</PageSize>
		<PageNumber>1</PageNumber>
		<ConfigRuleList>
			<CompliancePackId>cp-8d5c6457e0d9002a****</CompliancePackId>
			<ConfigRuleId>cr-8d5c6457e0d9002a****</ConfigRuleId>
			<AccountId>987654321</AccountId>
			<Description>OSS存储空间的ACL策略禁止公共读访问，视为“合规”。</Description>
			<Compliance>
				<ComplianceType>COMPLIANT</ComplianceType>
				<Count>161</Count>
			</Compliance>
			<ConfigRuleArn>acs:config::120886317861****:rule/cr-8d5c6457e0d9002a****</ConfigRuleArn>
			<SourceOwner>ALIYUN</SourceOwner>
			<SourceIdentifier>oss-bucket-public-read-prohibited</SourceIdentifier>
			<CreateBy>
				<CompliancePackId>cp-8d5c6457e0d9002a628b</CompliancePackId>
				<CompliancePackName>OSS合规管理最佳实践</CompliancePackName>
				<CreatorId>1208863178612953</CreatorId>
			</CreateBy>
			<ConfigRuleName>OSS合规管理最佳实践-OSS存储空间ACL禁止公共读访问</ConfigRuleName>
			<RiskLevel>1</RiskLevel>
			<ConfigRuleState>ACTIVE</ConfigRuleState>
		</ConfigRuleList>
	</ConfigRules>
</ListConfigRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "8195B664-9565-4685-89AC-8B5F04B44B92",
  "ConfigRules" : {
    "TotalCount" : 1,
    "PageSize" : 20,
    "PageNumber" : 1,
    "ConfigRuleList" : [ {
      "CompliancePackId" : "cp-8d5c6457e0d9002a****",
      "ConfigRuleId" : "cr-8d5c6457e0d9002a****",
      "AccountId" : "987654321",
      "Description" : "OSS存储空间的ACL策略禁止公共读访问，视为“合规”。",
      "Compliance" : {
        "ComplianceType" : "COMPLIANT",
        "Count" : 161
      },
      "ConfigRuleArn" : "acs:config::120886317861****:rule/cr-8d5c6457e0d9002a****",
      "SourceOwner" : "ALIYUN",
      "SourceIdentifier" : "oss-bucket-public-read-prohibited",
      "CreateBy" : {
        "CompliancePackId" : "cp-8d5c6457e0d9002a628b",
        "CompliancePackName" : "OSS合规管理最佳实践",
        "CreatorId" : "1208863178612953"
      },
      "ConfigRuleName" : "OSS合规管理最佳实践-OSS存储空间ACL禁止公共读访问",
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
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

