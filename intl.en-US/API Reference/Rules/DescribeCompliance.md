# DescribeCompliance

Queries the statistics of compliance evaluations based on compliance types.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeCompliance&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeCompliance|The operation that you want to perform. Set the value to **DescribeCompliance**. |
|ResourceType|String|No|ACS::ECS::Instance|The type of the resource.

 If you query compliance evaluation results by resource, you must specify the ResourceType and ResourceId parameters. |
|ResourceId|String|No|i-bp151g9tpto890zr\*\*\*\*|The ID of the resource.

 If you query compliance evaluation results by resource, you must specify the ResourceType and ResourceId parameters. |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|ConfigRuleId|String|No|cr-12b398b633820012\*\*\*\*|The ID of the rule.

 If you query compliance evaluation results by resource, you must specify the ConfigRuleId, ResourceType, and ResourceId parameters. Otherwise, the ConfigRuleId parameter becomes invalid. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|1234567|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ComplianceResult|Object| |The statistics of compliance evaluations. |
|TotalCount|Long|13|The total number of compliance evaluations.

 -   This parameter returns the total number of evaluated resources if you set the ResourceId parameter in the request.
-   This parameter returns the total number of triggered rules if you set the ConfigRuleId parameter in the request. |
|Compliances|Array of Compliances| |The compliance evaluation results based on compliance types. |
|ComplianceType|String|COMPLIANT|The compliance evaluation result of the resource. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant.
-   NOT\_APPLICABLE: The rule does not apply to the resource.
-   INSUFFICIENT\_DATA: The resource data is insufficient. |
|Count|Integer|13|The number of compliance evaluations with the corresponding result.

 -   This parameter returns the total number of evaluated resources if you set the ResourceId parameter in the request.
-   This parameter returns the total number of triggered rules if you set the ConfigRuleId parameter in the request. |
|RequestId|String|17306AB1-34E0-468F-BD7B-68D8AEAB754F|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeCompliance
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

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
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "17306AB1-34E0-468F-BD7B-68D8AEAB754F",
  "Compliances" : {
    "Compliances" : [ {
      "ComplianceType" : "NOT_APPLICABLE",
      "Count" : 0
    }, {
      "ComplianceType" : "NON_COMPLIANT",
      "Count" : 5
    }, {
      "ComplianceType" : "INSUFFICIENT_DATA",
      "Count" : 0
    }, {
      "ComplianceType" : "COMPLIANT",
      "Count" : 13
    } ]
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

