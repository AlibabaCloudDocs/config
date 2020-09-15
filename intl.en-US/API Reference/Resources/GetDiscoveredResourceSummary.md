# GetDiscoveredResourceSummary

Queries the statistics of the resources monitored by Cloud Config.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceSummary&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetDiscoveredResourceSummary|The operation that you want to perform. Set the value to GetDiscoveredResourceSummary. |
|MultiAccount|Boolean|No|false|Specifies whether to query the statistics of the resources, including the numbers of monitored resource types, monitored resources, and involved regions, under the member accounts of the current master account. Valid values:

-   true: Query the statistics of the resources under all the member accounts in the resource directory of the current master account.
-   false: Query the statistics of the resources under the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose resources are to be queried. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

-   When MemberId is left empty, the system retrieves the statistics of the resources under the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the statistics of the resources under the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DiscoveredResourceSummary|Struct| |The statistics of the resources monitored by Cloud Config. |
|RegionCount|Integer|6|The number of the regions involved in the monitoring. |
|ResourceCount|Integer|7|The number of the resources monitored by Cloud Config. |
|ResourceTypeCount|Integer|45|The number of the resource types monitored by Cloud Config. |
|RequestId|String|2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=GetDiscoveredResourceSummary
&<Common request parameters>
```

Sample success responses

`XML` format

```
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
{
    "DiscoveredResourceSummary": {
        "ResourceTypeCount": "45",
        "ResourceCount": "7",
        "RegionCount": "6"
    },
    "RequestId": "2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

