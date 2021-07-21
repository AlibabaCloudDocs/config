# GetDiscoveredResourceCountsGroupByRegion

调用GetDiscoveredResourceCountsGroupByRegion接口从地域维度查询资源的统计结果。

本文将提供一个示例，从地域维度查询资源的统计结果。返回结果显示地域`cn-hangzhou`中资源总数为10条。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceCountsGroupByRegion&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetDiscoveredResourceCountsGroupByRegion|要执行的操作，取值：**GetDiscoveredResourceCountsGroupByRegion**。 |
|ResourceType|String|否|ACS::ECS::Instance|资源类型。

 关于如何获取资源类型，请参见[ListDiscoveredResources](~~169620~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|399BD94C-D20C-4D27-88D4-89E8D75C0595|请求ID。 |
|DiscoveredResourceCountsSummary|Array of GroupedResourceCount| |资源统计结果。 |
|ResourceCount|Long|10|资源总数量。 |
|Region|String|cn-hangzhou|用于分组统计的地域。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetDiscoveredResourceCountsGroupByRegion
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetDiscoveredResourceCountsGroupByRegionResponse>
    <RequestId>399BD94C-D20C-4D27-88D4-89E8D75C0595</RequestId>
    <DiscoveredResourceCountsSummary>
        <ResourceCount>10</ResourceCount>
        <Region>cn-hangzhou</Region>
    </DiscoveredResourceCountsSummary>
</GetDiscoveredResourceCountsGroupByRegionResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "399BD94C-D20C-4D27-88D4-89E8D75C0595",
  "DiscoveredResourceCountsSummary" : [ {
    "ResourceCount" : 10,
    "Region" : "cn-hangzhou"
  } ]
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

