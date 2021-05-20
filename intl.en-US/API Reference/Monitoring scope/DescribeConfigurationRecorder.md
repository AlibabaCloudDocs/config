# DescribeConfigurationRecorder

Queries the types of resources that are monitored by Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeConfigurationRecorder&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeConfigurationRecorder|The operation that you want to perform. Set the value to DescribeConfigurationRecorder. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConfigurationRecorder|Struct| |The details of the configuration recorder that monitors resources. |
|AccountId|Long|123456789|The ID of your Alibaba Cloud account. |
|ConfigurationRecorderStatus|String|REGISTERED|The status of the configuration recorder. Valid values:

 -   REGISTRABLE: The configuration recorder has not been registered.
-   BUILDING: The configuration recorder is being deployed.
-   REGISTERED: The configuration recorder has been registered.
-   REBUILDING: The configuration recorder is being redeployed. |
|ResourceTypes|List|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|The types of resources that are monitored by Cloud Config. |
|RequestId|String|A3601178-A6A2-4636-BE56-1116F73C0B0C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeConfigurationRecorder
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeConfigurationRecorderResponse>
		  <RequestId>A3601178-A6A2-4636-BE56-1116F73C0B0C</RequestId>
		  <ConfigurationRecorder>
			    <ResourceTypes>ACS::ECS::Instance</ResourceTypes>
			    <ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
			    <AccountId>123456789</AccountId>
			    <ConfigurationRecorderStatus>REGISTERED</ConfigurationRecorderStatus>
		  </ConfigurationRecorder>
</DescribeConfigurationRecorderResponse>
```

`JSON` format

```
{
  "RequestId": "A3601178-A6A2-4636-BE56-1116F73C0B0C",  
  "ConfigurationRecorder": {
    "ResourceTypes": [
      "ACS::ECS::Instance",
      "ACS::ECS::NetworkInterface"
    ],
    "AccountId": "123456789",
    "ConfigurationRecorderStatus": "REGISTERED"
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

