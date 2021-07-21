# ListAggregateResourceEvaluationResults

调用ListAggregateResourceEvaluationResults接口查询指定账号组内资源的合规评估结果。

本文将提供一个示例，查询账号组`ca-7f00626622af0041****`内资源`23642660635396****`（RAM用户）的合规评估结果。返回结果显示，规则`cr-7f7d626622af0041****`对该资源的合规评估结果为`NON_COMPLIANT`（不合规）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListAggregateResourceEvaluationResults&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAggregateResourceEvaluationResults|要执行的操作，取值：**ListAggregateResourceEvaluationResults**。 |
|ResourceType|String|否|ACS::RAM::User|资源类型。

 关于如何获取资源类型，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|ResourceId|String|否|23642660635396\*\*\*\*|资源ID。

 关于如何获取资源类型ID，请参见[ListAggregateDiscoveredResources](~~265983~~)。 |
|ComplianceType|String|否|NON\_COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|NextToken|String|否|IWBjqMYSy0is7zSMGu16\*\*\*\*|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |
|MaxResults|Integer|否|10|单次请求返回结果的最大条数。取值范围：1~100。 |
|Region|String|否|global|资源归属的地域ID。 |
|AggregatorId|String|是|ca-7f00626622af0041\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|25C89DDB-BB79-487D-88C3-4A561F21EFC4|请求ID。 |
|EvaluationResults|Object| |资源评估结果。 |
|NextToken|String|IWBjqMYSy0is7zSMGu16\*\*\*\*|查询下一页使用的Token。 |
|MaxResults|Integer|10|每页最大记录数。 |
|EvaluationResultList|Array of EvaluationResult| |资源评估结果列表。 |
|RiskLevel|Integer|1|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ComplianceType|String|NON\_COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ResultRecordedTimestamp|Long|1624932227595|产生资源评估结果的时间戳。单位：毫秒。 |
|Annotation|String|\{\\"configuration\\":\\"false\\",\\"desiredValue\\":\\"True\\",\\"operator\\":\\"StringEquals\\",\\"property\\":\\"$.LoginProfile.MFABindRequired\\"\}|不合规资源的补充信息。 |
|ConfigRuleInvokedTimestamp|Long|1624932227157|调用规则评估资源的时间戳。单位：毫秒。 |
|InvokingEventMessageType|String|ScheduledNotification|规则触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EvaluationResultIdentifier|Object| |资源评估结果标识符。 |
|OrderingTimestamp|Long|1624932227157|时间轴展示的时间戳。单位：毫秒。 |
|EvaluationResultQualifier|Object| |资源评估结果中的资源信息。 |
|ConfigRuleArn|String|acs:config::100931896542\*\*\*\*:rule/cr-7f7d626622af0041\*\*\*\*|规则ARN。 |
|ResourceType|String|ACS::RAM::User|资源类型。 |
|ConfigRuleName|String|RAM用户开启MFA|规则名称。 |
|ResourceId|String|23642660635396\*\*\*\*|资源ID。 |
|ConfigRuleId|String|cr-7f7d626622af0041\*\*\*\*|规则ID。 |
|ResourceName|String|rd\_member|资源名称。 |
|RegionId|String|global|资源归属的地域ID。 |
|RemediationEnabled|Boolean|false|是否启用修正设置。取值：

 -   true
-   false |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAggregateResourceEvaluationResults
&ResourceId=23642660635396****
&AggregatorId=ca-7f00626622af0041****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAggregateResourceEvaluationResultsResponse>
	<code>200</code>
	<data>
		<RequestId>25C89DDB-BB79-487D-88C3-4A561F21EFC4</RequestId>
		<EvaluationResults>
			<EvaluationResultList>
				<ConfigRuleInvokedTimestamp>1624932227157</ConfigRuleInvokedTimestamp>
				<ComplianceType>NON_COMPLIANT</ComplianceType>
				<ResultRecordedTimestamp>1624932227595</ResultRecordedTimestamp>
				<InvokingEventMessageType>ScheduledNotification</InvokingEventMessageType>
				<EvaluationResultIdentifier>
					<EvaluationResultQualifier>
						<ConfigRuleId>cr-7f7d626622af0041****</ConfigRuleId>
						<ConfigRuleArn>acs:config::100931896542****:rule/cr-7f7d626622af0041****</ConfigRuleArn>
						<ResourceId>23642660635396****</ResourceId>
						<ResourceName>rd_member</ResourceName>
						<ConfigRuleName>RAM用户开启MFA</ConfigRuleName>
						<ResourceType>ACS::RAM::User</ResourceType>
						<RegionId>global</RegionId>
					</EvaluationResultQualifier>
					<OrderingTimestamp>1624932227157</OrderingTimestamp>
				</EvaluationResultIdentifier>
				<RiskLevel>1</RiskLevel>
				<RemediationEnabled>false</RemediationEnabled>
				<Annotation>{\"configuration\":\"false\",\"desiredValue\":\"True\",\"operator\":\"StringEquals\",\"property\":\"$.LoginProfile.MFABindRequired\"}</Annotation>
			</EvaluationResultList>
			<MaxResults>10</MaxResults>
		</EvaluationResults>
	</data>
	<httpStatusCode>200</httpStatusCode>
	<requestId>25C89DDB-BB79-487D-88C3-4A561F21EFC4</requestId>
</ListAggregateResourceEvaluationResultsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "25C89DDB-BB79-487D-88C3-4A561F21EFC4",
    "EvaluationResults" : {
      "EvaluationResultList" : [ {
        "ConfigRuleInvokedTimestamp" : 1624932227157,
        "ComplianceType" : "NON_COMPLIANT",
        "ResultRecordedTimestamp" : 1624932227595,
        "InvokingEventMessageType" : "ScheduledNotification",
        "EvaluationResultIdentifier" : {
          "EvaluationResultQualifier" : {
            "ConfigRuleId" : "cr-7f7d626622af0041****",
            "ConfigRuleArn" : "acs:config::100931896542****:rule/cr-7f7d626622af0041****",
            "ResourceId" : "23642660635396****",
            "ResourceName" : "rd_member",
            "ConfigRuleName" : "RAM用户开启MFA",
            "ResourceType" : "ACS::RAM::User",
            "RegionId" : "global"
          },
          "OrderingTimestamp" : 1624932227157
        },
        "RiskLevel" : 1,
        "RemediationEnabled" : false,
        "Annotation" : "{\"configuration\":\"false\",\"desiredValue\":\"True\",\"operator\":\"StringEquals\",\"property\":\"$.LoginProfile.MFABindRequired\"}"
      } ],
      "MaxResults" : 10
    }
  },
  "httpStatusCode" : "200",
  "requestId" : "25C89DDB-BB79-487D-88C3-4A561F21EFC4"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|配置审计的服务角色不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

