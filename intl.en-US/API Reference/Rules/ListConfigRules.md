# ListConfigRules

Queries rules in Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=ListConfigRules&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListConfigRules|The operation that you want to perform. Set the value to ListConfigRules. |
|PageNumber|Integer|Yes|1|The number of the page to return. Pages start from page 1. |
|PageSize|Integer|Yes|20|The number of entries to return on each page. Valid values: 1 to 100. |
|ConfigRuleState|String|No|ACTIVE|The status of the rule. Valid values:

 -   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resources. Valid values:

 -   COMPLIANT: The resources are evaluated to be compliant.
-   NON\_COMPLIANT: The resources are evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|RiskLevel|Integer|No|1|The risk level of the resources that are not compliant with the rule. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|MessageType|String|No|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|MultiAccount|Boolean|No|true|Specifies whether to query the rules that belong to the member accounts of the current master account. Valid values:

 -   true: Queries the rules that belong to the member accounts in the resource directory of the current master account.
-   false \(default value\): Queries the rules that belong to the current master account.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose rules you want to query. This parameter is unspecified by default. It is available only when MultiAccount is set to true.

 -   If MemberId is unspecified, the system queries the rules that belong to the current master account and its member accounts.
-   When MemberId is specified, the system queries the rules that belong to the specified member account.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConfigRules|Struct| |The information of the queried rules. |
|ConfigRuleList|Array of ConfigRule| |The details of the rule. |
|AccountId|Long|987654321|The ID of the Alibaba Cloud account that owns the rule. |
|AutomationType|String|LC|The type of the remediation template. |
|Compliance|Struct| |The statistics of the compliance evaluation results based on the rule. |
|ComplianceType|String|NON\_COMPLIANT|The compliance evaluation result of the resources. Valid values:

 -   COMPLIANT: The resources are evaluated to be compliant.
-   NON\_COMPLIANT: The resources are evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|Count|Integer|2|The number of resources with the specified compliance evaluation result. |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-7f085180a8d100d4\*\*\*\*|The Alibaba Cloud Resource Name \(ARN\) of the rule. |
|ConfigRuleId|String|cr-7f085180a8d100d4\*\*\*\*|The ID of the rule. |
|ConfigRuleName|String|test123|The name of the rule. |
|ConfigRuleState|String|ACTIVE|The status of the rule. Valid values:

 -   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|CreateBy|Struct| |The information of the created rule. |
|ConfigRuleSceneId|String|level3\_protection|The ID of the scenario in which the rule was created.

 **Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|ConfigRuleSceneName|String|level3\_protection|The name of the scenario in which the rule was created.

 **Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorId|String|level3\_protection|The ID of the account that was used to create the rule.

 **Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorName|String|level3\_protection|The name of the account that was used to create the rule.

 **Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorType|String|CONFIG\_RULE\_SCENE|The type of the rule creator. Valid values:

 -   RESOURCE\_DIRECTORY: indicates a master account. If you are using Cloud Config for Enterprise, you can create rules by using a master account.
-   CONFIG\_RULE\_SCENE: indicates the system. If you are using Cloud Config for individuals, the system automatically creates rules in specific scenarios, such as classified protection precheck, OSS compliance baseline, and CIS compliance check. |
|Description|String|test|The description of the rule. |
|RiskLevel|Integer|1|The risk level of the resources that are not compliant with the rule. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|SourceIdentifier|String|rds-instance-enabled-security-ip-list|The name of the rule.

 -   For a managed rule, the value is the name of the managed rule.
-   For a custom rule, the value is the ARN of the custom rule. |
|SourceOwner|String|ALIYUN|Indicates whether you or Alibaba Cloud owns and manages the rule. Valid values:

 -   CUSTOM\_FC: The rule is a custom rule that you own.
-   ALIYUN: The rule is a managed rule of Alibaba Cloud. |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|10|The number of entries returned on each page. Valid values: 1 to 100. |
|TotalCount|Long|36|The total number of rules. |
|RequestId|String|482DAB02-28AA-42FF-A382-842D9CC22635|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ListConfigRules
&PageNumber=1
&PageSize=20
&<common request parameters>
```

Sample responses

`XML` format

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
			      This rule is evaluated to be compliant if no public IP addresses are bound to ECS instances. This rule is applicable only to IPv4 addresses. </Description>
			      <Compliance>
				        <ComplianceType>NON_COMPLIANT</ComplianceType>
				        <Count>9</Count>
			      </Compliance>
			      <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-1c886457e0d900d3****</ConfigRuleArn>
			      <SourceOwner>ALIYUN</SourceOwner>
			      <SourceIdentifier>ecs-instance-no-public-ip</SourceIdentifier>
			      <CreateBy>
				        <CreatorId>level3_protection</CreatorId>
				        <ConfigRuleSceneName>level3_protection</ConfigRuleSceneName>
				        <ConfigRuleSceneId>level3_protection</ConfigRuleSceneId>
				        <CreatorType>CONFIG_RULE_SCENE</CreatorType>
				        <CreatorName>level3_protection</CreatorName>
			      </CreateBy>
			      <ConfigRuleName>level3_protection-ecs-instance-no-public-ip-d37a71</ConfigRuleName>
			      <RiskLevel>1</RiskLevel>
			      <ConfigRuleState>ACTIVE</ConfigRuleState>
		    </ConfigRuleList>
		    <ConfigRuleList>
			      <ConfigRuleId>cr-3f4c6457e0d90029****</ConfigRuleId>
			      <AccountId>120886317861****</AccountId>
			      <Description>This rule is evaluated to be compliant if all associated resources have specified tags. </Description>
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
			      <Description>This rule is evaluated to be compliant if hotlink protection is enabled for the OSS buckets within your account. </Description>
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

`JSON` format

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
				"Description": "This rule is evaluated to be compliant if no public IP addresses are bound to ECS instances. This rule is applicable only to IPv4 addresses.",
				"Compliance": {
					"ComplianceType": "NON_COMPLIANT",
					"Count": 9
				},
				"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-1c886457e0d900d3****",
				"SourceOwner": "ALIYUN",
				"SourceIdentifier": "ecs-instance-no-public-ip",
				"CreateBy": {
					"CreatorId": "level3_protection",
					"ConfigRuleSceneName": "level3_protection",
					"ConfigRuleSceneId": "level3_protection",
					"CreatorType": "CONFIG_RULE_SCENE",
					"CreatorName": "level3_protection"
				},
				"ConfigRuleName": "level3_protection-ecs-instance-no-public-ip-d37a71",
				"RiskLevel": 1,
				"ConfigRuleState": "ACTIVE"
			},
          {
				"ConfigRuleId": "cr-3f4c6457e0d90029****",
				"AccountId": "120886317861****",
				<Description>This rule is evaluated to be compliant if all associated resources have specified tags.
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
				<Description>This rule is evaluated to be compliant if hotlink protection is enabled for the OSS buckets within your account.
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

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

