# DescribeConfigRule

调用DescribeConfigRule接口查询规则详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeConfigRule&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeConfigRule|要执行的操作，取值：**DescribeConfigRule**。 |
|ConfigRuleId|String|是|cr-7bc06457e0d90041\*\*\*\*|规则ID。关于如何查询规则ID，请参见[ListConfigRules](~~169607~~)。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99|请求ID。 |
|ConfigRule|Object| |规则详情。 |
|RiskLevel|Integer|3|规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|InputParameters|Map| |规则入参。 |
|Source|Object| |规则执行逻辑的来源信息。 |
|SourceDetails|Array of SourceDetails| |规则来源详情。 |
|MessageType|String|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EventSource|String|aliyun.config|事件来源。

 **说明：** 目前仅支持配置审计事件：aliyun.config。 |
|MaximumExecutionFrequency|String|Six\_Hours|规则的执行周期。取值：

 -   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|Owner|String|ALIYUN|规则来源的归属。取值：

 -   CUSTOM\_FC：用户自定义函数。
-   ALIYUN：托管规则。 |
|SourceConditions|Array of SourceConditions| |规则的配置条件。 |
|DesiredValue|String|2|规则入参的期望值。 |
|Tips|String|实例的状态|参数的提示信息。 |
|Operator|String|GreaterOrEquals|规则入参的操作符。通过SelectPath获取到的不同数据类型，对应不同的操作符。

 -   当数据类型为String时，取值：
    -   StringEquals：等于。
    -   NotStringEquals：不等于。
    -   StringIn：存在。
    -   NotStringIn：不存在。
    -   StringContains：包含。
    -   NotStringContains：不包含。
-   当数据类型为Number时，取值：
    -   Equals：等于。
    -   NotEquals：不等于。
    -   Less：小于。
    -   LessOrEquals：小于等于。
    -   Greater：大于。
    -   GreaterOrEquals：大于等于。
-   当数据类型为基于Base64进制编码的Base64 String时，取值：
    -   Base64Contains：包含。
    -   NotBase64Contains：不包含。
    -   Base64ContainsAll：包含全部。
    -   Base64ExcludeAll：排除全部。
-   当数据类型为Array时，取值：
    -   Contains：包含。
    -   NotContains：不包含。
    -   In：存在。
    -   NotIn：不存在。
    -   ContainsAll：包含全部。
    -   ExcludeAll：排除全部。
    -   IsEmpty：为空。 |
|Name|String|cpuCount|规则入参的名称。 |
|Identifier|String|rds-cpu-min-count-limit|规则标识。

 -   如果规则使用了托管规则，则该参数为托管规则名称。
-   如果规则使用了自定义函数，则该参数为函数ARN。 |
|ConfigRuleState|String|ACTIVE|当前规则的运行状态。取值：

 -   ACTIVE：应用中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|MaximumExecutionFrequency|String|Six\_Hours|规则的执行周期。取值：

 -   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|ManagedRule|Object| |托管规则详情。 |
|SourceDetails|Array of SourceDetails| |托管规则详情。 |
|MessageType|String|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EventSource|String|aliyun.config|规则的事件来源。

 **说明：** 目前仅支持配置审计事件：aliyun.config。 |
|MaximumExecutionFrequency|String|Six\_Hours|规则的执行周期。取值：

 -   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|Description|String|RDS实例的CPU核数大于等于设置的阈值，视为“合规”。|托管规则的描述信息。 |
|Labels|Array of String|\["RDS","CPU"\]|托管规则的标签列表。 |
|Identifier|String|rds-cpu-min-count-limit|托管规则的标识符。 |
|OptionalInputParameterDetails|Map| |托管规则可选参数的描述信息。 |
|ManagedRuleName|String|rds-cpu-min-count-limit|托管规则的名称。 |
|CompulsoryInputParameterDetails|Map| |托管规则必填参数的信息。 |
|ConfigRuleArn|String|acs:config::120886317861\*\*\*\*:rule/cr-7bc06457e0d90041\*\*\*\*|规则ARN。 |
|Description|String|RDS实例的CPU核数大于等于设置的阈值，视为“合规”。|规则的描述信息。 |
|ConfigRuleName|String|RDS实例CPU核数满足最低要求|规则名称。 |
|Scope|Object| |规则的监控范围。 |
|ComplianceResourceTypes|Array of String|\["ACS::RDS::DBInstance"\]|待评估资源类型列表。 |
|ComplianceResourceId|String|vpc-6weoy5flv41pj4wvr\*\*\*\*|待评估资源ID。 |
|ConfigRuleEvaluationStatus|Object| |资源评估状态。 |
|LastErrorCode|String|FunctionNotFound|规则最近一次执行的错误码。 |
|LastSuccessfulEvaluationTimestamp|Long|1618901957876|规则最近一次调用成功的结束时间戳。 |
|FirstActivatedTimestamp|Long|1618901952341|首次激活时间戳。 |
|FirstEvaluationStarted|Boolean|true|规则是否已执行过评估。取值：

 -   true（默认值）
-   false |
|LastSuccessfulInvocationTimestamp|Long|1618901957395|规则最近一次调用成功的开始时间戳。 |
|LastErrorMessage|String|function 'funtionName' does not exist in service 'serviceName'|规则最近一次执行的错误信息。 |
|LastFailedEvaluationTimestamp|Long|1602819143913|规则最近一次调用失败的结束时间戳。 |
|LastFailedInvocationTimestamp|Long|1602819143910|规则最近一次调用失败的开始时间戳。 |
|ConfigRuleId|String|cr-7bc06457e0d90041\*\*\*\*|规则ID。 |
|ModifiedTimestamp|Long|1602992721000|规则最近一次修改的时间戳。 |
|CreateTimestamp|Long|1602818964884|创建规则时的时间戳。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeConfigRule
&ConfigRuleId=cr-7bc06457e0d90041****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeConfigRuleResponse>
	<RequestId>A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99</RequestId>
	<ConfigRule>
		<ManagedRule>
			<ManagedRuleName>rds-cpu-min-count-limit</ManagedRuleName>
			<OptionalInputParameterDetails />
			<Description>RDS实例的CPU核数大于等于设置的阈值，视为“合规”。</Description>
			<Identifier>rds-cpu-min-count-limit</Identifier>
			<CompulsoryInputParameterDetails>
				<cpuCount>
					<defaultValue>2</defaultValue>
					<type>integer</type>
				</cpuCount>
			</CompulsoryInputParameterDetails>
			<Labels>RDS</Labels>
			<Labels>CPU</Labels>
			<SourceDetails>
				<EventSource>aliyun.config</EventSource>
				<MessageType>ConfigurationItemChangeNotification</MessageType>
			</SourceDetails>
		</ManagedRule>
		<ConfigRuleEvaluationStatus>
			<FirstActivatedTimestamp>1618901952341</FirstActivatedTimestamp>
			<LastSuccessfulEvaluationTimestamp>1618901957876</LastSuccessfulEvaluationTimestamp>
			<FirstEvaluationStarted>true</FirstEvaluationStarted>
			<LastSuccessfulInvocationTimestamp>1618901957395</LastSuccessfulInvocationTimestamp>
		</ConfigRuleEvaluationStatus>
		<ConfigRuleState>ACTIVE</ConfigRuleState>
		<Source>
			<Owner>ALIYUN</Owner>
			<Identifier>rds-cpu-min-count-limit</Identifier>
			<SourceConditions>
				<Operator>GreaterOrEquals</Operator>
				<DesiredValue>2</DesiredValue>
				<Required>true</Required>
				<SelectPath>$.DBInstanceCPU</SelectPath>
			</SourceConditions>
			<SourceDetails>
				<EventSource>aliyun.config</EventSource>
				<MessageType>ConfigurationItemChangeNotification</MessageType>
			</SourceDetails>
		</Source>
		<OrganizationRule>false</OrganizationRule>
		<ConfigRuleId>cr-7bc06457e0d90041****</ConfigRuleId>
		<Scope>
			<ComplianceResourceTypes>ACS::RDS::DBInstance</ComplianceResourceTypes>
		</Scope>
		<ConfigRuleArn>acs:config::120886317861****:rule/cr-7bc06457e0d90041****</ConfigRuleArn>
		<ConfigRuleName>RDS实例CPU核数满足最低要求</ConfigRuleName>
		<RiskLevel>3</RiskLevel>
		<InputParameters>
			<cpuCount>2</cpuCount>
		</InputParameters>
	</ConfigRule>
</DescribeConfigRuleResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99",
  "ConfigRule" : {
    "ManagedRule" : {
      "ManagedRuleName" : "rds-cpu-min-count-limit",
      "OptionalInputParameterDetails" : { },
      "Description" : "RDS实例的CPU核数大于等于设置的阈值，视为“合规”。",
      "Identifier" : "rds-cpu-min-count-limit",
      "CompulsoryInputParameterDetails" : {
        "cpuCount" : {
          "defaultValue" : "2",
          "type" : "integer"
        }
      },
      "Labels" : [ "RDS", "CPU" ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "ConfigRuleEvaluationStatus" : {
      "FirstActivatedTimestamp" : 1618901952341,
      "LastSuccessfulEvaluationTimestamp" : 1618901957876,
      "FirstEvaluationStarted" : true,
      "LastSuccessfulInvocationTimestamp" : 1618901957395
    },
    "ConfigRuleState" : "ACTIVE",
    "Source" : {
      "Owner" : "ALIYUN",
      "Identifier" : "rds-cpu-min-count-limit",
      "SourceConditions" : [ {
        "Operator" : "GreaterOrEquals",
        "DesiredValue" : "2",
        "Required" : true,
        "SelectPath" : "$.DBInstanceCPU"
      } ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "OrganizationRule" : false,
    "ConfigRuleId" : "cr-7bc06457e0d90041****",
    "Scope" : {
      "ComplianceResourceTypes" : [ "ACS::RDS::DBInstance" ]
    },
    "ConfigRuleArn" : "acs:config::120886317861****:rule/cr-7bc06457e0d90041****",
    "ConfigRuleName" : "RDS实例CPU核数满足最低要求",
    "RiskLevel" : 3,
    "InputParameters" : {
      "cpuCount" : "2"
    }
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|此规则不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

