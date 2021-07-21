# DeleteAggregateConfigRules

调用DeleteAggregateConfigRules接口删除指定账号组内的规则。

本文将提供一个示例，删除账号组`ca-a4e5626622af0079****`内的规则`cr-4e3d626622af0080****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DeleteAggregateConfigRules&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAggregateConfigRules|要执行的操作，取值：**DeleteAggregateConfigRules**。 |
|ConfigRuleIds|String|是|cr-4e3d626622af0080\*\*\*\*|规则ID。多个规则ID之间用半角逗号（,）分隔。

 关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|AggregatorId|String|是|ca-a4e5626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|OperateRuleResult|Object| |删除规则的操作结果。 |
|OperateRuleItemList|Array of OperateRuleItem| |删除规则的操作列表。 |
|ErrorCode|String|ConfigRuleCanNotDelete|错误码。

 -   当您删除规则成功时，该参数为空。
-   当您删除规则失败时，该参数显示错误码。错误码详情，请参见[错误中心](https://error-center.aliyun.com/status/product/Config)。 |
|Success|Boolean|false|操作是否成功。取值：

 -   true：成功。
-   false：失败。 |
|ConfigRuleId|String|cr-4e3d626622af0080\*\*\*\*|规则ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteAggregateConfigRules
&ConfigRuleIds=cr-4e3d626622af0080****
&AggregatorId=ca-a4e5626622af0079****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteAggregateConfigRulesResponse>
	<RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
	<OperateRuleResult>
		<OperateRuleItemList>
			<ErrorCode>ConfigRuleCanNotDelete</ErrorCode>
			<Success>false</Success>
			<ConfigRuleId>cr-4e3d626622af0080****</ConfigRuleId>
		</OperateRuleItemList>
	</OperateRuleResult>
</DeleteAggregateConfigRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "OperateRuleResult" : {
    "OperateRuleItemList" : [ {
      "ErrorCode" : "ConfigRuleCanNotDelete",
      "Success" : false,
      "ConfigRuleId" : "cr-4e3d626622af0080****"
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|ConfigRuleCanNotDelete|The config rule cannot be deleted.|当前规则不能被删除。|
|400|Invalid.ConfigRuleIds.SizeExceed|The maximum number of ConfigRuleIds cannot exceed 20.|输入的规则ID不能超过20个。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|403|AggregatorMemberNoPermission|The aggregator member is not authorized to perform the operation.|账号组内的成员账号无权限执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

