# GetDiscoveredResourceCounts

Queries the number of resources of each type or in each region supported by Cloud Config under the specified account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceCounts&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetDiscoveredResourceCounts|The operation that you want to perform. Set the value to GetDiscoveredResourceCounts. |
|GroupByKey|String|No|ResourceType|The dimension by which resources are grouped. Valid values:

-   ResourceType: specifies that resources are grouped by type.
-   Region: specifies that resources are grouped by region. |
|MultiAccount|Boolean|No|true|Specifies whether to query the numbers of resources under the member accounts of the current master account. Valid values:

-   true: Query the numbers of resources under all the member accounts in the resource directory of the current master account.
-   false: Query the numbers of resources under the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose resources are to be queried. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

-   When MemberId is left empty, the system retrieves the numbers of resources under the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the numbers of resources under the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|GroupedResourceCounts|Struct| |The returned information about resources. |
|GroupByKey|String|ResourceType|The dimension by which resources are grouped. |
|GroupedResourceCountList|Array of GroupedResourceCount| |The information about resources in a specific group. |
|GroupName|String|ACS::ECS::Snapshot|The name of the resource group. |
|ResourceCount|Long|13|The number of resources in the group. |
|RequestId|String|54BFA4FB-6E08-4D58-9E83-1A8A3EC80247|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=GetDiscoveredResourceCounts
&<Common request parameters>
```

Sample success responses

`XML` format

```
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
{
  "RequestId": "54BFA4FB-6E08-4D58-9E83-1A8A3EC80247",
  "GroupedResourceCounts": {
    "GroupedResourceCountList": [
      {
        "GroupName": "ACS::ECS::Snapshot",
        "ResourceCount": 13
      },
      {
        "GroupName": "ACS::ECS::SecurityGroup",
        "ResourceCount": 10
      }
    ],
    "GroupByKey": "ResourceType"
  }
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

