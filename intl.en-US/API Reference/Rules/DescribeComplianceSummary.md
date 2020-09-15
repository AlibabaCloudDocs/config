# DescribeComplianceSummary

Queries the summary of compliance evaluations from the rule and resource dimensions.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeComplianceSummary&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeComplianceSummary|The operation that you want to perform. Set the value to DescribeComplianceSummary. |
|MultiAccount|Boolean|No|false|Specifies whether to query the summary of compliance evaluations from the member accounts under the master account. Valid values:

-   true: Query the summary of compliance evaluations from all the member accounts in the resource directory of the current master account.
-   false: Query the summary of compliance evaluations from the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|123456789|The ID of the member account from which you want to query the summary of compliance evaluations. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

-   When MemberId is left empty, the system retrieves the summary of compliance evaluations from the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the summary of compliance evaluations from the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ComplianceSummary|Struct| |The summary of compliance evaluations. |
|ComplianceSummaryByConfigRule|Struct| |The summary of compliance evaluations from the rule dimension. |
|ComplianceSummaryTimestamp|Long|1589853712165|The timestamp when the summary was recorded. |
|CompliantCount|Integer|111|The number of rules whose evaluation results are compliant. |
|NonCompliantCount|Integer|12|The number of rules whose evaluation results are non-compliant. |
|TotalCount|Long|123|The total number of rules. |
|ComplianceSummaryByResource|Struct| |The summary of compliance evaluations from the resource dimension. |
|ComplianceSummaryTimestamp|Long|1589853712165|The timestamp when the summary was recorded. |
|CompliantCount|Integer|1|The number of resources evaluated as compliant. |
|NonCompliantCount|Integer|12|The number of resources evaluated as non-compliant. |
|TotalCount|Long|13|The total number of resources. |
|RequestId|String|CAEE6F34-DEDC-4AAA-AA8C-946D5D008735|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeComplianceSummary
&<Common request parameters>
```

Sample success responses

`XML` format

```
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
{
  "RequestId": "CAEE6F34-DEDC-4AAA-AA8C-946D5D008735",
  "ComplianceSummary": {
    "ComplianceSummaryByResource": {
      "CompliantCount": 29,
      "NonCompliantCount": 581,
      "ComplianceSummaryTimestamp": 1589853712165
    },
    "ComplianceSummaryByConfigRule": {
      "TotalCount": 79,
      "CompliantCount": 1,
      "NonCompliantCount": 34,
      "ComplianceSummaryTimestamp": 1589853712128
    }
  },
  "HttpStatusCode": 200,
  "Success": true
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

