# DescribeDiscoveredResource

Queries the configuration of a resource.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeDiscoveredResource&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDiscoveredResource|The operation that you want to perform. Set the value to DescribeDiscoveredResource. |
|Region|String|Yes|cn-hangzhou|The ID of the region. |
|ResourceId|String|Yes|adaf.zhilon\*\*\*\*|The ID of the resource. |
|ResourceType|String|Yes|ACS::CDN::Domain|The type of the resource.

 **Note:** You can call the GetSupportedResourceTypes operation to query the resource types that are supported by Cloud Config. For more information, see [GetSupportedResourceTypes](~~169618~~). |
|MultiAccount|Boolean|No|true|Specifies whether to query the configuration of the specified resource under the member accounts of the current master account. Valid values:

 -   true: Query the configuration of the specified resource under the specified member account in the resource directory of the current master account.
-   false: Query the configuration of the specified resource under the current master account. This is the default value.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose resource configuration is to be queried. This parameter is empty by default. This parameter is available only when MultiAccount is set to true.

 -   When MemberId is left empty, the system retrieves the configuration of the specified resource under the current master account and all its member accounts.
-   When MemberId is set to a specific value, the system retrieves the configuration of the specified resource under the specified member account.

 **Note:** If you are using Cloud Config for individuals, ignore this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DiscoveredResourceDetail|Struct| |The information about the resource. |
|AccountId|Long|123456789|The ID of your Alibaba Cloud account. |
|AvailabilityZone|String|cn-hangzhou-h|The ID of the zone where the resource resides. |
|Configuration|String|\{"Description":"","SslProtocol":"off","DomainName":"adaf.zhilong.me","GmtModified":"2019-04-10T03:11Z","CdnType":"web","GmtCreated":"2016-03-03T01:31:35Z","Cname":"adaf.zhilong.me.w.kunlunno.com","Sources":\{"Source":\[\{"Type":"oss","Content":"test2-mh.oss-cn-shenzhen.aliyuncs.com","Priority":"20","Port":80,"Weight":"10"\}\]\},"DomainStatus":"offline","Sandbox":""\}|The configuration of the resource. |
|Region|String|cn-hangzhou|The ID of the region where the resource resides. |
|ResourceCreationTime|Long|1456968695000|The timestamp when the resource was created. |
|ResourceDeleted|Integer|1|Indicates whether the resource is deleted. Valid values:

 -   1: The resource is not deleted.
-   0: The resource is deleted. |
|ResourceId|String|adaf.zhilon\*\*\*\*|The ID of the resource. |
|ResourceName|String|test-resource-name|The name of the resource. |
|ResourceStatus|String|offline|The status of the resource. The parameter value varies with the resource type and it may be left empty. Examples:

 -   When ResourceType is set to ACS::ECS::Instance, the resource is an Elastic Compute Service \(ECS\) instance and it has a specific status. In this case, valid values of this parameter include Running and Stopped.
-   When ResourceType is set to ACS::OSS::Bucket, the resource is an Object Storage Service \(OSS\) bucket and it does not have a specific status. In this case, this parameter is left empty. |
|ResourceType|String|ACS::CDN::Domain|The type of the resource. |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|The tags of the resource. |
|RequestId|String|E4D71ACE-6B0A-46E0-8352-56952378CC7F|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeDiscoveredResource
&Region=cn-hangzhou
&ResourceId=adaf.zhilon****
&ResourceType=ACS::CDN::Domain
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDiscoveredResourceResponse>
      <RequestId>E4D71ACE-6B0A-46E0-8352-56952378CC7F</RequestId>    
      <DiscoveredResourceDetail>
            <accountId>100931896542****</accountId>
            <resourceId>adaf.zhilon****</resourceId>
            <resourceStatus>offline</resourceStatus>
            <configuration>{"Description":"","SslProtocol":"off","DomainName":"adaf.zhilong.me","GmtModified":"2019-04-10T03:11Z","CdnType":"web","GmtCreated":"2016-03-03T01:31:35Z","Cname":"adaf.zhilong.me.w.kunlunno.com","Sources":{"Source":[{"Type":"oss","Content":"test2-mh.oss-cn-shenzhen.aliyuncs.com","Priority":"20","Port":80,"Weight":"10"}]},"DomainStatus":"offline","Sandbox":""}</configuration>
            <resourceDeleted>1</resourceDeleted>
            <resourceName>test-resource-name</resourceName>
            <region>cn-hangzhou</region>
            <availabilityZone>cn-hangzhou-h</availabilityZone>
            <resourceCreationTime>1456968695000</resourceCreationTime>
            <tags></tags>
            <resourceType>ACS::CDN::Domain</resourceType>
      </DiscoveredResourceDetail>
</DescribeDiscoveredResourceResponse>
```

`JSON` format

```
{
  "RequestId": "E4D71ACE-6B0A-46E0-8352-56952378CC7F",
  "DiscoveredResourceDetail": {
    "accountId": "100931896542****",
    "resourceId": "adaf.zhilon****",
    "resourceStatus": "offline",
    "configuration": "{\"Description\":\"\",\"SslProtocol\":\"off\",\"DomainName\":\"adaf.zhilong.me\",\"GmtModified\":\"2019-04-10T03:11Z\",\"CdnType\":\"web\",\"GmtCreated\":\"2016-03-03T01:31:35Z\",\"Cname\":\"adaf.zhilong.me.w.kunlunno.com\",\"Sources\":{\"Source\":[{\"Type\":\"oss\",\"Content\":\"test2-mh.oss-cn-shenzhen.aliyuncs.com\",\"Priority\":\"20\",\"Port\":80,\"Weight\":\"10\"}]},\"DomainStatus\":\"offline\",\"Sandbox\":\"\"}",
    "resourceDeleted": 1,
    "resourceName": "test-resource-name",
    "region": "cn-hangzhou",
    "availabilityZone": "cn-hangzhou-h",
    "resourceCreationTime": 1456968695000,
    "tags": "",
    "resourceType": "ACS::CDN::Domain"
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

