# ListDiscoveredResources

调用ListDiscoveredResources接口查询资源列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListDiscoveredResources&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListDiscoveredResources|要执行的操作，取值：**ListDiscoveredResources**。 |
|ResourceId|String|否|s-hp3d9r78m7uysiii\*\*\*\*|资源ID。 |
|ResourceDeleted|Integer|否|1|资源删除状态。取值：

 -   1：未删除。
-   0：已删除。 |
|PageSize|Integer|是|1|分页查询时设置的每页行数。取值范围：1~100。 |
|PageNumber|Integer|是|10|资源列表的页码。起始值：1。 |
|ResourceTypes|String|否|ACS::ECS::Snapshot|资源类型。多个资源类型用半角逗号（,）分隔。 |
|Regions|String|否|cn-huhehaote|地域。多个地域用半角逗号（,）分隔。 |
|ComplianceType|String|否|COMPLIANT|资源合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DiscoveredResourceProfiles|Object| |资源列表结果。 |
|DiscoveredResourceProfileList|Array of DiscoveredResourceProfile| |资源列表。 |
|ResourceType|String|ACS::ECS::Snapshot|资源类型。 |
|Region|String|cn-huhehaote|地域ID。 |
|ResourceCreationTime|Long|1618675206000|资源创建时间戳。 |
|Tags|String|\{\\"key1\\":\[\\"value2\\"\],\\"key3\\":\[\\"value4\\"\]\}|资源标签。 |
|AccountId|Long|987654321|阿里云账号ID。 |
|ResourceId|String|s-hp3d9r78m7uysiii\*\*\*\*|资源ID。 |
|ResourceName|String|auto2.0\_20210418\_sp-hp3e2kkt8ugld7ox\*\*\*\*|资源名称。 |
|ResourceDeleted|Integer|1|资源删除状态。取值：

 -   1：未删除。
-   0：已删除。 |
|ResourceStatus|String|accomplished|资源状态。资源的状态取决于各云服务对其的定义，该参数可能为空。

 例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |
|PageNumber|Integer|10|资源列表的页码。起始值：1。 |
|PageSize|Integer|1|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Integer|129|资源总数。 |
|RequestId|String|C7817373-78CB-4F9A-8AFA-E7A88E9D64A2|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListDiscoveredResources
&PageNumber=10
&PageSize=1
&<公共请求参数>
```

正常返回示例

`XML`格式

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

`JSON`格式

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

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|该成员账号不属于您所在的资源目录。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

