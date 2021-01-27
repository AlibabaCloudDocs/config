# DescribeEvaluationResults

Queries the compliance evaluation results of resources.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeEvaluationResults&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeEvaluationResults|The operation that you want to perform. Set the value to DescribeEvaluationResults. |
|ResourceType|String|No|ACS::ECS::Instance|The type of the resource. This parameter must be specified if you query the compliance evaluation results of resources by resource type.

 You can call the GetSupportedResourceTypes API operation to query the resource types that are supported by Cloud Config. For more information, see [GetSupportedResourceTypes](~~169618~~).

 **Note:** You only need to specify ResourceType or ConfigRuleId. |
|ResourceId|String|No|i-bp151g9tpto890zr\*\*\*\*|The ID of the resource. This parameter must be specified if you query the compliance evaluation results of resources by resource type. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|PageNumber|Integer|No|1|The page number of the page to return. Pages start from page 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. |
|ConfigRuleId|String|No|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule.

 This parameter must be specified if you query the compliance evaluation results of resources by rule.

 **Note:** You only need to specify ResourceType or ConfigRuleId. |
|MultiAccount|Boolean|No|false|Specifies whether to query the compliance evaluation results of the resources that belong to the member accounts of the current master account. Valid values:

 -   true: Queries the compliance evaluation results of the resources that belong to the member accounts in the resource directory of the current master account.
-   false \(default value\): Queries the compliance evaluation results of the resources that belong to the current master account.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |
|MemberId|Long|No|1234567|The ID of the member account whose resources you want to query. This parameter is unspecified by default. It is available only when MultiAccount is set to true.

 -   If MemberId is unspecified, the system queries the compliance evaluation results of the resources that belong to the current master account and its member accounts.
-   If MemberId is specified, the system queries the compliance evaluation results of the resources that belong to the specified member accounts.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|EvaluationResults|Struct| |The compliance evaluation results of resources. |
|EvaluationResultList|Array of EvaluationResult| |The details of the compliance evaluation result. |
|Annotation|String|\{"operator": "StringEquals", "property": "$.SslProtocol", "desiredValue": "on", "configuration": "\['off'\]"\}|The annotation to the resource that is evaluated to be non-compliant. |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|ConfigRuleInvokedTimestamp|Long|1589941923258|The timestamp that was generated when the rule was triggered. |
|EvaluationResultIdentifier|Struct| |The identifier of the compliance evaluation result. |
|EvaluationResultQualifier|Struct| |The information of the rule and the evaluated resource. |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-2da35180a8d1008e\*\*\*\*|The Alibaba Cloud Resource Name \(ARN\) of the rule. |
|ConfigRuleId|String|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule. |
|ConfigRuleName|String|ecs-instance-deletion-protection-enabled|The name of the rule. |
|RegionId|String|cn-hangzhou|The ID of the region. |
|ResourceId|String|i-bp151g9tpto890zr\*\*\*\*|The ID of the evaluated resource. |
|ResourceType|String|ACS::ECS::Instance|The type of the evaluated resource. |
|OrderingTimestamp|Long|1589941923117|The timestamp that was generated when the compliance evaluation was performed. |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|RemediationEnabled|Boolean|true|Indicates whether the remediation template is enabled. Valid values:

 -   true
-   false |
|ResultRecordedTimestamp|Long|1589941923432|The timestamp that was generated when the compliance evaluation result was recorded. |
|RiskLevel|Integer|1|The risk level of the non-compliant resource. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|10|The number of entries returned on each page. Valid values: 1 to 100. |
|TotalCount|Long|2|The total number of compliance evaluation results. |
|RequestId|String|7A90353C-A64F-4914-A452-68995753F5C2|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeEvaluationResults
&ConfigRuleId=cr-2da35180a8d1008e****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeEvaluationResultsResponse>
	  <RequestId>D296EE41-1143-4B13-83BB-909008100130</RequestId>
	  <EvaluationResults>
		    <EvaluationResultList>
			      <ConfigRuleInvokedTimestamp>1608262263084</ConfigRuleInvokedTimestamp>
			      <ComplianceType>COMPLIANT</ComplianceType>
			      <ResultRecordedTimestamp>1608262263321</ResultRecordedTimestamp>
			      <InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
			      <EvaluationResultIdentifier>
				        <EvaluationResultQualifier>
					          <ConfigRuleId>cr-22726457e0d90078****</ConfigRuleId>
					          <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-22726457e0d90078****</ConfigRuleArn>
					          <ResourceId>i-t4n0piq1mkfo1d27****</ResourceId>
					          <ConfigRuleName>ecs-instance-deletion-protection-enabled</ConfigRuleName>
					          <ResourceType>ACS::ECS::Instance</ResourceType>
					          <RegionId>cn-hangzhou</RegionId>
				        </EvaluationResultQualifier>
				        <OrderingTimestamp>1608262263084</OrderingTimestamp>
			      </EvaluationResultIdentifier>
			      <RiskLevel>3</RiskLevel>
			      <RemediationEnabled>true</RemediationEnabled>
			      <Annotation></Annotation>
		    </EvaluationResultList>
		    <EvaluationResultList>
			      <ConfigRuleInvokedTimestamp>1608262263084</ConfigRuleInvokedTimestamp>
			      <ComplianceType>COMPLIANT</ComplianceType>
			      <ResultRecordedTimestamp>1608262263326</ResultRecordedTimestamp>
			      <InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
			      <EvaluationResultIdentifier>
				        <EvaluationResultQualifier>
					          <ConfigRuleId>cr-22726457e0d90078****</ConfigRuleId>
					          <ConfigRuleArn>acs:config::120886317861****:config-rule/cr-22726457e0d90078****</ConfigRuleArn>
					          <ResourceId>i-2ze5o2beycwbvqnx****</ResourceId>
					          <ConfigRuleName>ecs-instance-deletion-protection-enabled</ConfigRuleName>
					          <ResourceType>ACS::ECS::Instance</ResourceType>
					          <RegionId>cn-hangzhou</RegionId>
				        </EvaluationResultQualifier>
				        <OrderingTimestamp>1608262263084</OrderingTimestamp>
			      </EvaluationResultIdentifier>
			      <RiskLevel>3</RiskLevel>
			      <RemediationEnabled>true</RemediationEnabled>
			      <Annotation></Annotation>
		    </EvaluationResultList>
		    <TotalCount>52</TotalCount>
		    <PageSize>10</PageSize>
		    <PageNumber>1</PageNumber>
	  </EvaluationResults>
</DescribeEvaluationResultsResponse>
```

`JSON` format

```
{
	"RequestId": "D296EE41-1143-4B13-83BB-909008100130",
	"EvaluationResults": {
		"EvaluationResultList": [
			{
				"ConfigRuleInvokedTimestamp": 1608262263084,
				"ComplianceType": "COMPLIANT",
				"ResultRecordedTimestamp": 1608262263321,
				"InvokingEventMessageType": "ConfigurationItemChangeNotification",
				"EvaluationResultIdentifier": {
					"EvaluationResultQualifier": {
						"ConfigRuleId": "cr-22726457e0d90078****",
						"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
						"ResourceId": "i-t4n0piq1mkfo1d27****",
						"ConfigRuleName": "ecs-instance-deletion-protection-enabled",
						"ResourceType": "ACS::ECS::Instance",
						"RegionId": "cn-hangzhou"
					},
					"OrderingTimestamp": 1608262263084
				},
				"RiskLevel": 3,
				"RemediationEnabled": true,
				"Annotation": ""
			},
			{
				"ConfigRuleInvokedTimestamp": 1608262263084,
				"ComplianceType": "COMPLIANT",
				"ResultRecordedTimestamp": 1608262263326,
				"InvokingEventMessageType": "ConfigurationItemChangeNotification",
				"EvaluationResultIdentifier": {
					"EvaluationResultQualifier": {
						"ConfigRuleId": "cr-22726457e0d90078****",
						"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
						"ResourceId": "i-2ze5o2beycwbvqnx****",
						"ConfigRuleName": "ecs-instance-deletion-protection-enabled",
						"ResourceType": "ACS::ECS::Instance",
						"RegionId": "cn-hangzhou"
					},
					"OrderingTimestamp": 1608262263084
				},
				"RiskLevel": 3,
				"RemediationEnabled": true,
				"Annotation": ""
			}
		],
		"TotalCount": 52,
		"PageSize": 10,
		"PageNumber": 1
	}
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|The error message returned because the AliyunServiceRoleForConfig role does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

