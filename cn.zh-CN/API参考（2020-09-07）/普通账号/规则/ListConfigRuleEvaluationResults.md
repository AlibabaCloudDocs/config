# ListConfigRuleEvaluationResults

调用ListConfigRuleEvaluationResults接口查询规则对资源的评估结果。

本文将提供一个示例，查询规则`cr-cac56457e0d900d3****`对资源的评估结果。返回结果显示，规则对资源`i-hp3e4kvhzqn2s11t****`（ECS实例）的评估结果为`NON_COMPLIANT`（不合规）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListConfigRuleEvaluationResults&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListConfigRuleEvaluationResults|要执行的操作，取值：**ListConfigRuleEvaluationResults**。 |
|ComplianceType|String|否|NON\_COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|NextToken|String|否|IWBjqMYSy0is7zSMGu16\*\*\*\*|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |
|MaxResults|Integer|否|10|单次请求返回结果的最大条数。取值范围：1~100。 |
|ConfigRuleId|String|否|cr-cac56457e0d900d3\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListConfigRules](~~169607~~)。 |
|CompliancePackId|String|否|cp-f1e3326622af00cb\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListCompliancePacks](~~263332~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2A4A33BD-8186-4D60-91B9-42174EED75B5|请求ID。 |
|EvaluationResults|Object| |规则评估结果。 |
|NextToken|String|IWBjqMYSy0is7zSMGu16\*\*\*\*|查询下一页使用的Token。 |
|MaxResults|Integer|10|每页的最大记录数。 |
|EvaluationResultList|Array of EvaluationResult| |规则评估结果列表。 |
|RiskLevel|Integer|1|规则风险等级。取值：

 -   1：高风险。
-   2：中风险。
-   3：低风险。 |
|ComplianceType|String|NON\_COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|ResultRecordedTimestamp|Long|1622802307150|产生资源评估结果的时间戳。单位：毫秒。 |
|Annotation|String|\{\\"configuration\\":\\"\\",\\"desiredValue\\":\\"\\",\\"operator\\":\\"IsNotStringEmpty\\",\\"property\\":\\"$.KeyPairName\\",\\"reason\\":\\"No property contains.\\"\}|不合规资源的补充信息。可能包含以下信息：

 -   `configuration`：资源当前实际配置，即资源不合规配置。
-   `desiredValue`：资源期望配置，即资源合规配置。
-   `operator`：资源当前配置和期望配置之间的比较运算符。
-   `property`：当前配置在资源属性结构体中的JSON路径。
-   `reason`：资源不合规原因。 |
|ConfigRuleInvokedTimestamp|Long|1622802307081|规则被触发执行评估的时间戳。单位：毫秒。 |
|InvokingEventMessageType|String|ConfigurationItemChangeNotification|规则触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EvaluationResultIdentifier|Object| |规则评估结果标识符。 |
|OrderingTimestamp|Long|1622802307081|时间轴展示的时间戳。单位：毫秒。 |
|EvaluationResultQualifier|Object| |规则评估结果中的资源信息。 |
|ResourceOwnerId|Long|120886317861\*\*\*\*|资源归属的阿里云账号ID。 |
|ConfigRuleArn|String|acs:config::120886317861\*\*\*\*:rule/cr-cac56457e0d900d3\*\*\*\*|规则ARN。 |
|ResourceType|String|ACS::ECS::Instance|资源类型。 |
|ConfigRuleName|String|ECS实例CPU核数满足最低要求|规则名称。 |
|ResourceId|String|i-hp3e4kvhzqn2s11t\*\*\*\*|资源ID。 |
|ConfigRuleId|String|cr-cac56457e0d900d3\*\*\*\*|规则ID。 |
|ResourceName|String|iZuf6j91r34rnwawoox\*\*\*\*|资源名称。 |
|RegionId|String|cn-hangzhou|资源归属的地域ID。 |
|CompliancePackId|String|cp-bcc33457e0d900d5\*\*\*\*|规则所属的合规包ID。 |
|RemediationEnabled|Boolean|false|是否启用修正设置。取值：

 -   true
-   fasle |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListConfigRuleEvaluationResults
&ConfigRuleId=cr-cac56457e0d900d3****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListConfigRuleEvaluationResultsResponse>
    <RequestId>2A4A33BD-8186-4D60-91B9-42174EED75B5</RequestId>
    <EvaluationResults>
        <NextToken>IWBjqMYSy0is7zSMGu16****</NextToken>
        <MaxResults>10</MaxResults>
        <EvaluationResultList>
            <RiskLevel>1</RiskLevel>
            <ComplianceType>NON_COMPLIANT</ComplianceType>
            <ResultRecordedTimestamp>1622802307150</ResultRecordedTimestamp>
            <Annotation>{\"configuration\":\"\",\"desiredValue\":\"\",\"operator\":\"IsNotStringEmpty\",\"property\":\"$.KeyPairName\",\"reason\":\"No property contains.\"}</Annotation>
            <ConfigRuleInvokedTimestamp>1622802307081</ConfigRuleInvokedTimestamp>
            <InvokingEventMessageType>ConfigurationItemChangeNotification</InvokingEventMessageType>
            <EvaluationResultIdentifier>
                <OrderingTimestamp>1622802307081</OrderingTimestamp>
                <EvaluationResultQualifier>
                    <ConfigRuleArn>acs:config::120886317861****:rule/cr-cac56457e0d900d3****</ConfigRuleArn>
                    <ResourceType>ACS::ECS::Instance</ResourceType>
                    <ConfigRuleName>ECS实例CPU核数满足最低要求</ConfigRuleName>
                    <ResourceId>i-hp3e4kvhzqn2s11t****</ResourceId>
                    <ConfigRuleId>cr-cac56457e0d900d3****</ConfigRuleId>
                    <ResourceName>iZuf6j91r34rnwawoox****</ResourceName>
                    <RegionId>cn-hangzhou</RegionId>
                    <CompliancePackId>cp-bcc33457e0d900d5****</CompliancePackId>
                </EvaluationResultQualifier>
            </EvaluationResultIdentifier>
            <RemediationEnabled>false</RemediationEnabled>
        </EvaluationResultList>
    </EvaluationResults>
</ListConfigRuleEvaluationResultsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "2A4A33BD-8186-4D60-91B9-42174EED75B5",
  "EvaluationResults" : {
    "NextToken" : "IWBjqMYSy0is7zSMGu16****",
    "MaxResults" : 10,
    "EvaluationResultList" : [ {
      "RiskLevel" : 1,
      "ComplianceType" : "NON_COMPLIANT",
      "ResultRecordedTimestamp" : 1622802307150,
      "Annotation" : "{\\\"configuration\\\":\\\"\\\",\\\"desiredValue\\\":\\\"\\\",\\\"operator\\\":\\\"IsNotStringEmpty\\\",\\\"property\\\":\\\"$.KeyPairName\\\",\\\"reason\\\":\\\"No property contains.\\\"}",
      "ConfigRuleInvokedTimestamp" : 1622802307081,
      "InvokingEventMessageType" : "ConfigurationItemChangeNotification",
      "EvaluationResultIdentifier" : {
        "OrderingTimestamp" : 1622802307081,
        "EvaluationResultQualifier" : {
          "ConfigRuleArn" : "acs:config::120886317861****:rule/cr-cac56457e0d900d3****",
          "ResourceType" : "ACS::ECS::Instance",
          "ConfigRuleName" : "ECS实例CPU核数满足最低要求",
          "ResourceId" : "i-hp3e4kvhzqn2s11t****",
          "ConfigRuleId" : "cr-cac56457e0d900d3****",
          "ResourceName" : "iZuf6j91r34rnwawoox****",
          "RegionId" : "cn-hangzhou",
          "CompliancePackId" : "cp-bcc33457e0d900d5****"
        }
      },
      "RemediationEnabled" : false
    } ]
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|配置审计的服务角色不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

