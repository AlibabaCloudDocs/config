# GetResourceComplianceTimeline

调用GetResourceComplianceTimeline接口查询资源合规时间线。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceComplianceTimeline&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceComplianceTimeline|要执行的操作，取值：**GetResourceComplianceTimeline**。 |
|ResourceType|String|是|ACS::ECS::Instance|资源类型。 |
|ResourceId|String|是|i-uf6072y75i2cevjq\*\*\*\*|资源ID。 |
|StartTime|Long|否|1593599340010|开始时间戳。默认为发起调用前的30天。 |
|EndTime|Long|否|1593599342230|结束时间戳。默认为发起调用时的时间。 |
|Limit|Integer|否|10|分页查询时设置的每页行数。取值范围：1~100。默认值：10。 |
|MultiAccount|Boolean|否|true|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|String|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|Region|String|是|cn-hangzhou|地域ID。 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DE9FFFE5-FCAD-4B24-9546-BF49273C562B|请求ID。 |
|ResourceComplianceTimeline|Object| |资源合规时间线。 |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|下一个查询开始的Token。 |
|Limit|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|ComplianceList|Array of ComplianceList| |资源合规时间线列表。 |
|Tags|String|\{\\"project\\":\[\\"efg\\"\]\}|资源标签。 |
|AccountId|String|120390217529\*\*\*\*|阿里云账号ID。 |
|AvailabilityZone|String|cn-hangzhou-f|资源可用区。 |
|ResourceType|String|ACS::ECS::Instance|资源类型。 |
|ResourceCreateTime|Long|1203902175293610|资源创建时间戳。 |
|Region|String|cn-hangzhou|地域ID。 |
|Configuration|String|\{\\"managetest-required-tags\\":\[\{\},\{\\"configRuleId\\":\\"cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleName\\":\\"managetest-required-tags\\",\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"riskLevel\\":1,\\"annotation\\":\\"\{\\\\\\"desiredValue\\\\\\":\\\\\\"key1\\\\\\",\\\\\\"reason\\\\\\":\\\\\\"No tag with name key1\\\\\\"\}\\",\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|资源关联的规则列表和规则合规详情。 |
|CaptureTime|Long|1203902175292305|合规评估时间戳。 |
|ConfigurationDiff|String|\{\\"Compliance\\":\{\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"count\\":2\},\\"ConfigRuleList\\":\[\{\\"configRuleId\\":\\"cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleName\\":\\"required-tags\\",\\"complianceType\\":\\"COMPLIANT\\",\\"riskLevel\\":1,\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|合规状态发生变化的规则详情。 |
|ResourceId|String|i-uf6072y75i2cevjq\*\*\*\*|资源ID。 |
|ResourceName|String|test-resource|资源名称。 |
|ResourceStatus|String|Running|资源状态。资源状态取决于各云服务对其的定义，该参数可能为空。例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |
|TotalCount|Long|100|历史合规结果总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetResourceComplianceTimeline
&Region=cn-hangzhou
&ResourceId=i-uf6072y75i2cevjq****
&ResourceType=ACS::ECS::Instance
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ResourceComplianceTimelineResponse>
    <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
    <ComplianceList>
        <AccountId>120390217529****</AccountId>
        <CaptureTime>1203902175292305</CaptureTime>
        <ConfigurationDiff>{\"Compliance\":{\"complianceType\":\"NON_COMPLIANT\",\"count\":2},\"ConfigRuleList\":[{\"configRuleId\":\"cr-7b6e5180a8d100cc****\",\"configRuleArn\":\"acs:config::120390217529****:config-rule/cr-7b6e5180a8d100cc****\",\"configRuleName\":\"required-tags\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"invokingEventMessageType\":\"ConfigurationItemChangeNotification\"}]}</ConfigurationDiff>
        <Configuration>{\"managetest-required-tags\":[{},{\"configRuleId\":\"cr-656d5180a8d1009c****\",\"configRuleArn\":\"acs:config::120390217529****:config-rule/cr-656d5180a8d1009c****\",\"configRuleName\":\"managetest-required-tags\",\"complianceType\":\"NON_COMPLIANT\",\"riskLevel\":1,\"annotation\":\"{\\\"desiredValue\\\":\\\"key1\\\",\\\"reason\\\":\\\"No tag with name key1\\\"}\",\"invokingEventMessageType\":\"ConfigurationItemChangeNotification\"}]}</Configuration>
        <ResourceId>i-uf6072y75i2cevjq****</ResourceId>
        <ResourceName>test-resource</ResourceName>
        <AvailabilityZone>cn-hangzhou-f</AvailabilityZone>
        <Region>cn-hangzhou</Region>
        <ResourceStatus>Running</ResourceStatus>
        <ResourceType>ACS::ECS::Instance</ResourceType>
        <ResourceCreateTime>1203902175293610</ResourceCreateTime>
        <Tags>{\"project\":[\"efg\"]}</Tags>
    </ComplianceList>
    <Limit>10</Limit>
    <RequestId>DE9FFFE5-FCAD-4B24-9546-BF49273C562B</RequestId>
</ResourceComplianceTimelineResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ResourceComplianceTimeline" : {
    "NextToken" : "caeba0bbb2be03f84eb48b699f0a****",
    "ComplianceList" : [ {
      "AccountId" : "120390217529****",
      "CaptureTime" : "1203902175292305",
      "ConfigurationDiff" : "{\\\"Compliance\\\":{\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"count\\\":2},\\\"ConfigRuleList\\\":[{\\\"configRuleId\\\":\\\"cr-7b6e5180a8d100cc****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-7b6e5180a8d100cc****\\\",\\\"configRuleName\\\":\\\"required-tags\\\",\\\"complianceType\\\":\\\"COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
      "Configuration" : "{\\\"managetest-required-tags\\\":[{},{\\\"configRuleId\\\":\\\"cr-656d5180a8d1009c****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-656d5180a8d1009c****\\\",\\\"configRuleName\\\":\\\"managetest-required-tags\\\",\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"annotation\\\":\\\"{\\\\\\\"desiredValue\\\\\\\":\\\\\\\"key1\\\\\\\",\\\\\\\"reason\\\\\\\":\\\\\\\"No tag with name key1\\\\\\\"}\\\",\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
      "ResourceId" : "i-uf6072y75i2cevjq****",
      "ResourceName" : "test-resource",
      "AvailabilityZone" : "cn-hangzhou-f",
      "Region" : "cn-hangzhou",
      "ResourceStatus" : "Running",
      "ResourceType" : "ACS::ECS::Instance",
      "ResourceCreateTime" : "1203902175293610",
      "Tags" : "{\\\"project\\\":[\\\"efg\\\"]}"
    } ],
    "Limit" : 10
  },
  "RequestId" : "DE9FFFE5-FCAD-4B24-9546-BF49273C562B"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

