# GetDiscoveredResourceSummary

调用GetDiscoveredResourceSummary接口查询资源概览。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetDiscoveredResourceSummary&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetDiscoveredResourceSummary|要执行的操作，取值：**GetDiscoveredResourceSummary**。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DiscoveredResourceSummary|Object| |资源概览。 |
|RegionCount|Integer|6|覆盖地域数量。 |
|ResourceCount|Integer|7|监控中的资源数量。 |
|ResourceTypeCount|Integer|45|监控中的资源类型数量。 |
|RequestId|String|2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetDiscoveredResourceSummary
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetDiscoveredResourceSummaryResponse>
    <DiscoveredResourceSummary>
        <ResourceTypeCount>45</ResourceTypeCount>
        <ResourceCount>7</ResourceCount>
        <RegionCount>6</RegionCount>
    </DiscoveredResourceSummary>
    <RequestId>2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C</RequestId>
</GetDiscoveredResourceSummaryResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "DiscoveredResourceSummary" : {
    "ResourceTypeCount" : "45",
    "ResourceCount" : "7",
    "RegionCount" : "6"
  },
  "RequestId" : "2A8FA4FB-2E08-4D28-8F83-1A8A3EC80B1C"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|该成员账号不属于您所在的资源目录。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

