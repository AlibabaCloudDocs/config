# DescribeDiscoveredResource

调用DescribeDiscoveredResource接口查询资源配置详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeDiscoveredResource&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDiscoveredResource|要执行的操作，取值：**DescribeDiscoveredResource**。 |
|ResourceId|String|是|adaf.zhilon\*\*\*\*|资源ID。 |
|ResourceType|String|是|ACS::CDN::Domain|资源类型。

 **说明：** 您可以通过GetSupportedResourceTypes接口获取配置审计支持的资源类型列表。更多信息，请参见[GetSupportedResourceTypes](~~169618~~)。 |
|Region|String|是|cn-hangzhou|地域ID。 |
|MultiAccount|Boolean|否|true|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E4D71ACE-6B0A-46E0-8352-56952378CC7F|请求ID。 |
|DiscoveredResourceDetail|Object| |资源详情。 |
|AvailabilityZone|String|cn-hangzhou-h|资源可用区。 |
|ResourceType|String|ACS::CDN::Domain|资源类型。 |
|Configuration|String|\{\\"Description\\":\\"\\",\\"SslProtocol\\":\\"off\\",\\"DomainName\\":\\"adaf.zhilong\*\*\*\*\\",\\"GmtModified\\":\\"2019-04-10T03:11Z\\",\\"CdnType\\":\\"web\\",\\"GmtCreated\\":\\"2016-03-03T01:31:35Z\\",\\"Cname\\":\\"adaf.zhilong.me.w.kun\*\*\*\*.com\\",\\"Sources\\":\{\\"Source\\":\[\{\\"Type\\":\\"oss\\",\\"Content\\":\\"test2-mh.oss-cn-hangzhou.aliyuncs.com\\",\\"Priority\\":\\"20\\",\\"Port\\":80,\\"Weight\\":\\"10\\"\}\]\},\\"DomainStatus\\":\\"offline\\",\\"Sandbox\\":\\"\\"\}|资源的完整配置信息。 |
|Region|String|cn-hangzhou|地域ID。 |
|ResourceCreationTime|Long|1456968695000|资源创建时间戳。 |
|Tags|String|\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}|资源标签。 |
|AccountId|Long|987654321|阿里云账号ID。 |
|ResourceId|String|adaf.zhilon\*\*\*\*|资源ID。 |
|ResourceDeleted|Integer|1|资源删除状态。取值：

 -   1：未删除。
-   0：已删除。 |
|ResourceName|String|test-resource-name|资源名称。 |
|ResourceStatus|String|offline|资源状态。资源的状态取决于各云服务对其的定义，该参数可能为空。例如：

 -   当资源类型为ACS::ECS::Instance时，由于ECS实例有状态，因此该参数为Running或Stopped。
-   当资源类型为ACS::OSS::Bucket时，由于OSS Bucket无状态，因此该参数为空。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeDiscoveredResource
&Region=cn-hangzhou
&ResourceId=adaf.zhilon****
&ResourceType=ACS::CDN::Domain
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeDiscoveredResourceResponse>
	<RequestId>E4D71ACE-6B0A-46E0-8352-56952378CC7F</RequestId>
	<DiscoveredResourceDetail>
		<accountId>987654321</accountId>
		<resourceId>adaf.zhilon****</resourceId>
		<resourceStatus>offline</resourceStatus>
		<configuration>{\"Description\":\"\",\"SslProtocol\":\"off\",\"DomainName\":\"adaf.zhilong****\",\"GmtModified\":\"2019-04-10T03:11Z\",\"CdnType\":\"web\",\"GmtCreated\":\"2016-03-03T01:31:35Z\",\"Cname\":\"adaf.zhilong.me.w.kun****.com\",\"Sources\":{\"Source\":[{\"Type\":\"oss\",\"Content\":\"test2-mh.oss-cn-hangzhou.aliyuncs.com\",\"Priority\":\"20\",\"Port\":80,\"Weight\":\"10\"}]},\"DomainStatus\":\"offline\",\"Sandbox\":\"\"}</configuration>
		<resourceDeleted>1</resourceDeleted>
		<resourceName>test-resource-name</resourceName>
		<region>cn-hangzhou</region>
		<availabilityZone>cn-hangzhou-h</availabilityZone>
		<resourceCreationTime>1456968695000</resourceCreationTime>
		<tags>{\"\"hc\"\":[\"\"value2\"\"]}</tags>
		<resourceType>ACS::CDN::Domain</resourceType>
	</DiscoveredResourceDetail>
</DescribeDiscoveredResourceResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "E4D71ACE-6B0A-46E0-8352-56952378CC7F",
  "DiscoveredResourceDetail" : {
    "accountId" : "987654321",
    "resourceId" : "adaf.zhilon****",
    "resourceStatus" : "offline",
    "configuration" : "{\"Description\":\"\",\"SslProtocol\":\"off\",\"DomainName\":\"adaf.zhilong****\",\"GmtModified\":\"2019-04-10T03:11Z\",\"CdnType\":\"web\",\"GmtCreated\":\"2016-03-03T01:31:35Z\",\"Cname\":\"adaf.zhilong.me.w.kun****.com\",\"Sources\":{\"Source\":[{\"Type\":\"oss\",\"Content\":\"test2-mh.oss-cn-hangzhou.aliyuncs.com\",\"Priority\":\"20\",\"Port\":80,\"Weight\":\"10\"}]},\"DomainStatus\":\"offline\",\"Sandbox\":\"\"}",
    "resourceDeleted" : 1,
    "resourceName" : "test-resource-name",
    "region" : "cn-hangzhou",
    "availabilityZone" : "cn-hangzhou-h",
    "resourceCreationTime" : 1456968695000,
    "tags" : "{\"\"hc\"\":[\"\"value2\"\"]}",
    "resourceType" : "ACS::CDN::Domain"
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

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

