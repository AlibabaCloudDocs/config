# DescribeCompliance

Queries the statistics of compliance evaluations based on compliance types.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeCompliance&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeCompliance|The operation that you want to perform. Set the value to DescribeCompliance. |
|ResourceType|String|No|ACS::ECS::Instance|The type of the resource.

 **Note:** This parameter is required when you query compliance evaluation results by resource. |
|ResourceId|String|No|i-bp151g9tpto890zr\*\*\*\*|The ID of the resource. If you assign values to both the ResourceId and ConfigRuleId parameters, the value of ConfigRuleId prevails.

 **Note:** This parameter is required when you query compliance evaluation results by resource. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the target resources. Valid values:

 -   COMPLIANT: The resources are evaluated as compliant.
-   NON\_COMPLIANT: The resources are evaluated as non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the target resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|ConfigRuleId|String|No|cr-12b398b633820012\*\*\*\*|The ID of the rule. If you assign values to both the ResourceId and ConfigRuleId parameters, the value of ConfigRuleId prevails.

 **Note:** This parameter is required when you query compliance evaluation results by rule. |
|MultiAccount|Boolean|No|false|Specifies whether to query the statistics of compliance evaluations from the member accounts of the current master account. Valid values:

 -   true: Query the statistics of compliance evaluations from all the member accounts in the resource directory of the current master account.
-   false: Query the statistics of compliance evaluations from the current master account. This is the default value.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|1234567|The ID of the member account from which you want to query the statistics of compliance evaluations. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

 -   When MemberId is left empty, the system retrieves the statistics of compliance evaluations from the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the statistics of compliance evaluations from the specified member account.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ComplianceResult|Struct| |The statistics of compliance evaluations. |
|Compliances|Array of Compliances| |The compliance evaluation results based on compliance types. |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the target resources. Valid values:

 -   COMPLIANT: The resources are evaluated as compliant.
-   NON\_COMPLIANT: The resources are evaluated as non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the target resources.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|Count|Integer|13|The number of compliance evaluations with the corresponding result.

 -   This parameter returns the number of resources for each compliance type if you set the ResourceId parameter in the request.
-   This parameter returns the number of triggered rules for each compliance type if you set the ConfigRuleId parameter in the request. |
|TotalCount|Long|13|The total number of compliance evaluations.

 -   This parameter returns the total number of evaluated resources if you set the ResourceId parameter in the request.
-   This parameter returns the total number of triggered rules if you set the ConfigRuleId parameter in the request. |
|RequestId|String|17306AB1-34E0-468F-BD7B-68D8AEAB754F|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeCompliance
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeComplianceResponse>
    <RequestId>17306AB1-34E0-468F-BD7B-68D8AEAB754F</RequestId>
    <Compliances>
        <Compliances>
            <ComplianceType>NOT_APPLICABLE</ComplianceType>
            <Count>0</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>NON_COMPLIANT</ComplianceType>
            <Count>5</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>INSUFFICIENT_DATA</ComplianceType>
            <Count>0</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>COMPLIANT</ComplianceType>
            <Count>13</Count>
        </Compliances>
    </CompliancesResponse>
</DescribeCompliance>
```

`JSON` format

```
{
  "RequestId": "17306AB1-34E0-468F-BD7B-68D8AEAB754F",
  "Compliances": {
    "Compliances": [
      {
        "ComplianceType": "NOT_APPLICABLE",
        "Count": 0
      },
      {
        "ComplianceType": "NON_COMPLIANT",
        "Count": 5
      },
      {
        "ComplianceType": "INSUFFICIENT_DATA",
        "Count": 0
      },
      {
        "ComplianceType": "COMPLIANT",
        "Count": 13
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

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

