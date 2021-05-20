# ListDiscoveredResources

Queries resources based on specified query criteria.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=ListDiscoveredResources&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListDiscoveredResources|The operation that you want to perform. Set the value to **ListDiscoveredResources**. |
|ResourceId|String|No|s-hp3d9r78m7uysiii\*\*\*\*|The ID of the resource. |
|ResourceDeleted|Integer|No|1|Specifies whether the resource is deleted. Valid values:

 -   1: The resource is not deleted.
-   0: The resource is deleted. |
|PageSize|Integer|Yes|1|The number of entries to return on each page. Valid values: 1 to 100. |
|PageNumber|Integer|Yes|10|The number of the page to return. Pages start from page 1. |
|ResourceTypes|String|No|ACS::ECS::Snapshot|The type of the resource. Separate multiple resources with commas \(,\). |
|Regions|String|No|cn-huhehaote|The IDs of the regions in which the resources are to be queried. Separate multiple regions with commas \(,\). |
|ComplianceType|String|No|COMPLIANT|The compliance evaluation result of the resources. Valid values:

 -   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DiscoveredResourceProfiles|Object| |The information about the returned resources. |
|DiscoveredResourceProfileList|Array of DiscoveredResourceProfile| |The returned resources. |
|ResourceType|String|ACS::ECS::Snapshot|The type of the resource. |
|Region|String|cn-huhehaote|The ID of the region. |
|ResourceCreationTime|Long|1618675206000|The timestamp when the resource was created. |
|Tags|String|\{\\"key1\\":\[\\"value2\\"\],\\"key3\\":\[\\"value4\\"\]\}|The tags of the resource. |
|AccountId|Long|987654321|The ID of your Alibaba Cloud account. |
|ResourceId|String|s-hp3d9r78m7uysiii\*\*\*\*|The ID of the resource. |
|ResourceName|String|auto2.0\_20210418\_sp-hp3e2kkt8ugld7ox\*\*\*\*|The name of the resource. |
|ResourceDeleted|Integer|1|Indicates whether the resource is deleted. Valid values:

 -   1: The resource is not deleted.
-   0: The resource is deleted. |
|ResourceStatus|String|accomplished|The status of the resource. The parameter value varies with the resource type and may be left empty.

 Examples:

 -   If ResourceType is set to ACS::ECS::Instance, the resource is an Elastic Compute Service \(ECS\) instance which has a specific state. In this case, valid values of this parameter include Running and Stopped.
-   If ResourceType is set to ACS::OSS::Bucket, the resource is an Object Storage Service \(OSS\) bucket which does not have a specific state. In this case, this parameter is left empty. |
|PageNumber|Integer|10|The page number of the returned page. Pages start from page 1. |
|PageSize|Integer|1|The number of entries returned on each page. Valid values: 1 to 100. |
|TotalCount|Integer|129|The total number of resources. |
|RequestId|String|C7817373-78CB-4F9A-8AFA-E7A88E9D64A2|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ListDiscoveredResources
&PageNumber=10
&PageSize=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListDiscoveredResourcesResponse>
	<DiscoveredResourceProfiles>
		<TotalCount>129</TotalCount>
		<PageSize>1</PageSize>
		<PageNumber>10</PageNumber>
		<DiscoveredResourceProfileList>
			<AccountId>987654321</AccountId>
			<ResourceCreationTime>1618675206000</ResourceCreationTime>
			<ResourceId>s-hp3d9r78m7uysiii****</ResourceId>
			<ResourceName>auto2.0_20210418_sp-hp3e2kkt8ugld7ox****</ResourceName>
			<Region>cn-huhehaote</Region>
			<ResourceStatus>accomplished</ResourceStatus>
			<ResourceType>ACS::ECS::Snapshot</ResourceType>
			<ResourceDeleted>1</ResourceDeleted>
			<Tags>{\"key1\":[\"value2\"],\"key3\":[\"value4\"]}</Tags>
		</DiscoveredResourceProfileList>
	</DiscoveredResourceProfiles>
	<RequestId>C7817373-78CB-4F9A-8AFA-E7A88E9D64A2</RequestId>
</ListDiscoveredResourcesResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "DiscoveredResourceProfiles" : {
    "TotalCount" : 129,
    "PageSize" : 1,
    "PageNumber" : 10,
    "DiscoveredResourceProfileList" : [ {
      "AccountId" : "987654321",
      "ResourceCreationTime" : 1618675206000,
      "ResourceId" : "s-hp3d9r78m7uysiii****",
      "ResourceName" : "auto2.0_20210418_sp-hp3e2kkt8ugld7ox****",
      "Region" : "cn-huhehaote",
      "ResourceStatus" : "accomplished",
      "ResourceType" : "ACS::ECS::Snapshot",
      "ResourceDeleted" : 1,
      "Tags" : "{\"key1\":[\"value2\"],\"key3\":[\"value4\"]}"
    } ]
  },
  "RequestId" : "C7817373-78CB-4F9A-8AFA-E7A88E9D64A2"
}
```

## Error codes

|HttpCode|Error codes|Error message|Description|
|--------|-----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

