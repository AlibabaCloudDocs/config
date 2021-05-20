# GetDiscoveredResourceCounts

Queries the number of resources.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceCounts&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetDiscoveredResourceCounts|The operation that you want to perform. Set the value to GetDiscoveredResourceCounts. |
|GroupByKey|String|No|ResourceType|The dimension by which resources are grouped. Valid values:

 -   ResourceType: specifies that resources are grouped by type.
-   Region: specifies that resources are grouped by region. |
|MultiAccount|Boolean|No|true|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|54BFA4FB-6E08-4D58-9E83-1A8A3EC80247|The ID of the request. |
|GroupedResourceCounts|Object| |The returned information about resources. |
|GroupedResourceCountList|Array of GroupedResourceCount| |The information about resources in a specific group. |
|ResourceCount|Long|13|The number of resources in the group. |
|GroupName|String|ACS::ECS::Snapshot|The name of the resource group. |
|GroupByKey|String|ResourceType|The dimension by which resources are grouped. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=GetDiscoveredResourceCounts
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetDiscoveredResourceCountsResponse>
    <RequestId>54BFA4FB-6E08-4D58-9E83-1A8A3EC80247</RequestId>    
    <GroupedResourceCounts>
        <GroupedResourceCountList>
            <GroupName>ACS::ECS::Snapshot</GroupName>
            <ResourceCount>13</ResourceCount>
        </GroupedResourceCountList>
        <GroupedResourceCountList>
            <GroupName>ACS::ECS::SecurityGroup</GroupName>
            <ResourceCount>10</ResourceCount>
        </GroupedResourceCountList>
        <GroupByKey>ResourceType</GroupByKey>
    </GroupedResourceCounts>
</GetDiscoveredResourceCountsResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "54BFA4FB-6E08-4D58-9E83-1A8A3EC80247",
  "GroupedResourceCounts" : {
    "GroupedResourceCountList" : [ {
      "GroupName" : "ACS::ECS::Snapshot",
      "ResourceCount" : 13
    }, {
      "GroupName" : "ACS::ECS::SecurityGroup",
      "ResourceCount" : 10
    } ],
    "GroupByKey" : "ResourceType"
  }
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

