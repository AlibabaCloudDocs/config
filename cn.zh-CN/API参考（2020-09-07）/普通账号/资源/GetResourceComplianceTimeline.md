# GetResourceComplianceTimeline

调用GetResourceComplianceTimeline接口查询指定资源的合规时间线。

本文将提供一个示例，查询地域`cn-hangzhou`中资源`new-bucket`（存储空间）的合规时间线。返回结果显示，资源的合规时间线为`1625200295276`（北京时间：2021-07-02 12:31:35）和`1625200228510`（北京时间：2021-07-02 12:30:28）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceComplianceTimeline&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceComplianceTimeline|要执行的操作，取值：**GetResourceComplianceTimeline**。 |
|ResourceType|String|是|ACS::OSS::Bucket|资源类型。

 关于如何获取类型，请参见[ListDiscoveredResources](~~169620~~)。 |
|ResourceId|String|是|new-bucket|资源ID。

 关于如何获取资源ID，请参见[ListDiscoveredResources](~~169620~~)。 |
|StartTime|Long|否|1623211156000|开始时间戳。默认查询发起调用前30天的时间。单位：毫秒。 |
|EndTime|Long|否|1625821156000|结束时间戳。默认查询发起调用时的时间。单位：毫秒。 |
|MaxResults|Integer|否|10|单次请求返回结果的最大条数。取值范围：1~100。 |
|Region|String|是|cn-hangzhou|地域ID。 |
|NextToken|String|否|IWBjqMYSy0is7zSMGu16\*\*\*\*|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8D53A78F-1EB8-4264-A554-72F07E34FAE6|请求ID。 |
|ResourceComplianceTimeline|Object| |资源合规时间线。 |
|NextToken|String|5OVS5J4I1/UKTkHV5oNs\*\*\*\*|查询下一页使用的Token。 |
|MaxResults|Integer|10|单次请求返回结果的最大条数。 |
|ComplianceList|Array of ComplianceList| |资源合规时间线列表。 |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|资源标签。 |
|AccountId|String|100931896542\*\*\*\*|资源归属的阿里云账号ID。 |
|AvailabilityZone|String|cn-hangzhou-f|资源可用区。 |
|ResourceType|String|ACS::OSS::Bucket|资源类型。 |
|ResourceCreateTime|Long|1624961112000|创建资源的时间戳。单位：毫秒。 |
|Region|String|cn-hangzhou|地域ID。 |
|Configuration|String|\{\\"Compliance\\":\{\\"complianceType\\":\\"COMPLIANT\\",\\"count\\":1\},\\"ConfigRuleList\\":\[\{\\"accountId\\":100931896542\*\*\*\*,\\"configRuleId\\":\\"cr-9524626622af003d\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::100931896542\*\*\*\*:rule/cr-9524626622af003d\*\*\*\*\\",\\"configRuleName\\":\\"OSS存储空间ACL禁止公共读写\\",\\"complianceType\\":\\"COMPLIANT\\",\\"riskLevel\\":1,\\"annotation\\":\\"\\",\\"invokingEventMessageType\\":\\"ScheduledNotification\\"\}\]\}|资源关联的规则列表和规则合规详情。 |
|CaptureTime|Long|1625200295276|记录资源合规评估的时间戳。单位：毫秒。 |
|ConfigurationDiff|String|\{\\"OSS存储空间ACL禁止公共读写\\":\[\{\\"accountId\\":100931896542\*\*\*\*,\\"configRuleId\\":\\"cr-965f626622af003d\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::100931896542\*\*\*\*:rule/cr-965f626622af003d\*\*\*\*\\",\\"configRuleName\\":\\"OSS存储空间ACL禁止公共读写\\",\\"complianceType\\":\\"COMPLIANT\\",\\"riskLevel\\":1,\\"annotation\\":\\"\\",\\"invokingEventMessageType\\":\\"ScheduledNotification\\"\},\{\}\]\}|触发本次评估的资源变更细节。 |
|ResourceId|String|new-bucket|资源ID。 |
|ResourceName|String|new-bucket|资源名称。 |
|ResourceStatus|String|Running|资源状态。资源状态取决于各云服务对其的定义，该参数可能为空。例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetResourceComplianceTimeline
&ResourceType=ACS::OSS::Bucket
&ResourceId=new-bucket
&Region=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetResourceComplianceTimelineResponse>
	<RequestId>8D53A78F-1EB8-4264-A554-72F07E34FAE6</RequestId>
	<ResourceComplianceTimeline>
		<NextToken>5OVS5J4I1/UKTkHV5oNs****</NextToken>
		<ComplianceList>
			<AccountId>100931896542****</AccountId>
			<CaptureTime>1625200295276</CaptureTime>
			<ConfigurationDiff>{\"OSS存储空间ACL禁止公共读写\":[{\"accountId\":100931896542****,\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"annotation\":\"\",\"invokingEventMessageType\":\"ScheduledNotification\"},{}]}</ConfigurationDiff>
			<Configuration>{\"Compliance\":{\"complianceType\":\"COMPLIANT\",\"count\":1},\"ConfigRuleList\":[{\"accountId\":100931896542****,\"configRuleId\":\"cr-9524626622af003d****\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-9524626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"annotation\":\"\",\"invokingEventMessageType\":\"ScheduledNotification\"}]}</Configuration>
			<ResourceId>new-bucket</ResourceId>
			<ResourceName>new-bucket</ResourceName>
			<AvailabilityZone>cn-hangzhou-f</AvailabilityZone>
			<Region>cn-hangzhou</Region>
			<ResourceType>ACS::OSS::Bucket</ResourceType>
			<ResourceCreateTime>1624961112000</ResourceCreateTime>
			<Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
		</ComplianceList>
		<ComplianceList>
			<AccountId>100931896542****</AccountId>
			<CaptureTime>1625200228510</CaptureTime>
			<ConfigurationDiff>{\"OSS存储空间ACL禁止公共读写\":[{},{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1}]}</ConfigurationDiff>
			<Configuration>{\"Compliance\":{\"complianceType\":\"COMPLIANT\",\"count\":2},\"ConfigRuleList\":[{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-9524626622af003d****\",\"configRuleId\":\"cr-9524626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1},{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1}]}</Configuration>
			<ResourceId>new-bucket</ResourceId>
			<ResourceName>new-bucket</ResourceName>
			<AvailabilityZone>cn-hangzhou-f</AvailabilityZone>
			<Region>cn-hangzhou</Region>
			<ResourceType>ACS::OSS::Bucket</ResourceType>
			<ResourceCreateTime>1624961112000</ResourceCreateTime>
			<Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
		</ComplianceList>
		<MaxResults>10</MaxResults>
	</ResourceComplianceTimeline>
</GetResourceComplianceTimelineResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "8D53A78F-1EB8-4264-A554-72F07E34FAE6",
  "ResourceComplianceTimeline" : {
    "NextToken" : "5OVS5J4I1/UKTkHV5oNs****",
    "ComplianceList" : [ {
      "AccountId" : "100931896542****",
      "CaptureTime" : 1625200295276,
      "ConfigurationDiff" : "{\"OSS存储空间ACL禁止公共读写\":[{\"accountId\":100931896542****,\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"annotation\":\"\",\"invokingEventMessageType\":\"ScheduledNotification\"},{}]}",
      "Configuration" : "{\"Compliance\":{\"complianceType\":\"COMPLIANT\",\"count\":1},\"ConfigRuleList\":[{\"accountId\":100931896542****,\"configRuleId\":\"cr-9524626622af003d****\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-9524626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"annotation\":\"\",\"invokingEventMessageType\":\"ScheduledNotification\"}]}",
      "ResourceId" : "new-bucket",
      "ResourceName" : "new-bucket",
      "AvailabilityZone" : "cn-hangzhou-f",
      "Region" : "cn-hangzhou",
      "ResourceType" : "ACS::OSS::Bucket",
      "ResourceCreateTime" : 1624961112000,
      "Tags" : "{\"\"hc\"\":[\"\"value2\"\"]}"
    }, {
      "AccountId" : "100931896542****",
      "CaptureTime" : 1625200228510,
      "ConfigurationDiff" : "{\"OSS存储空间ACL禁止公共读写\":[{},{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1}]}",
      "Configuration" : "{\"Compliance\":{\"complianceType\":\"COMPLIANT\",\"count\":2},\"ConfigRuleList\":[{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-9524626622af003d****\",\"configRuleId\":\"cr-9524626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1},{\"annotation\":\"\",\"complianceType\":\"COMPLIANT\",\"configRuleArn\":\"acs:config::100931896542****:rule/cr-965f626622af003d****\",\"configRuleId\":\"cr-965f626622af003d****\",\"configRuleName\":\"OSS存储空间ACL禁止公共读写\",\"invokingEventMessageType\":\"ScheduledNotification\",\"riskLevel\":1}]}",
      "ResourceId" : "new-bucket",
      "ResourceName" : "new-bucket",
      "AvailabilityZone" : "cn-hangzhou-f",
      "Region" : "cn-hangzhou",
      "ResourceType" : "ACS::OSS::Bucket",
      "ResourceCreateTime" : 1624961112000,
      "Tags" : "{\"\"hc\"\":[\"\"value2\"\"]}"
    } ],
    "MaxResults" : 10
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

