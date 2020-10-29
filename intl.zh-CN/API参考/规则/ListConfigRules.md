# ListConfigRules

调用ListConfigRules接口查询规则列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListConfigRules&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListConfigRules|要执行的操作，取值：ListConfigRules。 |
|PageNumber|Integer|是|1|规则列表的页码。起始值：1。 |
|PageSize|Integer|是|20|分页查询时设置的每页行数。取值范围：1~100。 |
|ConfigRuleState|String|否|ACTIVE|规则的状态。取值：

 -   ACTIVE：应用中
-   EVALUATING：评估中
-   INACTIVE：已停用 |
|ComplianceType|String|否|COMPLIANT|规则的合规类型。取值：

 -   COMPLIANT：合规
-   NON\_COMPLIANT：不合规
-   NOT\_APPLICABLE：不适用
-   INSUFFICIENT\_DATA：数据不充分 |
|RiskLevel|Integer|否|1|规则的风险等级。取值：

 -   1：高风险
-   2：中风险
-   3：低风险 |
|MessageType|String|否|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更
-   ScheduledNotification：周期执行 |
|MultiAccount|Boolean|否|true|企业管理账号是否查询成员账号的规则列表。取值：

 -   true：是。企业管理账号查询资源目录中指定成员账号的规则列表。
-   false（默认值）：否。企业管理账号查询当前账号的规则列表。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |
|MemberId|Long|否|123456789|待查询规则归属的成员账号ID。默认为空。当MultiAccount设置为true时，该参数有效。

 -   当MemberId为空时，查询企业管理账号和所有成员账号的规则列表。
-   当MemberId不为空时，查询指定成员账号的规则列表。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConfigRules|Struct| |规则列表。 |
|ConfigRuleList|Array of ConfigRule| |规则列表。 |
|AccountId|Long|987654321|该规则归属的阿里云账号ID。 |
|AutomationType|String|LC|修正模板类型。 |
|Compliance|Struct| |规则合规情况统计。 |
|ComplianceType|String|NON\_COMPLIANT|规则合规类型。取值：

 -   COMPLIANT：合规
-   NON\_COMPLIANT：不合规
-   NOT\_APPLICABLE：不适用
-   INSUFFICIENT\_DATA：数据不充分 |
|Count|Integer|2|该规则符合指定合规类型的资源数统计。 |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-7f085180a8d100d4\*\*\*\*|规则ARN。 |
|ConfigRuleId|String|cr-7f085180a8d100d4\*\*\*\*|规则ID。 |
|ConfigRuleName|String|test123|规则名称。 |
|ConfigRuleState|String|ACTIVE|当前规则运行状态。取值：

 -   ACTIVE：应用中
-   EVALUATING：评估中
-   INACTIVE：已停用 |
|CreateBy|Struct| |规则的创建信息。 |
|ConfigRuleSceneId|String|level3\_protection|创建规则的场景ID。

 **说明：** 当CreatorType为CONFIG\_RULE\_SCENE时，该参数不为空。 |
|ConfigRuleSceneName|String|等保预检|创建规则的场景名称。

 **说明：** 当CreatorType为CONFIG\_RULE\_SCENE时，该参数不为空。 |
|CreatorId|String|level3\_protection|创建者ID。

 **说明：** 当CreatorType为CONFIG\_RULE\_SCENE时，该参数不为空。 |
|CreatorName|String|等保预检|创建者名称。

 **说明：** 当CreatorType为CONFIG\_RULE\_SCENE时，该参数不为空。 |
|CreatorType|String|CONFIG\_RULE\_SCENE|创建者类型。取值：

 -   RESOURCE\_DIRECTORY：当您使用企业版配置审计时，由企业管理账号创建规则。
-   CONFIG\_RULE\_SCENE：当您使用个人版配置审计时，系统自动创建某些应用场景，例如：等保预检、OSS合规基线、CIS合规检测。 |
|Description|String|test|规则的描述信息。 |
|RiskLevel|Integer|1|规则的风险等级。取值：

 -   1：高风险
-   2：中风险
-   3：低风险 |
|SourceIdentifier|String|rds-instance-enabled-security-ip-list|规则名称。

 -   如果规则使用了托管规则，则该参数为托管规则名称。
-   如果规则使用了自定义函数，则该参数为函数ARN。 |
|SourceOwner|String|ALIYUN|规则来源的归属。取值：

 -   CUSTOM\_FC：用户自定义函数
-   ALIYUN：托管规则 |
|PageNumber|Integer|1|规则列表的页码。起始值：1。 |
|PageSize|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Long|36|规则总数。 |
|RequestId|String|482DAB02-28AA-42FF-A382-842D9CC22635|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListConfigRules
&PageNumber=1
&PageSize=20
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListConfigRulesResponse>
	  <RequestId>05E055F1-79BE-4025-A53E-207A00E5AF6C</RequestId>
	  <ConfigRules>
		    <TotalCount>53</TotalCount>
		    <PageSize>20</PageSize>
		    <PageNumber>1</PageNumber>
		    <ConfigRuleList>
			      <ConfigRuleId>cr-1c886457e0d900d3****</ConfigRuleId>
			      <AccountId>120886317861****</AccountId>
			      <Description>ECS实例未直接绑定公网IP，视为“合规”。该规则仅适用于 IPv4 协议。</Description>
			      <Compliance>
				        <ComplianceType>NON_COMPLIANT</ComplianceType>
				        <Count>9</Count>
			      </Compliance>
			      <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-1c886457e0d900d3****</ConfigRuleArn>
			      <SourceOwner>ALIYUN</SourceOwner>
			      <SourceIdentifier>ecs-instance-no-public-ip</SourceIdentifier>
			      <CreateBy>
				        <CreatorId>level3_protection</CreatorId>
				        <ConfigRuleSceneName>等保预检</ConfigRuleSceneName>
				        <ConfigRuleSceneId>level3_protection</ConfigRuleSceneId>
				        <CreatorType>CONFIG_RULE_SCENE</CreatorType>
				        <CreatorName>等保预检</CreatorName>
			      </CreateBy>
			      <ConfigRuleName>level3_protection-ecs-instance-no-public-ip-d37a71</ConfigRuleName>
			      <RiskLevel>1</RiskLevel>
			      <ConfigRuleState>ACTIVE</ConfigRuleState>
		    </ConfigRuleList>
		    <ConfigRuleList>
			      <ConfigRuleId>cr-3f4c6457e0d90029****</ConfigRuleId>
			      <AccountId>120886317861****</AccountId>
			      <Description>关联的资源类型下实体资源均已有指定标签，视为“合规”。</Description>
			      <Compliance>
				        <ComplianceType>NON_COMPLIANT</ComplianceType>
				        <Count>306</Count>
			      </Compliance>
			      <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-3f4c6457e0d90029****</ConfigRuleArn>
			      <SourceOwner>ALIYUN</SourceOwner>
			      <SourceIdentifier>required-tags</SourceIdentifier>
			      <CreateBy></CreateBy>
			      <ConfigRuleName>required-tags</ConfigRuleName>
			      <RiskLevel>1</RiskLevel>
			      <ConfigRuleState>ACTIVE</ConfigRuleState>
		    </ConfigRuleList>
		    <ConfigRuleList>
			      <ConfigRuleId>cr-eab56457e0d9005a***</ConfigRuleId>
			      <AccountId>120886317861****</AccountId>
			      <Description>检测您账号下OSS存储桶是否开启防盗链开关，已开通视为“合规”。</Description>
			      <Compliance>
				        <ComplianceType>NON_COMPLIANT</ComplianceType>
				        <Count>94</Count>
			      </Compliance>
			      <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-eab56457e0d9005a****</ConfigRuleArn>
			      <AutomationType>OOS</AutomationType>
			      <SourceOwner>ALIYUN</SourceOwner>
			      <SourceIdentifier>oss-bucket-referer-limit</SourceIdentifier>
			      <CreateBy></CreateBy>
			      <ConfigRuleName>oss-bucket-referer-limit-test123</ConfigRuleName>
			      <RiskLevel>1</RiskLevel>
			      <ConfigRuleState>ACTIVE</ConfigRuleState>
		    </ConfigRuleList>
	  </ConfigRules>
</ListConfigRulesResponse>
```

`JSON` 格式

```
{
	"RequestId": "05E055F1-79BE-4025-A53E-207A00E5AF6C",
	"ConfigRules": {
		"TotalCount": 53,
		"PageSize": 20,
		"PageNumber": 1,
		"ConfigRuleList": [
			{
				"ConfigRuleId": "cr-1c886457e0d900d3****",
				"AccountId": "120886317861****",
				"Description": "ECS实例未直接绑定公网IP，视为“合规”。该规则仅适用于 IPv4 协议。",
				"Compliance": {
					"ComplianceType": "NON_COMPLIANT",
					"Count": 9
				},
				"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-1c886457e0d900d3****",
				"SourceOwner": "ALIYUN",
				"SourceIdentifier": "ecs-instance-no-public-ip",
				"CreateBy": {
					"CreatorId": "level3_protection",
					"ConfigRuleSceneName": "等保预检",
					"ConfigRuleSceneId": "level3_protection",
					"CreatorType": "CONFIG_RULE_SCENE",
					"CreatorName": "等保预检"
				},
				"ConfigRuleName": "level3_protection-ecs-instance-no-public-ip-d37a71",
				"RiskLevel": 1,
				"ConfigRuleState": "ACTIVE"
			},
          {
				"ConfigRuleId": "cr-3f4c6457e0d90029****",
				"AccountId": "120886317861****",
				"Description": "关联的资源类型下实体资源均已有指定标签，视为“合规”。",
				"Compliance": {
					"ComplianceType": "NON_COMPLIANT",
					"Count": 306
				},
				"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-3f4c6457e0d90029****",
				"SourceOwner": "ALIYUN",
				"SourceIdentifier": "required-tags",
				"CreateBy": {},
				"ConfigRuleName": "required-tags",
				"RiskLevel": 1,
				"ConfigRuleState": "ACTIVE"
			},
			{
				"ConfigRuleId": "cr-eab56457e0d9005a***",
				"AccountId": "120886317861****",
				"Description": "检测您账号下OSS存储桶是否开启防盗链开关，已开通视为“合规”。",
				"Compliance": {
					"ComplianceType": "NON_COMPLIANT",
					"Count": 94
				},
				"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-eab56457e0d9005a****",
				"AutomationType": "OOS",
				"SourceOwner": "ALIYUN",
				"SourceIdentifier": "oss-bucket-referer-limit",
				"CreateBy": {},
				"ConfigRuleName": "oss-bucket-referer-limit-test123",
				"RiskLevel": 1,
				"ConfigRuleState": "ACTIVE"
			}
		]
	}
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

