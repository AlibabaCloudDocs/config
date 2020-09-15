# ListDiscoveredResources

Queries resources based on specified query criteria.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=ListDiscoveredResources&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListDiscoveredResources|The operation that you want to perform. Set the value to ListDiscoveredResources. |
|PageNumber|Integer|Yes|1|The page number of the page to return. Pages start from page 1. |
|PageSize|Integer|Yes|10|The number of entries to return on each page. Valid values: 1 to 100. |
|ResourceId|String|No|tedst-1\*\*\*\*|The ID of the resource. |
|ResourceDeleted|Integer|No|1|Specifies whether to query deleted or existing resources. Valid values:

-   0: Query deleted resources.
-   1: Query existing resources. |
|ResourceTypes|String|No|ACS::ECS::Instance,ACS::ECS::Disk|The types of the resources to be queried. Separate multiple resource types with commas \(,\). |
|Regions|String|No|cn-hangzhou,cn-shanghai|The IDs of the regions in which the resources are to be queried. Separate multiple regions with commas \(,\). |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the target resources. Valid values:

-   COMPLIANT: The resources are evaluated as compliant.
-   NON\_COMPLIANT: The resources are evaluated as non-compliant. |
|MultiAccount|Boolean|No|false|Specifies whether to query the resources under the member accounts of the current master account. Valid values:

-   true: Query the resources under all the member accounts in the resource directory of the current master account.
-   false: Query the resources under the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose resources are to be queried. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

-   When MemberId is left empty, the system retrieves the resources under the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the resources under the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DiscoveredResourceProfiles|Struct| |The information about the returned resources. |
|DiscoveredResourceProfileList|Array of DiscoveredResourceProfile| |The returned resources. |
|AccountId|Long|123456789|The ID of your Alibaba Cloud account. |
|Region|String|cn-shanghai|The ID of the region where the resource resides. |
|ResourceCreationTime|Long|1588853241|The timestamp when the resource was created. |
|ResourceDeleted|Integer|1|Indicates whether the resource is deleted. Valid values:

-   1: The resource is not deleted.
-   0: The resource is deleted. |
|ResourceId|String|tedst-1\*\*\*\*|The ID of the resource. |
|ResourceName|String|test-resource-name|The name of the resource. |
|ResourceStatus|String|Running|The status of the resource. |
|ResourceType|String|ACS::ActionTrail::Trail|The type of the resource. |
|Tags|String|\{"Tags":\{"Project":\["Simulation"\]\}\}|The tags of the resource. |
|PageNumber|Integer|1|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|10|The number of entries returned per page. Valid values: 1 to 100. |
|TotalCount|Integer|1|The total number of resources. |
|RequestId|String|188AD190-A038-4EEE-9305-E3129808FF05|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ListDiscoveredResources
&PageNumber=1
&PageSize=10
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListDiscoveredResourcesResponse>
      <DiscoveredResourceProfiles>
            <TotalCount>1</TotalCount>
            <PageSize>10</PageSize>
            <PageNumber>1</PageNumber>
            <DiscoveredResourceProfileList>
                  <AccountId>100931896542****</AccountId>
                  <ResourceCreationTime>0</ResourceCreationTime>
                  <ResourceId>tedst-1****</ResourceId>
                  <ResourceName>test-resource-name</ResourceName>
                  <ResourceStatus></ResourceStatus>
                  <Region>cn-shanghai</Region>
                  <ResourceType>ACS::ActionTrail::Trail</ResourceType>
                  <Tags></Tags>
                  <ResourceDeleted>1</ResourceDeleted>
            </DiscoveredResourceProfileList>
      </DiscoveredResourceProfiles>
      <RequestId>188AD190-A038-4EEE-9305-E3129808FF05</RequestId>    
</ListDiscoveredResourcesResponse>
```

`JSON` format

```
{
  "DiscoveredResourceProfiles": {
    "TotalCount": 1,
    "PageSize": 10,
    "PageNumber": 1,
    "DiscoveredResourceProfileList": [
      {
        "AccountId": "100931896542****",
        "ResourceCreationTime": 0,
        "ResourceId": "tedst-1****",
        "ResourceName": "test-resource-name",
        "ResourceStatus": "",
        "Region": "cn-shanghai",
        "ResourceType": "ACS::ActionTrail::Trail",
        "Tags": "",
        "ResourceDeleted": 1
      }
    ]
  },
  "RequestId": "188AD190-A038-4EEE-9305-E3129808FF05"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

