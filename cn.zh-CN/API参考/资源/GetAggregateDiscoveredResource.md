# GetAggregateDiscoveredResource

调用GetAggregateDiscoveredResource接口查询指定账号组内指定资源详情。

本文将提供一个示例，查询账号组`ca-5885626622af0008****`内资源`new-bucket`的详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateDiscoveredResource&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateDiscoveredResource|要执行的操作，取值：**GetAggregateDiscoveredResource**。 |
|ResourceId|String|是|new-bucket|资源ID。

 关于如何获取资源ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|ResourceType|String|是|ACS::OSS::Bucket|资源类型。

 关于如何获取资源类型，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|Region|String|是|cn-hangzhou|资源所在地域ID。

 关于如何获取资源所在地域ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|AggregatorId|String|是|ca-5885626622af0008\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|ResourceOwnerId|Long|是|100931896542\*\*\*\*|资源归属的阿里云账号ID。 |

关于公共请求参数的详情，请参见[公共参数](~~169575~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E4D71ACE-6B0A-46E0-8352-56952378CC7F|请求ID。 |
|DiscoveredResourceDetail|Object| |资源详情。 |
|AvailabilityZone|String|cn-hangzhou-h|资源可用区。 |
|ResourceType|String|ACS::OSS::BucketACS::CDN::Domain|资源类型。 |
|Configuration|String|\{\\"AccessControlList\\":\{\\"Grant\\":\\"private\\"\},\\"ServerSideEncryptionRule\\":\{\\"SSEAlgorithm\\":\\"None\\"\},\\"Comment\\":\\"\\",\\"CreationDate\\":\\"2021-06-29T10:05:12.000Z\\",\\"Owner\\":\{\\"DisplayName\\":\\"100931896542\*\*\*\*\\",\\"ID\\":\\"100931896542\*\*\*\*\\"\},\\"StorageClass\\":\\"Standard\\",\\"DataRedundancyType\\":\\"LRS\\",\\"AllowEmptyReferer\\":\\"true\\",\\"Name\\":\\"new-bucket\\",\\"BucketPolicy\\":\{\\"LogPrefix\\":\\"\\",\\"LogBucket\\":\\"\\"\},\\"ExtranetEndpoint\\":\\"oss-cn-hangzhou.aliyuncs.com\\",\\"IntranetEndpoint\\":\\"oss-cn-hangzhou-internal.aliyuncs.com\\",\\"Location\\":\\"oss-cn-hangzhou\\"\}|资源的完整配置信息。 |
|Region|String|cn-hangzhou|地域ID。 |
|ResourceCreationTime|Long|1624961112000|资源创建时间戳。 |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|资源标签。 |
|AccountId|Long|100931896542\*\*\*\*|资源拥有者的阿里云账号ID。 |
|ResourceId|String|new-bucket|资源ID。 |
|ResourceDeleted|Integer|1|资源删除状态。取值：

 -   1：未删除。
-   0：已删除。 |
|ResourceName|String|new-bucket|资源名称。 |
|ResourceStatus|String|offline|资源状态。资源的状态取决于各云服务对其的定义，该参数可能为空。例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateDiscoveredResource
&ResourceId=new-bucket
&ResourceType=ACS::OSS::Bucket
&Region=cn-hangzhou
&AggregatorId=ca-5885626622af0008****
&ResourceOwnerId=100931896542****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateDiscoveredResourceResponse>
	<RequestId>E4D71ACE-6B0A-46E0-8352-56952378CC7F</RequestId>
	<DiscoveredResourceDetail>
		<AccountId>100931896542****</AccountId>
		<ResourceCreationTime>1624961112000</ResourceCreationTime>
		<Configuration>{\"AccessControlList\":{\"Grant\":\"private\"},\"ServerSideEncryptionRule\":{\"SSEAlgorithm\":\"None\"},\"Comment\":\"\",\"CreationDate\":\"2021-06-29T10:05:12.000Z\",\"Owner\":{\"DisplayName\":\"100931896542****\",\"ID\":\"100931896542****\"},\"StorageClass\":\"Standard\",\"DataRedundancyType\":\"LRS\",\"AllowEmptyReferer\":\"true\",\"Name\":\"new-bucket\",\"BucketPolicy\":{\"LogPrefix\":\"\",\"LogBucket\":\"\"},\"ExtranetEndpoint\":\"oss-cn-hangzhou.aliyuncs.com\",\"IntranetEndpoint\":\"oss-cn-hangzhou-internal.aliyuncs.com\",\"Location\":\"oss-cn-hangzhou\"}</Configuration>
		<ResourceId>new-bucket</ResourceId>
		<ResourceName>new-bucket</ResourceName>
		<Region>cn-hangzhou</Region>
		<AvailabilityZone>cn-hangzhou-h</AvailabilityZone>
		<ResourceStatus></ResourceStatus>
		<ResourceType>ACS::OSS::Bucket</ResourceType>
		<ResourceDeleted>1</ResourceDeleted>
		<Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
	</DiscoveredResourceDetail>
</GetAggregateDiscoveredResourceResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "E4D71ACE-6B0A-46E0-8352-56952378CC7F",
  "DiscoveredResourceDetail" : {
    "AccountId" : "100931896542****",
    "ResourceCreationTime" : 1624961112000,
    "Configuration" : "{\"AccessControlList\":{\"Grant\":\"private\"},\"ServerSideEncryptionRule\":{\"SSEAlgorithm\":\"None\"},\"Comment\":\"\",\"CreationDate\":\"2021-06-29T10:05:12.000Z\",\"Owner\":{\"DisplayName\":\"100931896542****\",\"ID\":\"100931896542****\"},\"StorageClass\":\"Standard\",\"DataRedundancyType\":\"LRS\",\"AllowEmptyReferer\":\"true\",\"Name\":\"new-bucket\",\"BucketPolicy\":{\"LogPrefix\":\"\",\"LogBucket\":\"\"},\"ExtranetEndpoint\":\"oss-cn-hangzhou.aliyuncs.com\",\"IntranetEndpoint\":\"oss-cn-hangzhou-internal.aliyuncs.com\",\"Location\":\"oss-cn-hangzhou\"}",
    "ResourceId" : "new-bucket",
    "ResourceName" : "new-bucket",
    "Region" : "cn-hangzhou",
    "AvailabilityZone" : "cn-hangzhou-h",
    "ResourceStatus" : "",
    "ResourceType" : "ACS::OSS::Bucket",
    "ResourceDeleted" : 1,
    "Tags" : "{\"\"hc\"\":[\"\"value2\"\"]}"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|该成员账号不属于您所在的资源目录。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

