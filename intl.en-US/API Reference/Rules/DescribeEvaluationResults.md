# DescribeEvaluationResults

Queries the compliance evaluation results.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeEvaluationResults&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeEvaluationResults|The operation that you want to perform. Set the value to DescribeEvaluationResults. |
|ResourceType|String|No|ACS::ECS::Instance|The type of the resource. This parameter is required when you query compliance evaluation results by resource.

You can call the GetSupportedResourceTypes operation to query the resource types that are supported by Cloud Config. For more information, see [GetSupportedResourceTypes](~~169618~~). |
|ResourceId|String|No|i-bp151g9tpto890zr\*\*\*\*|The ID of the resource. This parameter is required when you query compliance evaluation results by resource. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the target resources. Valid values:

-   COMPLIANT: The resources are evaluated as compliant.
-   NON\_COMPLIANT: The resources are evaluated as non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the target resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|PageNumber|Integer|No|1|The page number of the page to return. Pages start from page 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. |
|ConfigRuleId|String|No|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule.

This parameter is required when you query compliance evaluation results by rule. |
|MultiAccount|Boolean|No|false|Specifies whether to query compliance evaluation results from the member accounts of the current master account. Valid values:

-   true: Query the compliance evaluation results of the target resources under all the member accounts in the resource directory of the current master account.
-   false: Query the compliance evaluation results of the target resources under the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|1234567|The ID of the member account whose compliance evaluation results are to be queried. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

-   When MemberId is left empty, the system retrieves the compliance evaluation results of the target resources under the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the compliance evaluation results of the target resources under the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|EvaluationResults|Struct| |The details of the compliance evaluation results. |
|EvaluationResultList|Array of EvaluationResult| |The information about the compliance evaluation result. |
|Annotation|String|\{"operator": "StringEquals", "property": "$.SslProtocol", "desiredValue": "on", "configuration": "\['off'\]"\}|The annotation to the resources evaluated as non-compliant. |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the target resources. Valid values:

-   COMPLIANT: The resources are evaluated as compliant.
-   NON\_COMPLIANT: The resources are evaluated as non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the target resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|ConfigRuleInvokedTimestamp|Long|1589941923258|The timestamp when the rule was triggered. |
|EvaluationResultIdentifier|Struct| |The identifier of the compliance evaluation result. |
|EvaluationResultQualifier|Struct| |The information about the rule and resources evaluated by the rule. |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-2da35180a8d1008e\*\*\*\*|The Alibaba Cloud Resource Name \(ARN\) of the rule. |
|ConfigRuleId|String|cr-2da35180a8d1008e\*\*\*\*|The ID of the rule. |
|ConfigRuleName|String|level3\_protection-ecs-instances-in-vpc-8e\*\*\*\*|The name of the rule. |
|RegionId|String|cn-hangzhou|The ID of the region. |
|ResourceId|String|i-bp151g9tpto890zr\*\*\*\*|The ID of the evaluated resource. |
|ResourceType|String|ACS::ECS::Instance|The type of the evaluated resource. |
|OrderingTimestamp|Long|1589941923117|The timestamp when the compliance evaluation was performed. |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

-   ConfigurationItemChangeNotification: The rule is triggered upon configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|ResultRecordedTimestamp|Long|1589941923432|The timestamp when the result was recorded. |
|RiskLevel|Integer|1|The risk level of the resources that are not compliant with the rule. Valid values:

-   1: critical
-   2: warning
-   3: info |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|10|The number of entries returned per page. Valid values: 1 to 100. |
|TotalCount|Long|2|The total number of compliance evaluation results. |
|RequestId|String|7A90353C-A64F-4914-A452-68995753F5C2|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeEvaluationResults
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeEvaluationResultsResponse>
      <RequestId>7A90353C-A64F-4914-A452-68995753F5C2</RequestId>
      <EvaluationResults>
            <EvaluationResultList>
                  <ConfigRuleInvokedTimestamp>1589941923258</ConfigRuleInvokedTimestamp>
                  <ComplianceType>COMPLIANT</ComplianceType>
                  <ResultRecordedTimestamp>1589941923432</ResultRecordedTimestamp>
                  <InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
                  <EvaluationResultIdentifier>
                        <EvaluationResultQualifier>
                              <ConfigRuleId>cr-2da35180a8d1008e****</ConfigRuleId>
                              <ConfigRuleArn>acs:config::120390217529****:config-rule/cr-2da35180a8d1008e****</ConfigRuleArn>
                              <ResourceId>i-bp151g9tpto890zr****</ResourceId>
                              <ConfigRuleName>level3_protection-ecs-instances-in-vpc-8e0fc7</ConfigRuleName>
                              <ResourceType>ACS::ECS::Instance</ResourceType>
                        </EvaluationResultQualifier>
                        <OrderingTimestamp>1589941923117</OrderingTimestamp>
                  </EvaluationResultIdentifier>
                  <RiskLevel>1</RiskLevel>
                  <Annotation></Annotation>
            </EvaluationResultList>
            <EvaluationResultList>
                  <ConfigRuleInvokedTimestamp>1589941923258</ConfigRuleInvokedTimestamp>
                  <ComplianceType>COMPLIANT</ComplianceType>
                  <ResultRecordedTimestamp>1589941923629</ResultRecordedTimestamp>
                  <InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
                  <EvaluationResultIdentifier>
                        <EvaluationResultQualifier>
                              <ConfigRuleId>cr-2da35180a8d1008e****</ConfigRuleId>
                              <ConfigRuleArn>acs:config::120390217529****:config-rule/cr-2da35180a8d1008e****</ConfigRuleArn>
                              <ResourceId>i-bp151g9tpto890zr****</ResourceId>
                              <ConfigRuleName>level3_protection-ecs-instance-no-public-ip-8e0fc7</ConfigRuleName>
                              <ResourceType>ACS::ECS::Instance</ResourceType>
                        </EvaluationResultQualifier>
                        <OrderingTimestamp>1589941923117</OrderingTimestamp>
                  </EvaluationResultIdentifier>
                  <RiskLevel>1</RiskLevel>
                  <Annotation></Annotation>
            </EvaluationResultList>
            <TotalCount>3</TotalCount>
            <PageSize>10</PageSize>
            <PageNumber>1</PageNumber>
      </EvaluationResults>
</DescribeEvaluationResultsResponse>
```

`JSON` format

```
{
    "RequestId": "7A90353C-A64F-4914-A452-68995753F5C2",
    "EvaluationResults": {
        "EvaluationResultList": [
            {
                "ConfigRuleInvokedTimestamp": 1589941923258,
                "ComplianceType": "COMPLIANT",
                "ResultRecordedTimestamp": 1589941923432,
                "InvokingEventMessageType": "ConfigurationItemChangeNotification",
                "EvaluationResultIdentifier": {
                    "EvaluationResultQualifier": {
                        "ConfigRuleId": "cr-2da35180a8d1008e****",
                        "ConfigRuleArn": "acs:config::120390217529****:config-rule/cr-2da35180a8d1008e****",
                        "ResourceId": "i-bp151g9tpto890zr****",
                        "ConfigRuleName": "level3_protection-ecs-instances-in-vpc-8e****",
                        "ResourceType": "ACS::ECS::Instance"
                    },
                    "OrderingTimestamp": 1589941923117
                },
                "RiskLevel": 1,
                "Annotation": ""
            },
            {
                "ConfigRuleInvokedTimestamp": 1589941923258,
                "ComplianceType": "COMPLIANT",
                "ResultRecordedTimestamp": 1589941923629,
                "InvokingEventMessageType": "ConfigurationItemChangeNotification",
                "EvaluationResultIdentifier": {
                    "EvaluationResultQualifier": {
                        "ConfigRuleId": "cr-2da35180a8d1008e****",
                        "ConfigRuleArn": "acs:config::120390217529****:config-rule/cr-2da35180a8d1008e****",
                        "ResourceId": "i-bp151g9tpto890zr****",
                        "ConfigRuleName": "level3_protection-ecs-instance-no-public-ip-8e****",
                        "ResourceType": "ACS::ECS::Instance"
                    },
                    "OrderingTimestamp": 1589941923117
                },
                "RiskLevel": 1,
                "Annotation": ""
            }
        ],
        "TotalCount": 3,
        "PageSize": 10,
        "PageNumber": 1
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|The error message returned because the AliyunServiceRoleForConfig role does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

