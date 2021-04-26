# PutConfigRule

调用PutConfigRule接口新建或修改规则。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=PutConfigRule&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|PutConfigRule|要执行的操作，取值：**PutConfigRule**。 |
|ConfigRuleId|String|否|cr-2a914fcf617e00c9\*\*\*\*|规则ID。 |
|ConfigRuleName|String|是|RDS实例CPU核数满足最低要求|规则名称。 |
|Description|String|否|RDS实例的CPU核数大于等于设置的阈值，视为“合规”。|规则的描述信息。 |
|InputParameters|String|否|\{"cpuCount": "2"\}|规则入参。 |
|SourceOwner|String|是|ALIYUN|规则来源的归属。取值：

 -   CUSTOM\_FC：用户自定义函数。
-   ALIYUN：托管规则。 |
|SourceIdentifier|String|是|rds-cpu-min-count-limit|规则标识。

 -   如果规则使用了托管规则，则该参数为规则标识。
-   如果规则使用了自定义函数，则该参数为函数ARN。 |
|SourceDetailMessageType|String|是|ConfigurationItemChangeNotification|规则的触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|SourceMaximumExecutionFrequency|String|否|Twelve\_Hours|规则执行周期。取值：

 -   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|ScopeComplianceResourceId|String|否|vpc-6weoy5flv41pj4wvr\*\*\*\*|待评估资源ID。

 -   如果为空，则该规则评估ScopeComplianceResourceTypes指定的所有资源类型。
-   如果不为空，则该规则评估指定的资源。 |
|ScopeComplianceResourceTypes|String|是|\["ACS::RDS::DBInstance"\]|待评估的资源类型列表。 |
|RiskLevel|Integer|是|1|风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ClientToken|String|否|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConfigRuleId|String|cr-76ac4fcfb57e00c9\*\*\*\*|规则ID。 |
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=PutConfigRule
&ConfigRuleName=RDS实例CPU核数满足最低要求
&RiskLevel=1
&ScopeComplianceResourceTypes=["ACS::RDS::DBInstance"]
&SourceDetailMessageType=ConfigurationItemChangeNotification
&SourceIdentifier=rds-cpu-min-count-limit
&SourceOwner=ALIYUN
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<PutConfigRuleResponse>
	<ConfigRuleId>cr-76ac4fcfb57e00c9****</ConfigRuleId>
	<RequestId>A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7</RequestId>
</PutConfigRuleResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ConfigRuleId" : "cr-76ac4fcfb57e00c9****",
  "RequestId" : "A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ExceedMaxRuleCount|The maximum number of rules is exceeded.|超过规则上限。|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|此规则不存在。|
|400|ConfigRuleExists|The ConfigRule already exists.|规则名称重复。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

