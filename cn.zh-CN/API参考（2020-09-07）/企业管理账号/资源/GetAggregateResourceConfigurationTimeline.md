# GetAggregateResourceConfigurationTimeline

调用GetAggregateResourceConfigurationTimeline接口查询指定账号组内指定资源的配置时间线。

本文将提供一个示例，查询账号组`ca-5885626622af0008****`内地域`cn-hangzhou`中资源`new-bucket`（存储空间）的配置时间线。返回结果显示，资源的配置时间线为`1624961112000`（北京时间：2021-06-29 18:05:12）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateResourceConfigurationTimeline&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateResourceConfigurationTimeline|要执行的操作，取值：**GetAggregateResourceConfigurationTimeline**。 |
|ResourceId|String|是|new-bucket|资源ID。

 关于如何获取资源ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|StartTime|Long|否|1623211156000|开始时间戳。默认查询发起调用前30天的时间。单位：毫秒。 |
|EndTime|Long|否|1625821156000|结束时间戳。默认查询发起调用时的时间。单位：毫秒。 |
|MaxResults|Integer|否|10|单次请求返回结果的最大条数。取值范围：1~100。 |
|ResourceType|String|是|ACS::OSS::Bucket|资源类型。

 关于如何获取资源类型，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|Region|String|是|cn-hangzhou|资源归属的地域ID。

 关于如何获取资源归属的地域ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|AggregatorId|String|是|ca-5885626622af0008\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|ResourceOwnerId|Long|否|100931896542\*\*\*\*|资源归属的阿里云账号ID。 |
|NextToken|String|否|IWBjqMYSy0is7zSMGu16\*\*\*\*|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB|请求ID。 |
|ResourceConfigurationTimeline|Object| |资源配置时间线。 |
|NextToken|String|IWBjqMYSy0is7zSMGu16\*\*\*\*|查询下一页使用的Token。 |
|MaxResults|Integer|10|单次请求返回结果的最大条数。 |
|ConfigurationList|Array of ConfigurationList| |资源配置时间线列表。 |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|资源标签。 |
|AccountId|Long|100931896542\*\*\*\*|资源归属的阿里云账号ID。 |
|ResourceEventType|String|DISCOVERED|资源变更事件的类型。取值：

 -   DISCOVERED：配置审计新发现的资源事件。
-   DISCOVERED\_REVISED：配置审计新发现的通过周期订正任务产生的资源事件。
-   MODIFY：修改资源事件。
-   MODIFY\_REVISED：通过周期订正任务产生的修改资源事件。
-   REMOVE：删除资源事件。

 **说明：**

-   配置审计为了保障资源完整，通过周期订正任务对数据进行周期性对齐，产生新发现资源事件，该事件发生的频率较低。
-   通过周期订正任务产生资源事件的时间为任务发现时间，该时间晚于资源的实际变更时间。 |
|AvailabilityZone|String|cn-hangzhou-h|可用区。 |
|ResourceType|String|ACS::OSS::Bucket|资源类型。 |
|ResourceCreateTime|String|1624961112000|创建资源的时间戳。单位：毫秒。 |
|Region|String|cn-hangzhou|地域ID。 |
|CaptureTime|String|1624961156000|记录资源变更快照的时间戳。单位：毫秒。 |
|ConfigurationDiff|String|\{\\"AccessControlList\\":\[null,\{\\"Grant\\":\\"private\\"\}\],\\"ServerSideEncryptionRule\\":\[null,\{\\"SSEAlgorithm\\":\\"None\\"\}\],\\"CreationDate\\":\[null,\\"2021-06-29T10:05:12.000Z\\"\],\\"Owner\\":\[null,\{\\"DisplayName\\":\\"100931896542\*\*\*\*\\",\\"ID\\":\\"100931896542\*\*\*\*\\"\}\],\\"BucketPolicy\\":\[null,\{\\"LogPrefix\\":\\"\\",\\"LogBucket\\":\\"\\"\}\],\\"StorageClass\\":\[null,\\"Standard\\"\],\\"ExtranetEndpoint\\":\[null,\\"oss-cn-hangzhou.aliyuncs.com\\"\],\\"DataRedundancyType\\":\[null,\\"LRS\\"\],\\"AllowEmptyReferer\\":\[null,\\"true\\"\],\\"IntranetEndpoint\\":\[null,\\"oss-cn-hangzhou-internal.aliyuncs.com\\"\],\\"Name\\":\[null,\\"new-bucket\\"\],\\"Location\\":\[null,\\"oss-cn-hangzhou\\"\]\}|触发本次评估的资源变更细节。 |
|ResourceId|String|new-bucket|资源ID。 |
|ResourceName|String|new-bucket|资源名称。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateResourceConfigurationTimeline
&ResourceId=new-bucket
&ResourceType=ACS::OSS::Bucket
&Region=cn-hangzhou
&AggregatorId=ca-5885626622af0008****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateResourceConfigurationTimelineResponse>
	<RequestId>ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB</RequestId>
	<ResourceConfigurationTimeline>
		<MaxResults>10</MaxResults>
		<ConfigurationList>
			<AccountId>100931896542****</AccountId>
			<ResourceName>new-bucket</ResourceName>
			<AvailabilityZone>cn-hangzhou-h</AvailabilityZone>
			<ResourceType>ACS::OSS::Bucket</ResourceType>
			<ResourceEventType>DISCOVERED</ResourceEventType>
			<ResourceCreateTime>1624961112000</ResourceCreateTime>
			<CaptureTime>1624961156000</CaptureTime>
			<ConfigurationDiff>{\"AccessControlList\":[null,{\"Grant\":\"private\"}],\"ServerSideEncryptionRule\":[null,{\"SSEAlgorithm\":\"None\"}],\"CreationDate\":[null,\"2021-06-29T10:05:12.000Z\"],\"Owner\":[null,{\"DisplayName\":\"100931896542****\",\"ID\":\"100931896542****\"}],\"BucketPolicy\":[null,{\"LogPrefix\":\"\",\"LogBucket\":\"\"}],\"StorageClass\":[null,\"Standard\"],\"ExtranetEndpoint\":[null,\"oss-cn-hangzhou.aliyuncs.com\"],\"DataRedundancyType\":[null,\"LRS\"],\"AllowEmptyReferer\":[null,\"true\"],\"IntranetEndpoint\":[null,\"oss-cn-hangzhou-internal.aliyuncs.com\"],\"Name\":[null,\"new-bucket\"],\"Location\":[null,\"oss-cn-hangzhou\"]}</ConfigurationDiff>
			<ResourceId>new-bucket</ResourceId>
			<Region>cn-hangzhou</Region>
			<Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
		</ConfigurationList>
	</ResourceConfigurationTimeline>
</GetAggregateResourceConfigurationTimelineResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB",
  "ResourceConfigurationTimeline" : {
    "MaxResults" : 10,
    "ConfigurationList" : [ {
      "AccountId" : "100931896542****",
      "ResourceName" : "new-bucket",
      "AvailabilityZone" : "cn-hangzhou-h",
      "ResourceType" : "ACS::OSS::Bucket",
      "ResourceEventType" : "DISCOVERED",
      "ResourceCreateTime" : 1624961112000,
      "CaptureTime" : 1624961156000,
      "ConfigurationDiff" : "{\"AccessControlList\":[null,{\"Grant\":\"private\"}],\"ServerSideEncryptionRule\":[null,{\"SSEAlgorithm\":\"None\"}],\"CreationDate\":[null,\"2021-06-29T10:05:12.000Z\"],\"Owner\":[null,{\"DisplayName\":\"100931896542****\",\"ID\":\"100931896542****\"}],\"BucketPolicy\":[null,{\"LogPrefix\":\"\",\"LogBucket\":\"\"}],\"StorageClass\":[null,\"Standard\"],\"ExtranetEndpoint\":[null,\"oss-cn-hangzhou.aliyuncs.com\"],\"DataRedundancyType\":[null,\"LRS\"],\"AllowEmptyReferer\":[null,\"true\"],\"IntranetEndpoint\":[null,\"oss-cn-hangzhou-internal.aliyuncs.com\"],\"Name\":[null,\"new-bucket\"],\"Location\":[null,\"oss-cn-hangzhou\"]}",
      "ResourceId" : "new-bucket",
      "Region" : "cn-hangzhou",
      "Tags" : "{\"\"hc\"\":[\"\"value2\"\"]}"
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|400|Invalid.ResourceOwnerId.Value|The specified ResourceOwnerId is invalid.|该账号不存在或不在目标账号组内。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

