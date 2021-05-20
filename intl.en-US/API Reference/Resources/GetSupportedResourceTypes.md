# GetSupportedResourceTypes

Queries the resource types that are supported by Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetSupportedResourceTypes&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetSupportedResourceTypes|The operation that you want to perform. Set the value to **GetSupportedResourceTypes**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ResourceTypes|Array of String|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|The types of resources that are supported by Cloud Config. |
|RequestId|String|6CE4ABA1-9A57-41A9-8EA9-E8B17D4671CD|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=GetSupportedResourceTypes
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetSupportedResourceTypesResponse>
		<ResourceTypes>ACS::ECS::Instance</ResourceTypes>
		<ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
		<RequestId>3A0D65E8-D5C0-4664-B257-950F7A5E33C3</RequestId>
</GetSupportedResourceTypesResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ResourceTypes" : [ "ACS::ECS::Instance", "ACS::ECS::NetworkInterface" ],
  "RequestId" : "3A0D65E8-D5C0-4664-B257-950F7A5E33C3"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

