# GetAggregateResourceComplianceByConfigRule

调用GetAggregateResourceComplianceByConfigRule接口查询指定账号组内规则对资源的合规评估结果。

本文将提供一个示例，查询账号组`ca-a4e5626622af0079****`内规则`cr-d369626622af008e****`对资源的合规评估结果。返回结果显示，该规则共评估10个资源，其中5个资源合规。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateResourceComplianceByConfigRule&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateResourceComplianceByConfigRule|要执行的操作，取值：**GetAggregateResourceComplianceByConfigRule**。 |
|ComplianceType|String|否|COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ConfigRuleId|String|是|cr-d369626622af008e\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|AggregatorId|String|是|ca-a4e5626622af0079\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ComplianceResult|Object| |资源的评估结果。 |
|TotalCount|Long|10|规则评估的资源总数。 |
|Compliances|Array of Compliances| |资源的评估结果。 |
|ComplianceType|String|COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|Count|Integer|5|资源数。例如：当`ComplianceType`为`COMPLIANT`时，表示评估结果为合规的资源数。 |
|RequestId|String|23306AB1-34E0-468F-BD7B-68D8AEAB754C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateResourceComplianceByConfigRule
&ConfigRuleId=cr-d369626622af008e****
&AggregatorId=ca-a4e5626622af0079****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateResourceComplianceByConfigRuleResponse>
    <ComplianceResult>
        <TotalCount>10</TotalCount>
        <Compliances>
            <ComplianceType>COMPLIANT</ComplianceType>
            <Count>5</Count>
        </Compliances>
    </ComplianceResult>
    <RequestId>23306AB1-34E0-468F-BD7B-68D8AEAB754C</RequestId>
</GetAggregateResourceComplianceByConfigRuleResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ComplianceResult" : {
    "TotalCount" : 10,
    "Compliances" : [ {
      "ComplianceType" : "COMPLIANT",
      "Count" : 5
    } ]
  },
  "RequestId" : "23306AB1-34E0-468F-BD7B-68D8AEAB754C"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

