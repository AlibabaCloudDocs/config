# StopConfigRules

Disables multiple rules at a time to set them to Inactive.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=StopConfigRules&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StopConfigRules|The operation that you want to perform. Set the value to StopConfigRules. |
|ConfigRuleIds|String|Yes|cr-2da35180a8d1008e\*\*\*\*,cr-2da35180a8d1008e\*\*\*\*|The IDs of the rules. Separate multiple rule IDs with commas \(,\). You can specify a maximum of 50 rule IDs at a time. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConfigRuleIds|List|\["cr-2da35180a8d1008e\*\*\*\*","cr-2da351800131233a\*\*\*\*"\]|The IDs of the disabled rules. |
|RequestId|String|49C1A88F-D163-46DF-84A6-F300229F37AE|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=StopConfigRules
&ConfigRuleIds=cr-2da35180a8d1008e****,cr-2da35180a8d1008e****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StopConfigRulesResponse>
      <ConfigRuleIds>cr-2da35180a8d1008e****</ConfigRuleIds>
      <ConfigRuleIds>cr-2da351800131233a****</ConfigRuleIds>
      <RequestId>49C1A88F-D163-46DF-84A6-F300229F37AE</RequestId>
</StopConfigRulesResponse>
```

`JSON` format

```
{
    "ConfigRuleIds": [
        "cr-2da35180a8d1008e****",
        "cr-2da351800131233a****"
    ],
    "RequestId": "49C1A88F-D163-46DF-84A6-F300229F37AE"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|400|Invalid.ConfigRuleIds.SizeExceed|The maximum number of ConfigRuleIds cannot exceed 50.|The error message returned because the number of the specified rule IDs is greater than 50.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

