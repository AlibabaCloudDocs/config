# GetDiscoveredResourceSummary

Queries the statistics of the resources monitored by Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceSummary&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetDiscoveredResourceSummary|The operation that you want to perform. Set the value to **GetDiscoveredResourceSummary**. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DiscoveredResourceSummary|Object| |The statistics of the resources monitored by Cloud Config. |
|RegionCount|Integer|6|The number of the regions involved in the monitoring. |
|ResourceCount|Integer|7|The number of the resources monitored by Cloud Config. |
|ResourceTypeCount|Integer|45|The number of the resource types monitored by Cloud Config. |
|RequestId|String|2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=GetDiscoveredResourceSummary
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetDiscoveredResourceSummaryResponse>
    <DiscoveredResourceSummary>
        <ResourceTypeCount>45</ResourceTypeCount>
        <ResourceCount>7</ResourceCount>
        <RegionCount>6</RegionCount>
    </DiscoveredResourceSummary>
    <RequestId>2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C</RequestId>
</GetDiscoveredResourceSummaryResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "DiscoveredResourceSummary" : {
    "ResourceTypeCount" : "45",
    "ResourceCount" : "7",
    "RegionCount" : "6"
  },
  "RequestId" : "2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

