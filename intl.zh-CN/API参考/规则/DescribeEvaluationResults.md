# DescribeEvaluationResults

调用DescribeEvaluationResults接口查询资源评估结果。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeEvaluationResults&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeEvaluationResults|要执行的操作，取值：**DescribeEvaluationResults**。 |
|ResourceType|String|否|ACS::ECS::Instance|资源类型。当您按资源类型查询资源评估结果时，必须配置该参数。

 您可以通过GetSupportedResourceTypes接口获取配置审计支持的资源类型列表。更多信息，请参见[GetSupportedResourceTypes](~~169618~~)。

 **说明：** 资源类型（ResourceType）和规则ID（ConfigRuleId）二选一。 |
|ResourceId|String|否|i-bp151g9tpto890zr\*\*\*\*|资源ID。当您按资源类型查询资源评估结果时，必须配置该参数。 |
|ComplianceType|String|否|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|PageNumber|Integer|否|1|资源评估结果列表的页码。起始值：1。 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。取值范围：1~100。 |
|ConfigRuleId|String|否|cr-2da35180a8d1008e\*\*\*\*|规则ID。当您按规则查询资源评估结果时，必须配置该参数。

 **说明：** 资源类型（ResourceType）和规则ID（ConfigRuleId）二选一。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|D296EE41-1143-4B13-83BB-909008100130|请求ID。 |
|EvaluationResults|Object| |资源评估结果。 |
|EvaluationResultList|Array of EvaluationResult| |资源评估结果列表。 |
|RiskLevel|Integer|1|风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ComplianceType|String|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|ResultRecordedTimestamp|Long|1589941923432|资源评估结果的时间戳。 |
|Annotation|String|\{"operator": "StringEquals", "property": "$.SslProtocol", "desiredValue": "on", "configuration": "\['off'\]"\}|不合规资源的补充信息。 |
|ConfigRuleInvokedTimestamp|Long|1589941923258|调用规则评估资源时的时间戳。 |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EvaluationResultIdentifier|Object| |资源评估结果标识符。 |
|OrderingTimestamp|Long|1589941923117|时间轴展示的时间戳。 |
|EvaluationResultQualifier|Object| |规则评估的资源范围。 |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-2da35180a8d1008e\*\*\*\*|规则ARN。 |
|ResourceType|String|ACS::ECS::Instance|规则评估的资源类型。 |
|ConfigRuleName|String|ECS实例开启释放保护|规则名称。 |
|ResourceId|String|i-bp151g9tpto890zr\*\*\*\*|规则评估的资源ID。 |
|ConfigRuleId|String|cr-2da35180a8d1008e\*\*\*\*|规则ID。 |
|ResourceName|String|launch-advisor-20200330|规则评估的资源名称。 |
|RegionId|String|cn-hangzhou|地域ID。 |
|RemediationEnabled|Boolean|false|修正设置是否启用。取值：

 -   true
-   false |
|PageNumber|Integer|1|资源评估结果列表的页码。起始值：1。 |
|PageSize|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Long|2|资源评估结果的总记录数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeEvaluationResults
&ConfigRuleId=cr-2da35180a8d1008e****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeEvaluationResultsResponse>
	<RequestId>D296EE41-1143-4B13-83BB-909008100130</RequestId>
	<EvaluationResults>
		<EvaluationResultList>
			<ConfigRuleInvokedTimestamp>1608262263084</ConfigRuleInvokedTimestamp>
			<ComplianceType>COMPLIANT</ComplianceType>
			<ResultRecordedTimestamp>1608262263321</ResultRecordedTimestamp>
			<InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
			<EvaluationResultIdentifier>
				<EvaluationResultQualifier>
					<ConfigRuleId>cr-22726457e0d90078****</ConfigRuleId>
					<ConfigRuleArn>acs:config::120886317861****:config-rule/cr-22726457e0d90078****</ConfigRuleArn>
					<ResourceId>i-t4n0piq1mkfo1d27****</ResourceId>
					<ConfigRuleName>ECS实例开启释放保护</ConfigRuleName>
					<ResourceType>ACS::ECS::Instance</ResourceType>
					<RegionId>cn-hangzhou</RegionId>
				</EvaluationResultQualifier>
				<OrderingTimestamp>1608262263084</OrderingTimestamp>
			</EvaluationResultIdentifier>
			<RiskLevel>3</RiskLevel>
			<RemediationEnabled>true</RemediationEnabled>
			<Annotation></Annotation>
		</EvaluationResultList>
		<EvaluationResultList>
			<ConfigRuleInvokedTimestamp>1608262263084</ConfigRuleInvokedTimestamp>
			<ComplianceType>COMPLIANT</ComplianceType>
			<ResultRecordedTimestamp>1608262263326</ResultRecordedTimestamp>
			<InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
			<EvaluationResultIdentifier>
				<EvaluationResultQualifier>
					<ConfigRuleId>cr-22726457e0d90078****</ConfigRuleId>
					<ConfigRuleArn>acs:config::120886317861****:config-rule/cr-22726457e0d90078****</ConfigRuleArn>
					<ResourceId>i-2ze5o2beycwbvqnx****</ResourceId>
					<ConfigRuleName>ECS实例开启释放保护</ConfigRuleName>
					<ResourceType>ACS::ECS::Instance</ResourceType>
					<RegionId>cn-hangzhou</RegionId>
				</EvaluationResultQualifier>
				<OrderingTimestamp>1608262263084</OrderingTimestamp>
			</EvaluationResultIdentifier>
			<RiskLevel>3</RiskLevel>
			<RemediationEnabled>false</RemediationEnabled>
			<Annotation></Annotation>
		</EvaluationResultList>
		<TotalCount>52</TotalCount>
		<PageSize>10</PageSize>
		<PageNumber>1</PageNumber>
	</EvaluationResults>
</DescribeEvaluationResultsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "D296EE41-1143-4B13-83BB-909008100130",
  "EvaluationResults" : {
    "EvaluationResultList" : [ {
      "ConfigRuleInvokedTimestamp" : 1608262263084,
      "ComplianceType" : "COMPLIANT",
      "ResultRecordedTimestamp" : 1608262263321,
      "InvokingEventMessageType" : "ConfigurationItemChangeNotification",
      "EvaluationResultIdentifier" : {
        "EvaluationResultQualifier" : {
          "ConfigRuleId" : "cr-22726457e0d90078****",
          "ConfigRuleArn" : "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
          "ResourceId" : "i-t4n0piq1mkfo1d27****",
          "ConfigRuleName" : "ECS实例开启释放保护",
          "ResourceType" : "ACS::ECS::Instance",
          "RegionId" : "cn-hangzhou"
        },
        "OrderingTimestamp" : 1608262263084
      },
      "RiskLevel" : 3,
      "RemediationEnabled" : true,
      "Annotation" : ""
    }, {
      "ConfigRuleInvokedTimestamp" : 1608262263084,
      "ComplianceType" : "COMPLIANT",
      "ResultRecordedTimestamp" : 1608262263326,
      "InvokingEventMessageType" : "ConfigurationItemChangeNotification",
      "EvaluationResultIdentifier" : {
        "EvaluationResultQualifier" : {
          "ConfigRuleId" : "cr-22726457e0d90078****",
          "ConfigRuleArn" : "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
          "ResourceId" : "i-2ze5o2beycwbvqnx****",
          "ConfigRuleName" : "ECS实例开启释放保护",
          "ResourceType" : "ACS::ECS::Instance",
          "RegionId" : "cn-hangzhou"
        },
        "OrderingTimestamp" : 1608262263084
      },
      "RiskLevel" : 3,
      "RemediationEnabled" : false,
      "Annotation" : ""
    } ],
    "TotalCount" : 52,
    "PageSize" : 10,
    "PageNumber" : 1
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|配置审计的服务角色不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

