# GetResourceConfigurationTimeline

调用GetResourceConfigurationTimeline接口查询资源配置时间线。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceConfigurationTimeline&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceConfigurationTimeline|要执行的操作，取值：**GetResourceConfigurationTimeline**。 |
|ResourceId|String|是|i-bp19xem7lt97h973\*\*\*\*|资源ID。 |
|StartTime|Long|否|1605489195000|开始时间戳。默认为发起调用前的30天。 |
|EndTime|Long|否|1605489235000|结束时间戳。默认为发起调用时的时间。 |
|Limit|Integer|否|10|分页查询时设置的每页行数。取值范围：1~100。默认值：10。 |
|ResourceType|String|是|ACS::ECS::Instance|资源类型。 |
|Region|String|是|cn-hangzhou|地域ID。 |
|MultiAccount|Boolean|否|true|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB|请求ID。 |
|ResourceConfigurationTimeline|Object| |资源配置时间线。 |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |
|Limit|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|ConfigurationList|Array of ConfigurationList| |资源配置时间线列表。 |
|Tags|String|"\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}"|资源标签。 |
|AccountId|Long|987654321|阿里云账号ID。 |
|ResourceEventType|String|DISCOVERED|资源变更事件的类型。取值：

 -   DISCOVERED：新增资源事件。
-   MODIFY：修改资源事件。
-   REMOVE：删除资源事件。 |
|AvailabilityZone|String|cn-hangzhou-h|可用区。 |
|ResourceType|String|ACS::ECS::Instance|资源类型。 |
|ResourceCreateTime|String|1605237751000|资源创建时间。 |
|Region|String|cn-hangzhou|地域ID。 |
|CaptureTime|String|1605316711000|配置变更时间戳。 |
|ConfigurationDiff|String|\{\\"ExpiredTime\\":\[\\"2020-10-26T16:00Z\\",\\"2020-11-26T16:00Z\\"\]\}|配置资源关系变更信息。 |
|ResourceId|String|i-bp19xem7lt97h973\*\*\*\*|资源ID。 |
|ResourceName|String|ECS-test|资源名称。 |
|TotalCount|Long|100|资源配置时间线总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetResourceConfigurationTimeline
&Region=cn-hangzhou
&ResourceId=i-bp19xem7lt97h973****
&ResourceType=ACS::ECS::Instance
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetResourceConfigurationTimelineResponse>
		<RequestId>ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB</RequestId>
		<ResourceConfigurationTimeline>
			<ConfigurationList>
				<AccountId>987654321</AccountId>
				<ResourceCreateTime>1605237751000</ResourceCreateTime>
				<resourceEventType>DISCOVERED</resourceEventType>
                <CaptureTime>1605316711000</CaptureTime>
				<ConfigurationDiff>{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}</ConfigurationDiff>
				<ResourceId>i-bp19xem7lt97h973****</ResourceId>
				<ResourceName>ECS-test</ResourceName>
				<Region>cn-hangzhou</Region>
				<AvailabilityZone>cn-hangzhou-h</AvailabilityZone>
				<ResourceType>ACS::ECS::Instance</ResourceType>
				<Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
			</ConfigurationList>
			<Limit>10</Limit>
			<NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
		</ResourceConfigurationTimeline>
</GetResourceConfigurationTimelineResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB",
  "ResourceConfigurationTimeline" : {
    "ConfigurationList" : [ {
      "AccountId" : "987654321",
      "ResourceCreateTime" : "1605237751000",
      "resourceEventType" : "DISCOVERED",
      "CaptureTime" : "1605316711000",
      "ConfigurationDiff" : "{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}",
      "ResourceId" : "i-bp19xem7lt97h973****",
      "ResourceName" : "ECS-test",
      "Region" : "cn-hangzhou",
      "AvailabilityZone" : "cn-hangzhou-h",
      "ResourceType" : "ACS::ECS::Instance",
      "Tags" : "{\"\"hc\"\":[\"\"value2\"\"]}"
    } ],
    "Limit" : 10,
    "NextToken" : "caeba0bbb2be03f84eb48b699f0a****"
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

