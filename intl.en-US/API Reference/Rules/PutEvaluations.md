# PutEvaluations

Submits the compliance evaluation results.

****

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=PutEvaluations&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|PutEvaluations|The operation that you want to perform. Set the value to PutEvaluations. |
|ResultToken|String|Yes|=lAUbfkWp7GL9AFoQEIStinqBMc4FC8sHvip/1F1npkWUDNS2GEm6xwL6Zl/fSr0bbkWY+aiCLjTJxnp4H/yp/8p/Q8VCAtqG5uhRii4sfnYRnTPnE\*\*\*\*|The token used to return the response. |
|Evaluations|String|No|\[\{"annotation":"Resource type is ACS::CEN::Flowlog, not in ACS::ECS::Instance,ACS::ECS::NetworkInterface.","complianceResourceId":"flowlog-o6wdfo1yvgo4i8\*\*\*\*","complianceResourceType":"ACS::CEN::Flowlog","complianceType":"NOT\_APPLICABLE","orderingTimestamp":1588907220408\}\]|The compliance evaluation results. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7|The ID of the request. |
|Result|Boolean|true|Indicates whether the operation was successful. Valid values:

 -   true: The operation was successful.
-   false: The operation failed. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=PutEvaluations
&ResultToken==lAUbfkWp7GL9AFoQEIStinqBMc4FC8sHvip/1F1npkWUDNS2GEm6xwL6Zl/fSr0bbkWY+aiCLjTJxnp4H/yp/8p/Q8VCAtqG5uhRii4sfnYRnTPnE****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<PutEvaluationsResponse>
      <RequestId>A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7</RequestId>
      <Result>true</Result>
</PutEvaluationsResponse>
```

`JSON` format

```
{
  "RequestId": "A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7",
  "Result": true
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

