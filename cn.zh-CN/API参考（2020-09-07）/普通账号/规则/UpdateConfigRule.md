# UpdateConfigRule

调用UpdateConfigRule接口修改规则。

本文将提供一个示例，将托管规则`cr-a260626622af0005****`的风险等级修改为`3`（低风险）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=UpdateConfigRule&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateConfigRule|要执行的操作，取值：**UpdateConfigRule**。 |
|ConfigRuleId|String|是|cr-a260626622af0005\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListConfigRules](~~169607~~)。 |
|Description|String|否|最多可以定义6组标签。如果资源同时具有指定的所有标签，则视为“合规”。|规则描述。 |
|InputParameters|Map|否|\{"tag1Key":"ECS","tag1Value":"test"\}|规则参数。 |
|MaximumExecutionFrequency|String|否|One\_Hour|规则执行周期。取值：

 -   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours（默认值）：24小时。

 **说明：** 当`ConfigRuleTriggerTypes`设置为`ScheduledNotification`时，需要设置该参数。 |
|ResourceTypesScope|Array of String|否|ACS::ECS::Instance|规则评估的资源类型。多个资源类型之间用半角逗号（,）分隔。 |
|RiskLevel|Integer|否|3|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ClientToken|String|否|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。`ClientToken`只支持ASCII字符，且不能超过64个字符。 |
|RegionIdsScope|String|否|cn-hangzhou|规则仅对指定地域ID中的资源生效。多个地域ID之间用半角逗号（,）分隔。

 **说明：** 仅适用于托管规则。 |
|ExcludeResourceIdsScope|String|否|lb-t4nbowvtbkss7t326\*\*\*\*|规则对指定资源ID无效，即不对该资源执行评估。多个资源ID之间用半角逗号（,）分隔。

 **说明：** 仅适用于托管规则。 |
|ConfigRuleTriggerTypes|String|否|ConfigurationItemChangeNotification|规则触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。

 **说明：** 仅自定义规则能修改该参数。 |
|ResourceGroupIdsScope|String|否|rg-aekzc7r7rhx\*\*\*\*|规则仅对指定资源组ID中的资源生效。多个资源组ID之间用半角逗号（,）分隔。

 **说明：** 仅适用于托管规则。 |
|TagKeyScope|String|否|ECS|规则仅对绑定指定标签的资源生效。

 **说明：** 仅适用于托管规则，且`TagKeyScope`和`TagValueScope`必须同时设置。 |
|TagValueScope|String|否|test|规则仅对绑定指定标签的资源生效。

 **说明：** 仅适用于托管规则，且`TagKeyScope`和`TagValueScope`必须同时设置。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConfigRuleId|String|cr-a260626622af0005\*\*\*\*|规则ID。 |
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateConfigRule
&ConfigRuleId=cr-a260626622af0005****
&RiskLevel=3
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateConfigRuleResponse>
    <ConfigRuleId>cr-a260626622af0005****</ConfigRuleId>
    <RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
</UpdateConfigRuleResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ConfigRuleId" : "cr-a260626622af0005****",
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751"
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

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

