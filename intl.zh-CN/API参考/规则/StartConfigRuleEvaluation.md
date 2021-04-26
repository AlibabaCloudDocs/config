# StartConfigRuleEvaluation

调用StartConfigRuleEvaluation接口启用指定规则，使该规则执行一次评估。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=StartConfigRuleEvaluation&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartConfigRuleEvaluation|要执行的操作，取值：StartConfigRuleEvaluation。 |
|ConfigRuleId|String|是|cr-2a914fcf617e00c9\*\*\*\*|规则ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDD23A|请求ID。 |
|Result|Boolean|true|执行结果。取值：

 -   true：启用成功。
-   false：启用失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=StartConfigRuleEvaluation
&ConfigRuleId=cr-2a914fcf617e00c9****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<StartConfigRuleEvaluationResponse>
      <RequestId>A7A0FFF8-0B44-40C6-8BBF-3A185EFD5C2B</RequestId>
      <Result>true</Result>
</StartConfigRuleEvaluationResponse>
```

`JSON`格式

```
{
  "RequestId": "A7A0FFF8-0B44-40C6-8BBF-3A185EFD5C2B",
  "Result": true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|此规则不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

