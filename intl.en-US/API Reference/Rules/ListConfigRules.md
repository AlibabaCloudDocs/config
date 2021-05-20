# ListConfigRules

Queries rules in Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=ListConfigRules&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListConfigRules|The operation that you want to perform. Set the value to **ListConfigRules**. |
|ConfigRuleState|String|No|ACTIVE|The status of the rule. Valid values:

 -   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resources. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|RiskLevel|Integer|No|1|The risk level of the resources that are not compliant with the rule. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|MessageType|String|No|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|PageNumber|Integer|Yes|1|The number of the page to return. Pages start from page 1. |
|PageSize|Integer|Yes|20|The number of entries to return on each page. Valid values: 1 to 100. |
|MultiAccount|Boolean|No|true|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|ConfigRuleName|String|No|OSS compliance management - The ACL policy of the OSS bucket prohibits public read access|The name of the rule. |
|CompliancePackId|String|No|cp-8d5c6457e0d9002a\*\*\*\*|The ID of the compliance package to which the rule belongs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|8195B664-9565-4685-89AC-8B5F04B44B92|The ID of the request. |
|ConfigRules|Object| |The details of the rule. |
|ConfigRuleList|Array of ConfigRule| |The details of the rule. |
|CompliancePackId|String|cp-8d5c6457e0d9002a\*\*\*\*|The ID of the compliance package to which the rule belongs. |
|RiskLevel|Integer|1|The risk level of the resources that are not compliant with the rule. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|SourceOwner|String|ALIYUN|Indicates whether you or Alibaba Cloud owns and manages the rule. Valid values:

 -   CUSTOM\_FC: The rule is a custom rule that you own.
-   ALIYUN: The rule is a managed rule of Alibaba Cloud. |
|AccountId|Long|987654321|The ID of the Alibaba Cloud account that owns the rule. |
|ConfigRuleState|String|ACTIVE|The status of the rule. Valid values:

 -   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|Compliance|Object| |The statistics of the compliance evaluation results based on the rule. |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the resources. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|Count|Integer|161|The number of resources with the specified compliance evaluation result. |
|SourceIdentifier|String|oss-bucket-public-read-prohibited|The identifier of the rule.

 -   For a managed rule, the value is the name of the managed rule.
-   For a custom rule, the value is the Alibaba Cloud Resource Name \(ARN\) of the custom rule. |
|ConfigRuleArn|String|acs:config::120886317861\*\*\*\*:rule/cr-8d5c6457e0d9002a\*\*\*\*|The ARN of the rule. |
|Description|String|This rule is evaluated to be compliant if the ACL policy of OSS buckets prohibits public read access.|The description of the rule. |
|CreateBy|Object| |The information of the created rule. |
|CompliancePackId|String|cp-8d5c6457e0d9002a\*\*\*\*|The ID of the compliance package. |
|CompliancePackName|String|OSS compliance management|The name of the compliance package. |
|AutomationType|String|LC|The type of the remediation template. Set the value to LC.

 **Note:** LC represents Logic Composer. |
|ConfigRuleName|String|OSS compliance management - The ACL policy of the OSS bucket prohibits public read access|The name of the rule. |
|ConfigRuleId|String|cr-8d5c6457e0d9002a\*\*\*\*|The IDs of the rules. |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|20|The number of entries returned on each page. Valid values: 1 to 100. |
|TotalCount|Long|1|The total number of rules. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ListConfigRules
&PageNumber=1
&PageSize=20
&<Common request parameters>
```

Sample success responses

`XML` format

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
			<Description> The ACL policy of the OSS bucket prohibits public read access and is considered "compliant". </Description>
			<Compliance>
				<ComplianceType>COMPLIANT</ComplianceType>
				<Count>161</Count>
			</Compliance>
			<ConfigRuleArn>acs:config::120886317861****:rule/cr-8d5c6457e0d9002a****</ConfigRuleArn>
			<SourceOwner>ALIYUN</SourceOwner>
			<SourceIdentifier>oss-bucket-public-read-prohibited</SourceIdentifier>
			<CreateBy>
				<CompliancePackId>cp-8d5c6457e0d9002a628b</CompliancePackId>
				<CompliancePackName>OSS compliance management</CompliancePackName>
				<CreatorId>1208863178612953</CreatorId>
			</CreateBy>
			<ConfigRuleName>OSS compliance management - The ACL policy of the OSS bucket prohibits public read access</ConfigRuleName>
			<RiskLevel>1</RiskLevel>
			<ConfigRuleState>ACTIVE</ConfigRuleState>
		</ConfigRuleList>
	</ConfigRules>
</ListConfigRulesResponse>
```

`JSON` format

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
      "Description": "This rule is evaluated to be compliant if the ACL policy of OSS buckets prohibits public read access.",
      "Compliance" : {
        "ComplianceType" : "COMPLIANT",
        "Count" : 161
      },
      "ConfigRuleArn" : "acs:config::120886317861****:rule/cr-8d5c6457e0d9002a****",
      "SourceOwner" : "ALIYUN",
      "SourceIdentifier" : "oss-bucket-public-read-prohibited",
      "CreateBy" : {
        "CompliancePackId" : "cp-8d5c6457e0d9002a628b",
        "CompliancePackName": "OSS compliance management",
        "CreatorId" : "1208863178612953"
      },
      "ConfigRuleName": "OSS compliance management - The ACL policy of the OSS bucket prohibits public read access ",
      "RiskLevel" : 1,
      "ConfigRuleState" : "ACTIVE"
    } ]
  }
}
```

## Error codes

|HttpCode|Error codes|Error message|Description|
|--------|-----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

