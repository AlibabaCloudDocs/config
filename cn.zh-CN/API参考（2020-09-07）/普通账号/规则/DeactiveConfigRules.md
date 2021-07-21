# DeactiveConfigRules

调用DeactiveConfigRules接口停用规则。

本文将提供一个示例，停用规则`cr-19a56457e0d90058****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DeactiveConfigRules&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeactiveConfigRules|要执行的操作，取值：**DeactiveConfigRules**。 |
|ConfigRuleIds|String|是|cr-19a56457e0d90058\*\*\*\*|规则ID。多个规则ID之间用半角逗号（,）分隔。

 关于如何获取规则ID，请参见[ListConfigRules](~~169607~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|54FA74D9-45D4-4CA5-9BE1-97F6EA19AF5B|请求ID。 |
|OperateRuleResult|Object| |停用规则的操作结果。 |
|OperateRuleItemList|Array of OperateRuleItem| |停用规则的操作列表。 |
|ErrorCode|String|ConfigRuleCanNotDelete|错误码。

 -   当您停用规则成功时，该参数为空。
-   当您停用规则失败时，该参数显示错误码。错误码详情，请参见[错误中心](https://error-center.aliyun.com/status/product/Config)。 |
|Success|Boolean|false|操作是否成功。取值：

 -   true：成功。
-   false：失败。 |
|ConfigRuleId|String|cr-19a56457e0d90058\*\*\*\*|规则ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeactiveConfigRules
&ConfigRuleIds=cr-19a56457e0d90058****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeactiveConfigRulesResponse>
	<RequestId>54FA74D9-45D4-4CA5-9BE1-97F6EA19AF5B</RequestId>
	<OperateRuleResult>
		<OperateRuleItemList>
			<ConfigRuleId>cr-19a56457e0d90058****</ConfigRuleId>
			<ErrorCode></ErrorCode>
			<Success>true</Success>
		</OperateRuleItemList>
	</OperateRuleResult>
</DeactiveConfigRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "54FA74D9-45D4-4CA5-9BE1-97F6EA19AF5B",
  "OperateRuleResult" : {
    "OperateRuleItemList" : [ {
      "ConfigRuleId" : "cr-19a56457e0d90058****",
      "ErrorCode" : "",
      "Success" : true
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.ConfigRuleIds.SizeExceed|The maximum number of ConfigRuleIds cannot exceed 20.|输入的规则ID不能超过20个。|
|400|ConfigRuleStatusNotActive|The status of the config rule is not active.|当前规则不是启用状态。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

