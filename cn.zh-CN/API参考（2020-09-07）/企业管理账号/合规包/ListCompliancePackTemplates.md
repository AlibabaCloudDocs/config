# ListCompliancePackTemplates

调用ListCompliancePackTemplates接口查询合规包模板列表。

本文将提供一个示例，查询合规包模板`ct-d254ff4e06a300cf****`的详细信息。返回结果显示合规包模板名称`BestPracticesForNetwork`、合规包模板ID `ct-d254ff4e06a300cf****`、合规包模板中的托管规则`slb-servercertificate-expired-check`等。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListCompliancePackTemplates&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListCompliancePackTemplates|要执行的操作，取值：**ListCompliancePackTemplates**。 |
|CompliancePackTemplateId|String|否|ct-d254ff4e06a300cf\*\*\*\*|合规包模板ID。

 关于如何获取合规包模板ID，请参见[ListCompliancePackTemplates](~~261176~~)。 |
|PageSize|Integer|否|10|分页时每页显示的数据行数。

 取值范围：1~100。起始值：1。默认值：10。 |
|PageNumber|Integer|否|1|页码。

 起始值：1。默认值：1。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CompliancePackTemplatesResult|Object| |合规包模板详情。 |
|PageSize|Integer|10|分页时每页显示的数据行数。 |
|PageNumber|Integer|1|页码。 |
|TotalCount|Long|1|合规包模板总数。 |
|CompliancePackTemplates|Array of CompliancePackTemplate| |合规包模板列表。 |
|RiskLevel|Integer|1|合规包中托管规则的风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|Description|String|持续检测网络架构、负载额度、网络安全设置的合规性，避免网络安全风险。|合规包描述。 |
|ConfigRules|Array of ConfigRules| |合规包中托管规则列表。 |
|Description|String|SLB证书的到期时间距离当前时间大于参数设定的时间范围，视为“合规”。默认值：90天。|托管规则描述。 |
|ManagedRuleIdentifier|String|slb-servercertificate-expired-check|托管规则标识。 |
|ManagedRuleName|String|SLB证书到期检查|托管规则名称。 |
|ConfigRuleParameters|Array of ConfigRuleParameters| |托管规则参数信息。 |
|Required|Boolean|true|托管规则中参数是否必填。取值：

 -   true
-   false |
|ParameterName|String|days|托管规则参数名称。 |
|ParameterValue|String|90|托管规则参数值。 |
|CompliancePackTemplateName|String|网络合规管理最佳实践|合规包模板名称。 |
|CompliancePackTemplateId|String|ct-d254ff4e06a300cf\*\*\*\*|合规包模板ID。 |
|RequestId|String|D67FC82F-25AE-4268-A94C-3348340748F9|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListCompliancePackTemplates
&CompliancePackTemplateId=ct-d254ff4e06a300cf****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListCompliancePackTemplatesResponse>
    <CompliancePackTemplatesResult>
        <PageSize>10</PageSize>
        <PageNumber>1</PageNumber>
        <TotalCount>1</TotalCount>
        <CompliancePackTemplates>
            <RiskLevel>1</RiskLevel>
            <Description>持续检测网络架构、负载额度、网络安全设置的合规性，避免网络安全风险。</Description>
            <ConfigRules>
                <Description>SLB证书的到期时间距离当前时间大于参数设定的时间范围，视为“合规”。默认值：90天。</Description>
                <ManagedRuleIdentifier>slb-servercertificate-expired-check</ManagedRuleIdentifier>
                <ManagedRuleName>SLB证书到期检查</ManagedRuleName>
                <ConfigRuleParameters>
                    <Required>true</Required>
                    <ParameterName>days</ParameterName>
                    <ParameterValue>90</ParameterValue>
                </ConfigRuleParameters>
            </ConfigRules>
            <CompliancePackTemplateName>网络合规管理最佳实践</CompliancePackTemplateName>
            <CompliancePackTemplateId>ct-d254ff4e06a300cf****</CompliancePackTemplateId>
        </CompliancePackTemplates>
    </CompliancePackTemplatesResult>
    <RequestId>D67FC82F-25AE-4268-A94C-3348340748F9</RequestId>
</ListCompliancePackTemplatesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "CompliancePackTemplatesResult" : {
    "PageSize" : 10,
    "PageNumber" : 1,
    "TotalCount" : 1,
    "CompliancePackTemplates" : [ {
      "RiskLevel" : 1,
      "Description" : "持续检测网络架构、负载额度、网络安全设置的合规性，避免网络安全风险。",
      "ConfigRules" : [ {
        "Description" : "SLB证书的到期时间距离当前时间大于参数设定的时间范围，视为“合规”。默认值：90天。",
        "ManagedRuleIdentifier" : "slb-servercertificate-expired-check",
        "ManagedRuleName" : "SLB证书到期检查",
        "ConfigRuleParameters" : [ {
          "Required" : true,
          "ParameterName" : "days",
          "ParameterValue" : "90"
        } ]
      } ],
      "CompliancePackTemplateName" : "网络合规管理最佳实践",
      "CompliancePackTemplateId" : "ct-d254ff4e06a300cf****"
    } ]
  },
  "RequestId" : "D67FC82F-25AE-4268-A94C-3348340748F9"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

