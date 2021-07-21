# ListAggregators

调用ListAggregators接口查询账号组列表。

本文将提供一个示例，查询账号组列表，单次最多返回10条数据。返回结果显示，账号组名称为`Test_Group`、账号组描述为`测试组`、账号组类型为`CUSTOM`（自定义账号组）、账号组内成员账号个数为2等。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListAggregators&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAggregators|要执行的操作，取值：**ListAggregators**。 |
|NextToken|String|否|TGlzdFJlc291cmNlU2hhcmVzJjE1MTI2NjY4NzY5MTAzOTEmMiZORnI4NDhVeEtrUT0|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |
|MaxResults|Integer|是|10|单次请求返回结果的最大条数。取值范围：1~100。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|20C8526D-12C5-4336-BC72-EBD5D1BA732F|请求ID。 |
|AggregatorsResult|Object| |账号组结果列表。 |
|NextToken|String|TGlzdFJlc291cmNlU2hhcmVzJjE1MTI2NjY4NzY5MTAzOTEmMiZORnI4NDhVeEtrUT0|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |
|Aggregators|Array of Aggregators| |账号组列表。 |
|AggregatorCreateTimestamp|Long|1623036305000|创建账号组的时间戳。 |
|AggregatorAccountCount|Long|2|账号组内的成员账号数量。 |
|Description|String|测试组|账号组描述。 |
|AggregatorName|String|Test\_Group|账号组名称。 |
|AggregatorStatus|Integer|1|账号组状态。取值：

 -   0：创建中。
-   1：创建完成。 |
|AggregatorType|String|CUSTOM|账号组类型。取值：

 -   RD：全局账号组。
-   CUSTOM：自定义账号组。 |
|AccountId|Long|100931896542\*\*\*\*|创建账号组的企业管理账号ID。 |
|AggregatorId|String|ca-88ea626622af0055\*\*\*\*|账号组ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAggregators
&MaxResults=10
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAggregatorsResponse>
	<RequestId>20C8526D-12C5-4336-BC72-EBD5D1BA732F</RequestId>
	<AggregatorsResult>
		<NextToken></NextToken>
		<Aggregators>
			<AggregatorName>Test_Group</AggregatorName>
			<Description>测试组</Description>
			<AccountId>100931896542****</AccountId>
			<AggregatorCreateTimestamp>1623036305000</AggregatorCreateTimestamp>
			<AggregatorAccountCount>2</AggregatorAccountCount>
			<AggregatorStatus>1</AggregatorStatus>
			<AggregatorType>CUSTOM</AggregatorType>
			<AggregatorId>ca-9190626622af00a9****</AggregatorId>
		</Aggregators>
	</AggregatorsResult>
</ListAggregatorsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "20C8526D-12C5-4336-BC72-EBD5D1BA732F",
  "AggregatorsResult" : {
    "NextToken" : "",
    "Aggregators" : [ {
      "AggregatorName" : "Test_Group",
      "Description" : "测试组",
      "AccountId" : "100931896542****",
      "AggregatorCreateTimestamp" : 1623036305000,
      "AggregatorAccountCount" : 2,
      "AggregatorStatus" : 1,
      "AggregatorType" : "CUSTOM",
      "AggregatorId" : "ca-9190626622af00a9****"
    } ]
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

