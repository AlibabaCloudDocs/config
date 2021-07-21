# StartAggregateConfigRuleEvaluation

调用StartAggregateConfigRuleEvaluation接口使指定账号组内的规则执行一次评估。

**说明：** 本接口仅用于触发规则执行一次评估。如果您需要查看规则的本次评估结果，请调用ListAggregateConfigRuleEvaluationResults接口。更多信息，请参见[ListAggregateConfigRuleEvaluationResults](~~265979~~)。

本文将提供一个示例，使账号组`ca-3a58626622af0005****`内的规则`cr-c169626622af009f****`执行一次评估。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=StartAggregateConfigRuleEvaluation&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartAggregateConfigRuleEvaluation|要执行的操作，取值：**StartAggregateConfigRuleEvaluation**。 |
|ConfigRuleId|String|是|cr-c169626622af009f\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|AggregatorId|String|是|ca-3a58626622af0005\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|ABC0FFF8-0B44-40C6-8BBF-3A185EFDD212|请求ID。 |
|Result|Boolean|true|规则执行结果。取值：

 -   true：成功。
-   false：失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=StartAggregateConfigRuleEvaluation
&ConfigRuleId=cr-c169626622af009f****
&AggregatorId=ca-3a58626622af0005****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<StartAggregateConfigRuleEvaluationResponse>
    <RequestId>ABC0FFF8-0B44-40C6-8BBF-3A185EFDD212</RequestId>
    <Result>true</Result>
</StartAggregateConfigRuleEvaluationResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "ABC0FFF8-0B44-40C6-8BBF-3A185EFDD212",
  "Result" : true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|此规则不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|403|AggregatorMemberNoPermission|The aggregator member is not authorized to perform the operation.|账号组内的成员账号无权限执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

