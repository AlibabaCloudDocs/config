# StartConfigRuleEvaluation

Uses a specified rule to evaluate the compliance of target resources.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=StartConfigRuleEvaluation&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StartConfigRuleEvaluation|The operation that you want to perform. Set the value to StartConfigRuleEvaluation. |
|ConfigRuleId|String|Yes|cr-2a914fcf617e00c9\*\*\*\*|The ID of the rule. |
|MultiAccount|Boolean|No|false|Specifies whether to use the specified rule under the member accounts of the current master account for resource compliance evaluation.

 -   true: Use the specified rule under the specified member account or all the member accounts in the resource directory of the current master account to evaluate the target resources.
-   false: Use the specified rule under the current master account to evaluate the target resources. This is the default value.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|1234567|The ID of the member account to which the rule to be used belongs. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

 -   When MemberId is left empty, the system uses the specified rule under the current master account and all its member accounts to evaluate the target resources.
-   When MemberId is set to a specific value, the system uses the specified rule under the specified member account to evaluate the target resources.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDD23A|The ID of the request. |
|Result|Boolean|true|Indicates whether the operation was successful. Valid values:

 -   true: The operation was successful.
-   false: The operation failed. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=StartConfigRuleEvaluation
&ConfigRuleId=cr-2a914fcf617e00c9****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StartConfigRuleEvaluationResponse>
      <RequestId>A7A0FFF8-0B44-40C6-8BBF-3A185EFD5C2B</RequestId>
      <Result>true</Result>
</StartConfigRuleEvaluationResponse>
```

`JSON` format

```
{
  "RequestId": "A7A0FFF8-0B44-40C6-8BBF-3A185EFD5C2B",
  "Result": true
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|The error message returned because the specified rule does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

