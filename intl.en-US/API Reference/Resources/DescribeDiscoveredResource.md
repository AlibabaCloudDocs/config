# DescribeDiscoveredResource

Queries the configuration of a resource.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeDiscoveredResource&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDiscoveredResource|The operation that you want to perform. Set the value to **DescribeDiscoveredResource**. |
|ResourceId|String|Yes|adaf.zhilon\*\*\*\*|The ID of the resource. |
|ResourceType|String|Yes|ACS::CDN::Domain|The type of the resource.

 **Note:** You can call the GetSupportedResourceTypes operation to query the resource types supported by Cloud Config. For more information, see [GetSupportedResourceTypes](~~169618~~). |
|Region|String|Yes|cn-hangzhou|The ID of the region. |
|MultiAccount|Boolean|No|true|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|E4D71ACE-6B0A-46E0-8352-56952378CC7F|The ID of the request. |
|DiscoveredResourceDetail|Object| |The information about the resource. |
|AvailabilityZone|String|cn-hangzhou-h|The zone where the resource resides. |
|ResourceType|String|ACS::CDN::Domain|The type of the resource. |
|Configuration|String|\{\\"Description\\":\\"\\",\\"SslProtocol\\":\\"off\\",\\"DomainName\\":\\"adaf.zhilong\*\*\*\*\\",\\"GmtModified\\":\\"2019-04-10T03:11Z\\",\\"CdnType\\":\\"web\\",\\"GmtCreated\\":\\"2016-03-03T01:31:35Z\\",\\"Cname\\":\\"adaf.zhilong.me.w.kun\*\*\*\*.com\\",\\"Sources\\":\{\\"Source\\":\[\{\\"Type\\":\\"oss\\",\\"Content\\":\\"test2-mh.oss-cn-hangzhou.aliyuncs.com\\",\\"Priority\\":\\"20\\",\\"Port\\":80,\\"Weight\\":\\"10\\"\}\]\},\\"DomainStatus\\":\\"offline\\",\\"Sandbox\\":\\"\\"\}|The configuration of the resource. |
|Region|String|cn-hangzhou|The ID of the region. |
|ResourceCreationTime|Long|1456968695000|The timestamp when the resource was created. |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|The tags of the resource. |
|AccountId|Long|987654321|The ID of your Alibaba Cloud account. |
|ResourceId|String|adaf.zhilon\*\*\*\*|The ID of the resource. |
|ResourceDeleted|Integer|1|Indicates whether the resource is deleted. Valid values:

 -   1: The resource is not deleted.
-   0: The resource is deleted. |
|ResourceName|String|test-resource-name|The name of the resource. |
|ResourceStatus|String|offline|The status of the resource. The parameter value varies with the resource type and may be left empty. Examples:

 -   If ResourceType is set to ACS::ECS::Instance, the resource is an Elastic Compute Service \(ECS\) instance which has a specific state. In this case, valid values of this parameter include Running and Stopped.
-   If ResourceType is set to ACS::OSS::Bucket, the resource is an Object Storage Service \(OSS\) bucket which does not have a specific state. In this case, this parameter is left empty. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeDiscoveredResource
&Region=cn-hangzhou
&ResourceId=adaf.zhilon****
&ResourceType=ACS::CDN::Domain
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeDiscoveredResourceResponse>
	<RequestId>E4D71ACE-6B0A-46E0-8352-56952378CC7F</RequestId>
	<DiscoveredResourceDetail>
		<accountId>987654321</accountId>
		<resourceId>adaf.zhilon****</resourceId>
		<resourceStatus>offline</resourceStatus>
		<configuration>{\"Description\":\"\",\"SslProtocol\":\"off\",\"DomainName\":\"adaf.zhilong****\",\"GmtModified\":\"2019-04-10T03:11Z\",\"CdnType\":\"web\",\"GmtCreated\":\"2016-03-03T01:31:35Z\",\"Cname\":\"adaf.zhilong.me.w.kun****.com\",\"Sources\":{\"Source\":[{\"Type\":\"oss\",\"Content\":\"test2-mh.oss-cn-hangzhou.aliyuncs.com\",\"Priority\":\"20\",\"Port\":80,\"Weight\":\"10\"}]},\"DomainStatus\":\"offline\",\"Sandbox\":\"\"}</configuration>
		<resourceDeleted>1</resourceDeleted>
		<resourceName>test-resource-name</resourceName>
		<region>cn-hangzhou</region>
		<availabilityZone>cn-hangzhou-h</availabilityZone>
		<resourceCreationTime>1456968695000</resourceCreationTime>
		<tags>{\"\"hc\"\":[\"\"value2\"\"]}</tags>
		<resourceType>ACS::CDN::Domain</resourceType>
	</DiscoveredResourceDetail>
</DescribeDiscoveredResourceResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "E4D71ACE-6B0A-46E0-8352-56952378CC7F",
  "DiscoveredResourceDetail" : {
    "accountId" : "987654321",
    "resourceId" : "adaf.zhilon****",
    "resourceStatus" : "offline",
    "configuration" : "{\"Description\":\"\",\"SslProtocol\":\"off\",\"DomainName\":\"adaf.zhilong****\",\"GmtModified\":\"2019-04-10T03:11Z\",\"CdnType\":\"web\",\"GmtCreated\":\"2016-03-03T01:31:35Z\",\"Cname\":\"adaf.zhilong.me.w.kun****.com\",\"Sources\":{\"Source\":[{\"Type\":\"oss\",\"Content\":\"test2-mh.oss-cn-hangzhou.aliyuncs.com\",\"Priority\":\"20\",\"Port\":80,\"Weight\":\"10\"}]},\"DomainStatus\":\"offline\",\"Sandbox\":\"\"}",
    "resourceDeleted" : 1,
    "resourceName" : "test-resource-name",
    "region" : "cn-hangzhou",
    "availabilityZone" : "cn-hangzhou-h",
    "resourceCreationTime" : 1456968695000,
    "tags" : "{\"\"hc\"\":[\"\"value2\"\"]}",
    "resourceType" : "ACS::CDN::Domain"
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

