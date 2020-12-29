# DescribeEvaluationResults

调用DescribeEvaluationResults接口查询资源评估结果。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeEvaluationResults&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeEvaluationResults|要执行的操作，取值：DescribeEvaluationResults。 |
|ResourceType|String|否|ACS::ECS::Instance|资源类型。当您按资源类型查询资源评估结果时，必须配置该参数。

 您可以通过GetSupportedResourceTypes接口获取配置审计支持的资源类型列表，具体请参见[GetSupportedResourceTypes](~~169618~~)。

 **说明：** 资源类型（ResourceType）和规则ID（ConfigRuleId）二选一。 |
|ResourceId|String|否|i-bp151g9tpto890zr\*\*\*\*|资源ID。当您按资源类型查询资源评估结果时，必须配置该参数。 |
|ComplianceType|String|否|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规
-   NON\_COMPLIANT：不合规
-   NOT\_APPLICABLE：不适用
-   INSUFFICIENT\_DATA：数据不充分 |
|PageNumber|Integer|否|1|资源评估结果列表的页码。起始值：1。 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。取值范围：1~100。 |
|ConfigRuleId|String|否|cr-2da35180a8d1008e\*\*\*\*|规则ID。

 当您按规则查询资源评估结果时，必须配置该参数。

 **说明：** 资源类型（ResourceType）和规则ID（ConfigRuleId）二选一。 |
|MultiAccount|Boolean|否|false|企业管理账号是否查询成员账号的资源评估结果。取值：

 -   true：是。企业管理账号查询资源目录中所有成员账号的资源评估结果。
-   false（默认值）：否。企业管理账号查询当前账号的资源评估结果。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |
|MemberId|Long|否|1234567|待查询资源归属的成员账号ID。默认为空。当MultiAccount设置为true时，该参数有效。

 -   当MemberId为空时，查询企业管理账号和所有成员账号的资源评估结果。
-   当MemberId不为空时，查询指定成员账号的资源评估结果。

 **说明：** 当您使用个人版配置审计时，请忽略该参数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|EvaluationResults|Struct| |资源评估结果。 |
|EvaluationResultList|Array of EvaluationResult| |资源评估结果列表。 |
|Annotation|String|\{"operator": "StringEquals", "property": "$.SslProtocol", "desiredValue": "on", "configuration": "\['off'\]"\}|不合规资源的补充信息。 |
|ComplianceType|String|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规
-   NON\_COMPLIANT：不合规
-   NOT\_APPLICABLE：不适用
-   INSUFFICIENT\_DATA：数据不充分 |
|ConfigRuleInvokedTimestamp|Long|1589941923258|调用规则评估资源时的时间戳。 |
|EvaluationResultIdentifier|Struct| |资源评估结果标识符。 |
|EvaluationResultQualifier|Struct| |规则评估的资源范围。 |
|ConfigRuleArn|String|acs:config::120390217529\*\*\*\*:config-rule/cr-2da35180a8d1008e\*\*\*\*|规则ARN。 |
|ConfigRuleId|String|cr-2da35180a8d1008e\*\*\*\*|规则ID。 |
|ConfigRuleName|String|检测ECS实例是否开启释放保护|规则名称。 |
|RegionId|String|cn-hangzhou|地域ID。 |
|ResourceId|String|i-bp151g9tpto890zr\*\*\*\*|规则评估的资源ID。 |
|ResourceType|String|ACS::ECS::Instance|规则评估的资源类型。 |
|OrderingTimestamp|Long|1589941923117|时间轴展示的时间戳。 |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更
-   ScheduledNotification：周期 |
|RemediationEnabled|Boolean|true|修正设置是否启用。取值：

 -   true
-   false |
|ResultRecordedTimestamp|Long|1589941923432|资源评估结果的时间戳。 |
|RiskLevel|Integer|1|风险等级。取值：

 -   1：高风险
-   2：中风险
-   3：低风险 |
|PageNumber|Integer|1|资源评估结果列表的页码。起始值：1。 |
|PageSize|Integer|10|分页查询时设置的每页行数。取值范围：1~100。 |
|TotalCount|Long|2|资源评估结果的总记录数。 |
|RequestId|String|7A90353C-A64F-4914-A452-68995753F5C2|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeEvaluationResults
&ConfigRuleId=cr-2da35180a8d1008e****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
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
					          <ConfigRuleName>检测ECS实例是否开启释放保护</ConfigRuleName>
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
					          <ConfigRuleName>检测ECS实例是否开启释放保护</ConfigRuleName>
					          <ResourceType>ACS::ECS::Instance</ResourceType>
					          <RegionId>cn-hangzhou</RegionId>
				        </EvaluationResultQualifier>
				        <OrderingTimestamp>1608262263084</OrderingTimestamp>
			      </EvaluationResultIdentifier>
			      <RiskLevel>3</RiskLevel>
			      <RemediationEnabled>true</RemediationEnabled>
			      <Annotation></Annotation>
		    </EvaluationResultList>
		    <TotalCount>52</TotalCount>
		    <PageSize>10</PageSize>
		    <PageNumber>1</PageNumber>
	  </EvaluationResults>
</DescribeEvaluationResultsResponse>
```

`JSON` 格式

```
{
	"RequestId": "D296EE41-1143-4B13-83BB-909008100130",
	"EvaluationResults": {
		"EvaluationResultList": [
			{
				"ConfigRuleInvokedTimestamp": 1608262263084,
				"ComplianceType": "COMPLIANT",
				"ResultRecordedTimestamp": 1608262263321,
				"InvokingEventMessageType": "ConfigurationItemChangeNotification",
				"EvaluationResultIdentifier": {
					"EvaluationResultQualifier": {
						"ConfigRuleId": "cr-22726457e0d90078****",
						"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
						"ResourceId": "i-t4n0piq1mkfo1d27****",
						"ConfigRuleName": "检测ECS实例是否开启释放保护",
						"ResourceType": "ACS::ECS::Instance",
						"RegionId": "cn-hangzhou"
					},
					"OrderingTimestamp": 1608262263084
				},
				"RiskLevel": 3,
				"RemediationEnabled": true,
				"Annotation": ""
			},
			{
				"ConfigRuleInvokedTimestamp": 1608262263084,
				"ComplianceType": "COMPLIANT",
				"ResultRecordedTimestamp": 1608262263326,
				"InvokingEventMessageType": "ConfigurationItemChangeNotification",
				"EvaluationResultIdentifier": {
					"EvaluationResultQualifier": {
						"ConfigRuleId": "cr-22726457e0d90078****",
						"ConfigRuleArn": "acs:config::120886317861****:config-rule/cr-22726457e0d90078****",
						"ResourceId": "i-2ze5o2beycwbvqnx****",
						"ConfigRuleName": "检测ECS实例是否开启释放保护",
						"ResourceType": "ACS::ECS::Instance",
						"RegionId": "cn-hangzhou"
					},
					"OrderingTimestamp": 1608262263084
				},
				"RiskLevel": 3,
				"RemediationEnabled": true,
				"Annotation": ""
			}
		],
		"TotalCount": 52,
		"PageSize": 10,
		"PageNumber": 1
	}
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|配置审计的服务角色不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

