# DescribeEvaluationResults

Queries the compliance evaluation results of resources.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeEvaluationResults&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeEvaluationResults|The operation that you want to perform. Set the value to **DescribeEvaluationResults**. |
|ResourceType|String|No|ACS::ECS::Instance|The type of the resource. If you query the compliance evaluation results of resources by resource type, you must specify this parameter.

 You can call the GetSupportedResourceTypes operation to query the resource types supported by Cloud Config. For more information, see [GetSupportedResourceTypes](~~169618~~).

 **Note:** You must specify the ResourceType or ConfigRuleId parameter. |
|ResourceId|String|No|i-bp151g9tpto890zr\*\*\*\*|The ID of the resource. If you query the compliance evaluation results of resources by resource type, you must specify this parameter. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|PageNumber|Integer|No|1|The number of the page to return. Pages start from page 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. |
|ConfigRuleId|String|No|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule. If you query the compliance evaluation results of resources by rule, you must specify this parameter.

 **Note:** You must specify the ResourceType or ConfigRuleId parameter. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|D296EE41-1143-4B13-83BB-909008100130|The ID of the request. |
|EvaluationResults|Object| |The compliance evaluation results of resources. |
|EvaluationResultList|Array of EvaluationResult| |The details of the compliance evaluation result. |
|RiskLevel|Integer|1|The risk level of the non-compliant resource. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|ResultRecordedTimestamp|Long|1589941923432|The timestamp that was generated when the compliance evaluation result was recorded. |
|Annotation|String|\{"operator": "StringEquals", "property": "$.SslProtocol", "desiredValue": "on", "configuration": "\['off'\]"\}|The annotation to the resource that is evaluated to be non-compliant. |
|ConfigRuleInvokedTimestamp|Long|1589941923258|The timestamp that was generated when the rule was triggered. |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|EvaluationResultIdentifier|Object| |The identifier of the compliance evaluation result. |
|OrderingTimestamp|Long|1589941923117|The timestamp that was generated when the compliance evaluation was performed. |
|EvaluationResultQualifier|Object| |The information of the rule and the evaluated resource. |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-2da35180a8d1008e\*\*\*\*|The Alibaba Cloud Resource Name \(ARN\) of the rule. |
|ResourceType|String|ACS::ECS::Instance|The type of the evaluated resource. |
|ConfigRuleName|String|Enable release protection for ECS instances|The name of the rule. |
|ResourceId|String|i-bp151g9tpto890zr\*\*\*\*|The ID of the evaluated resource. |
|ConfigRuleId|String|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule. |
|ResourceName|String|launch-advisor-20200330|The type of the evaluated resource. |
|RegionId|String|cn-hangzhou|The ID of the region. |
|RemediationEnabled|Boolean|false|Specifies whether to enable the remediation template. Valid values:

 -   true
-   false |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|10|The number of entries returned on each page. Valid values: 1 to 100. |
|TotalCount|Long|2|The total number of compliance evaluation results. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeEvaluationResults
&ConfigRuleId=cr-2da35180a8d1008e****
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

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
					<ConfigRuleName>Enable release protection for ECS instances</ConfigRuleName>
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
					<ConfigRuleName>Enable release protection for ECS instances</ConfigRuleName>
					<ResourceType>ACS::ECS::Instance</ResourceType>
					<RegionId>cn-hangzhou</RegionId>
				</EvaluationResultQualifier>
				<OrderingTimestamp>1608262263084</OrderingTimestamp>
			</EvaluationResultIdentifier>
			<RiskLevel>3</RiskLevel>
			<RemediationEnabled>false</RemediationEnabled>
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
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "D296EE41-1143-4B13-83BB-909008100130",
  "EvaluationResults" : {
    "EvaluationResultList" : [ {
      "ConfigRuleInvokedTimestamp" : 1608262263084,
      "ComplianceType" : "COMPLIANT",
      "ResultRecordedTimestamp" : 1608262263321,
      "InvokingEventMessageType" : "ConfigurationItemChangeNotification",
      "EvaluationResultIdentifier" : {
        "EvaluationResultQualifier" : {
          "ConfigRuleId" : "cr-22726457e0d90078****",
          "ConfigRuleArn" : "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
          "ResourceId" : "i-t4n0piq1mkfo1d27****",
          "ConfigRuleName": "Enable release protection for ECS instances",
          "ResourceType" : "ACS::ECS::Instance",
          "RegionId" : "cn-hangzhou"
        },
        "OrderingTimestamp" : 1608262263084
      },
      "RiskLevel" : 3,
      "RemediationEnabled" : true,
      "Annotation" : ""
    }, {
      "ConfigRuleInvokedTimestamp" : 1608262263084,
      "ComplianceType" : "COMPLIANT",
      "ResultRecordedTimestamp" : 1608262263326,
      "InvokingEventMessageType" : "ConfigurationItemChangeNotification",
      "EvaluationResultIdentifier" : {
        "EvaluationResultQualifier" : {
          "ConfigRuleId" : "cr-22726457e0d90078****",
          "ConfigRuleArn" : "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
          "ResourceId" : "i-2ze5o2beycwbvqnx****",
          "ConfigRuleName": "Enable release protection for ECS instances",
          "ResourceType" : "ACS::ECS::Instance",
          "RegionId" : "cn-hangzhou"
        },
        "OrderingTimestamp" : 1608262263084
      },
      "RiskLevel" : 3,
      "RemediationEnabled" : false,
      "Annotation" : ""
    } ],
    "TotalCount" : 52,
    "PageSize" : 10,
    "PageNumber" : 1
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|The error message returned because the AliyunServiceRoleForConfig role does not exist.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

