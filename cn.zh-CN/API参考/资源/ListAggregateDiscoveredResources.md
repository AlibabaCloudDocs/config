# ListAggregateDiscoveredResources

调用ListAggregateDiscoveredResources接口查询指定账号组内的资源列表。

本文将提供一个示例，查询账号组`ca-c560626622af0005****`内的资源列表。返回结果显示资源列表中的所有资源，共8个。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListAggregateDiscoveredResources&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAggregateDiscoveredResources|要执行的操作，取值：**ListAggregateDiscoveredResources**。 |
|ResourceId|String|否|s-hp3d9r78m7uysiii\*\*\*\*|资源ID。 |
|ResourceDeleted|Integer|否|1|资源状态。取值：

 -   0：已删除。
-   1：保有中。 |
|PageSize|Integer|是|10|分页时每页显示的数据行数。

 取值范围：1~100。起始值：1。默认值：10。 |
|PageNumber|Integer|是|1|页码。

 起始值：1。默认值：1。 |
|ResourceTypes|String|否|ACS::ECS::Snapshot|资源类型。多个资源类型之间用半角逗号（,）分隔。 |
|Regions|String|否|cn-huhehaote|资源归属的地域ID。多个地域ID之间用半角逗号（,）分隔。

 关于如何获取资源所在地域ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|ComplianceType|String|否|COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|AggregatorId|String|是|ca-c560626622af0005\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|ResourceOwnerId|Long|否|161259599160\*\*\*\*|资源拥有者的阿里云账号ID。 |

关于公共请求参数的详情，请参见[公共参数](~~169575~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DiscoveredResourceProfiles|Object| |资源列表。 |
|DiscoveredResourceProfileList|Array of DiscoveredResourceProfile| |资源列表详情。 |
|ResourceType|String|ACS::ECS::Snapshot|资源类型。 |
|Region|String|cn-huhehaote|地域ID。 |
|ResourceCreationTime|Long|1618675206000|资源创建时间戳。单位：毫秒。 |
|Tags|String|\{\\"key1\\":\[\\"value2\\"\],\\"key3\\":\[\\"value4\\"\]\}|资源标签。 |
|AccountId|Long|161259599160\*\*\*\*|资源拥有者的阿里云账号ID。 |
|ResourceId|String|s-hp3d9r78m7uysiii\*\*\*\*|资源ID。 |
|ResourceName|String|auto2.0\_20210418\_sp-hp3e2kkt8ugld7ox\*\*\*\*|资源名称。 |
|ResourceDeleted|Integer|1|资源状态。取值：

 -   0：已删除。
-   1：保有中。 |
|ResourceStatus|String|Running|资源状态。资源的状态取决于各云服务对其的定义，该参数可能为空。例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |
|ResourceOwnerId|Long|161259599160\*\*\*\*|资源拥有者的阿里云账号ID。 |
|PageNumber|Integer|1|资源列表的页码。起始值：1。 |
|PageSize|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Integer|8|资源总数。 |
|RequestId|String|C7817373-78CB-4F9A-8AFA-E7A88E9D64A2|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAggregateDiscoveredResources
&PageSize=10
&PageNumber=1
&AggregatorId=ca-c560626622af0005****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAggregateDiscoveredResourcesResponse>
    <DiscoveredResourceProfiles>
        <DiscoveredResourceProfileList>
            <ResourceType>ACS::ECS::Snapshot</ResourceType>
            <Region>cn-huhehaote</Region>
            <ResourceCreationTime>1618675206000</ResourceCreationTime>
            <Tags>{\"key1\":[\"value2\"],\"key3\":[\"value4\"]}</Tags>
            <ResourceId>s-hp3d9r78m7uysiii****</ResourceId>
            <ResourceName>auto2.0_20210418_sp-hp3e2kkt8ugld7ox****</ResourceName>
            <ResourceDeleted>1</ResourceDeleted>
            <ResourceStatus>Running</ResourceStatus>
        </DiscoveredResourceProfileList>
        <PageNumber>1</PageNumber>
        <PageSize>10</PageSize>
        <TotalCount>8</TotalCount>
    </DiscoveredResourceProfiles>
    <RequestId>C7817373-78CB-4F9A-8AFA-E7A88E9D64A2</RequestId>
</ListAggregateDiscoveredResourcesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "DiscoveredResourceProfiles" : {
    "DiscoveredResourceProfileList" : [ {
      "ResourceType" : "ACS::ECS::Snapshot",
      "Region" : "cn-huhehaote",
      "ResourceCreationTime" : 1618675206000,
      "Tags" : "{\\\"key1\\\":[\\\"value2\\\"],\\\"key3\\\":[\\\"value4\\\"]}",
      "ResourceId" : "s-hp3d9r78m7uysiii****",
      "ResourceName" : "auto2.0_20210418_sp-hp3e2kkt8ugld7ox****",
      "ResourceDeleted" : 1,
      "ResourceStatus" : "Running"
    } ],
    "PageNumber" : 1,
    "PageSize" : 10,
    "TotalCount" : 8
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

