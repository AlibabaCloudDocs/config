# DescribeCompliance

调用DescribeCompliance接口查询资源的合规结果统计。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeCompliance&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCompliance|要执行的操作，取值：**DescribeCompliance**。 |
|ResourceType|String|否|ACS::ECS::Instance|资源类型。

 当您按资源维度查询资源评估结果时，必须配置参数ResourceType和ResourceId。 |
|ResourceId|String|否|i-bp151g9tpto890zr\*\*\*\*|资源ID。

 当您按资源维度查询资源评估结果时，必须配置参数ResourceType和ResourceId。 |
|ComplianceType|String|否|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|ConfigRuleId|String|否|cr-12b398b633820012\*\*\*\*|规则ID。

 当您按规则维度查询资源评估结果时，必须同时配置参数ConfigRuleId、ResourceType和ResourceId，否则ConfigRuleId无效。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|1234567|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ComplianceResult|Object| |合规结果统计。 |
|TotalCount|Long|13|所有合规类型的数量统计。

 -   当入参指定ResourceId时，该参数为资源数统计值。
-   当入参指定ConfigRuleId时，该参数为规则数统计值。 |
|Compliances|Array of Compliances| |资源合规结果统计。 |
|ComplianceType|String|COMPLIANT|合规类型。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：数据不充分。 |
|Count|Integer|13|指定合规类型的数量统计。

 -   当入参指定ResourceId时，该参数为资源数统计值。
-   当入参指定ConfigRuleId时，该参数为规则数统计值。 |
|RequestId|String|17306AB1-34E0-468F-BD7B-68D8AEAB754F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeCompliance
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeComplianceResponse>
    <RequestId>17306AB1-34E0-468F-BD7B-68D8AEAB754F</RequestId>
    <Compliances>
        <Compliances>
            <ComplianceType>NOT_APPLICABLE</ComplianceType>
            <Count>0</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>NON_COMPLIANT</ComplianceType>
            <Count>5</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>INSUFFICIENT_DATA</ComplianceType>
            <Count>0</Count>
        </Compliances>
        <Compliances>
            <ComplianceType>COMPLIANT</ComplianceType>
            <Count>13</Count>
        </Compliances>
    </CompliancesResponse>
</DescribeCompliance>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "17306AB1-34E0-468F-BD7B-68D8AEAB754F",
  "Compliances" : {
    "Compliances" : [ {
      "ComplianceType" : "NOT_APPLICABLE",
      "Count" : 0
    }, {
      "ComplianceType" : "NON_COMPLIANT",
      "Count" : 5
    }, {
      "ComplianceType" : "INSUFFICIENT_DATA",
      "Count" : 0
    }, {
      "ComplianceType" : "COMPLIANT",
      "Count" : 13
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

