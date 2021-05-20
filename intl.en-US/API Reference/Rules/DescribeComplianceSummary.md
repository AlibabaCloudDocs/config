# DescribeComplianceSummary

Queries the statistics of compliance evaluations from the rule and resource dimensions.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeComplianceSummary&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeComplianceSummary|The operation that you want to perform. Set the value to **DescribeComplianceSummary**. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CAEE6F34-DEDC-4AAA-AA8C-946D5D008735|The ID of the request. |
|ComplianceSummary|Object| |The summary of compliance evaluations. |
|ComplianceSummaryByResource|Object| |The summary of compliance evaluations from the resource dimension. |
|CompliantCount|Integer|1|The number of resources evaluated as compliant. |
|NonCompliantCount|Integer|12|The number of resources evaluated as non-compliant. |
|ComplianceSummaryTimestamp|Long|1589853712165|The timestamp when the summary was recorded. |
|TotalCount|Long|13|The total number of resources. |
|ComplianceSummaryByConfigRule|Object| |The summary of compliance evaluations from the rule dimension. |
|CompliantCount|Integer|111|The number of rules whose evaluation results are compliant. |
|NonCompliantCount|Integer|12|The number of rules whose evaluation results are non-compliant. |
|ComplianceSummaryTimestamp|Long|1589853712165|The timestamp when the summary was recorded. |
|TotalCount|Long|123|The total number of rules. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeComplianceSummary
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeComplianceSummaryResponse>
    <RequestId>CAEE6F34-DEDC-4AAA-AA8C-946D5D008735</RequestId>
    <ComplianceSummary>
        <ComplianceSummaryByResource>
            <CompliantCount>29</CompliantCount>
            <NonCompliantCount>581</NonCompliantCount>
            <ComplianceSummaryTimestamp>1589853712165</ComplianceSummaryTimestamp>
        </ComplianceSummaryByResource>
        <ComplianceSummaryByConfigRule>
            <TotalCount>79</TotalCount>
            <CompliantCount>1</CompliantCount>
            <NonCompliantCount>34</NonCompliantCount>
            <ComplianceSummaryTimestamp>1589853712128</ComplianceSummaryTimestamp>
        </ComplianceSummaryByConfigRule>
    </ComplianceSummary>
    <HttpStatusCode>200</HttpStatusCode>
    <Success>true</Success>
</DescribeComplianceSummaryResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CAEE6F34-DEDC-4AAA-AA8C-946D5D008735",
  "ComplianceSummary" : {
    "ComplianceSummaryByResource" : {
      "CompliantCount" : 29,
      "NonCompliantCount" : 581,
      "ComplianceSummaryTimestamp" : 1589853712165
    },
    "ComplianceSummaryByConfigRule" : {
      "TotalCount" : 79,
      "CompliantCount" : 1,
      "NonCompliantCount" : 34,
      "ComplianceSummaryTimestamp" : 1589853712128
    }
  },
  "HttpStatusCode" : 200,
  "Success" : true
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

