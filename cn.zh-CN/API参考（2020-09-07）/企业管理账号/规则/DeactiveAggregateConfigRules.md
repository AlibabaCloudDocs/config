# DeactiveAggregateConfigRules

调用DeactiveAggregateConfigRules接口停用指定账号组内的规则。

本文将提供一个示例，停用账号组`ca-04b3fd170e340007****`内的规则`cr-5772ba41209e007b****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DeactiveAggregateConfigRules&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeactiveAggregateConfigRules|要执行的操作，取值：**DeactiveAggregateConfigRules**。 |
|ConfigRuleIds|String|是|cr-5772ba41209e007b\*\*\*\*|规则ID。多个规则ID之间用半角逗号（,）分隔。

 关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|AggregatorId|String|是|ca-04b3fd170e340007\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EC7AED1-172F-42AE-9C12-295BC2ADB751|请求ID。 |
|OperateRuleResult|Object| |停用规则的操作结果。 |
|OperateRuleItemList|Array of OperateRuleItem| |停用规则的操作列表。 |
|ErrorCode|String|ConfigRuleNotExists|错误码。

 -   当您停用规则成功时，该参数为空。
-   当您停用规则失败时，该参数显示错误码。错误码详情，请参见[错误中心](https://error-center.aliyun.com/status/product/Config)。 |
|Success|Boolean|false|操作是否成功。取值：

 -   true：成功。
-   false：失败。 |
|ConfigRuleId|String|cr-5772ba41209e007b\*\*\*\*|规则ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeactiveAggregateConfigRules
&ConfigRuleIds=cr-5772ba41209e007b****
&AggregatorId=ca-04b3fd170e340007****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeactiveAggregateConfigRulesResponse>
    <RequestId>6EC7AED1-172F-42AE-9C12-295BC2ADB751</RequestId>
    <OperateRuleResult>
        <OperateRuleItemList>
            <ErrorCode>ConfigRuleNotExists</ErrorCode>
            <Success>false</Success>
            <ConfigRuleId>cr-5772ba41209e007b****</ConfigRuleId>
        </OperateRuleItemList>
    </OperateRuleResult>
</DeactiveAggregateConfigRulesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6EC7AED1-172F-42AE-9C12-295BC2ADB751",
  "OperateRuleResult" : {
    "OperateRuleItemList" : [ {
      "ErrorCode" : "ConfigRuleNotExists",
      "Success" : false,
      "ConfigRuleId" : "cr-5772ba41209e007b****"
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
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|403|AggregatorMemberNoPermission|The aggregator member is not authorized to perform the operation.|账号组内的成员账号无权限执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

