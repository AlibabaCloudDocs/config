# GetResourceComplianceByConfigRule

调用GetResourceComplianceByConfigRule接口查询指定规则对资源的评估结果。

本文将提供一个示例，查询规则`cr-d369626622af008e****`对资源的评估结果。返回结果显示，资源总数为10条，其中合规资源数为`5`条。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetResourceComplianceByConfigRule&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetResourceComplianceByConfigRule|要执行的操作，取值：**GetResourceComplianceByConfigRule**。 |
|ComplianceType|String|否|COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ConfigRuleId|String|是|cr-d369626622af008e\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListConfigRules](~~169607~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ComplianceResult|Object| |资源的评估结果。 |
|TotalCount|Long|10|评估资源总数。 |
|Compliances|Array of Compliances| |资源的评估结果。 |
|ComplianceType|String|COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|Count|Integer|5|符合评估结果的资源数。例如：`ComplianceType`为`COMPLIANT`，表示合规的资源数。 |
|RequestId|String|23306AB1-34E0-468F-BD7B-68D8AEAB753d|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetResourceComplianceByConfigRule
&ConfigRuleId=cr-d369626622af008e****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetResourceComplianceByConfigRuleResponse>
    <ComplianceResult>
        <TotalCount>10</TotalCount>
        <Compliances>
            <ComplianceType>COMPLIANT</ComplianceType>
            <Count>5</Count>
        </Compliances>
    </ComplianceResult>
    <RequestId>23306AB1-34E0-468F-BD7B-68D8AEAB753d</RequestId>
</GetResourceComplianceByConfigRuleResponse>
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
  "RequestId" : "23306AB1-34E0-468F-BD7B-68D8AEAB753d"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

