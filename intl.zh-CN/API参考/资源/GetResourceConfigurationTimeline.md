# GetResourceConfigurationTimeline

调用GetResourceConfigurationTimeline接口查询资源配置历史记录。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceConfigurationTimeline&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceConfigurationTimeline|要执行的操作，取值：GetResourceConfigurationTimeline。 |
|Region|String|是|cn-hangzhou|地域ID。 |
|ResourceId|String|是|i-bp19xem7lt97h973\*\*\*\*|资源ID。 |
|ResourceType|String|是|ACS::ECS::Instance|资源类型。 |
|StartTime|Long|否|1588852773|开始时间戳。默认查询发起调用前30天的时间。 |
|EndTime|Long|否|1588852780|结束时间戳。默认查询发起调用时的时间。 |
|Limit|Integer|否|10|分页查询时设置的每页行数。取值范围：1~100。默认值：10。 |
|MultiAccount|Boolean|否|true|企业管理账号是否查询成员账号的资源配置历史记录。取值：

 -   true：是。企业管理账号查询资源目录中指定成员账号的指定资源的配置历史记录。
-   false（默认值）：否。企业管理账号查询当前账号的指定资源的配置历史记录。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |
|MemberId|Long|否|123456789|待查询资源归属的成员账号ID。默认为空。当MultiAccount设置为true时，该参数有效。

 -   当MemberId为空时，查询企业管理账号和所有成员账号的指定资源的配置历史记录。
-   当MemberId不为空时，查询指定成员账号的指定资源的配置历史记录。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB|请求ID。 |
|ResourceConfigurationTimeline|Struct| |资源配置历史记录。 |
|ConfigurationList|Array of ConfigurationList| |资源配置历史记录列表。 |
|AccountId|Long|123456789|阿里云账号ID。 |
|AvailabilityZone|String|cn-hangzhou-h|可用区。 |
|CaptureTime|String|123456789000000|配置变更时间戳。 |
|ConfigurationDiff|String|\{\\"ExpiredTime\\":\[\\"2020-10-26T16:00Z\\",\\"2020-11-26T16:00Z\\"\]\}|配置资源关系变更信息。 |
|Region|String|cn-hangzhou|地域ID。 |
|Relationship|String|\{\}|资源关系。 |
|RelationshipDiff|String|\{\}|资源关系变更信息。 |
|ResourceCreateTime|String|123456789000000|资源创建时间。 |
|ResourceId|String|i-bp19xem7lt97h973\*\*\*\*|资源ID。 |
|ResourceName|String|test-name|资源名称。 |
|ResourceType|String|ACS::ECS::Instance|资源类型。 |
|Tags|String|"\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}"|资源标签。 |
|Limit|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |
|TotalCount|Long|100|资源配置历史记录总数。 |

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

`XML` 格式

```
<GetResourceConfigurationTimelineResponse>
		  <RequestId>ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB</RequestId>
		  <ResourceConfigurationTimeline>
			    <ConfigurationList>
				      <Relationships></Relationships>
				      <AccountId>100931896542****</AccountId>
				      <ResourceCreateTime>12344556777888</ResourceCreateTime>
				      <CaptureTime>12344556777888</CaptureTime>
				      <ConfigurationDiff>{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}</ConfigurationDiff>
				      <ResourceId>i-bp19xem7lt97h973****</ResourceId>
				      <ResourceName>ECS-test</ResourceName>
				      <Region>cn-hangzhou</Region>
				      <AvailabilityZone>cn-hangzhou-h</AvailabilityZone>
				      <ResourceType>ACS::ECS::Instance</ResourceType>
				      <RelationshipsDiff></RelationshipsDiff>
				      <Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
			    </ConfigurationList>
			    <Limit>10</Limit>
			    <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
		  </ResourceConfigurationTimeline>
</GetResourceConfigurationTimelineResponse>
```

`JSON` 格式

```
{
  "RequestId": "ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB",  
  "ResourceConfigurationTimeline": {
    "ConfigurationList": [
      {
        "Relationships": "",
        "AccountId": "100931896542****",
        "ResourceCreateTime": "12344556777888",
        "CaptureTime":"12344556777888",
        "ConfigurationDiff": "{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}",
        "ResourceId": "i-bp19xem7lt97h973****",
        "ResourceName": "ECS-test",
        "Region": "cn-hangzhou",
        "AvailabilityZone": "cn-hangzhou-h",
        "ResourceType": "ACS::ECS::Instance",
        "RelationshipsDiff": "",
        "Tags": "{\"\"hc\"\":[\"\"value2\"\"]}"
      }
    ],
    "Limit": 10,
    "NextToken": "caeba0bbb2be03f84eb48b699f0a****"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|该成员账号不属于您所在的资源目录。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

