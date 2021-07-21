# ListAggregateConfigRuleEvaluationResults

调用ListAggregateConfigRuleEvaluationResults接口查询指定账号组内规则对资源的评估结果。

本文将提供一个示例，查询账号组`ca-d1e3326622af00cb****`内规则`cr-888f626622af00ae****`对资源的评估结果。返回结果显示，规则对资源`Bucket-test`（存储空间）的评估结果为`NON_COMPLIANT`（不合规）。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=ListAggregateConfigRuleEvaluationResults&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAggregateConfigRuleEvaluationResults|要执行的操作，取值：**ListAggregateConfigRuleEvaluationResults**。 |
|ComplianceType|String|否|NON\_COMPLIANT|合规评估结果。取值：

 -   COMPLIANT：合规。
-   NON\_COMPLIANT：不合规。
-   NOT\_APPLICABLE：不适用。
-   INSUFFICIENT\_DATA：无数据。 |
|NextToken|String|否|IWBjqMYSy0is7zSMGu16\*\*\*\*|当请求的返回结果被截断时，您可以使用`NextToken`再次发起请求，获取从当前截断位置之后的内容。 |
|MaxResults|Integer|否|10|单次请求返回结果的最大条数。取值范围：1~100。 |
|ConfigRuleId|String|否|cr-888f626622af00ae\*\*\*\*|规则ID。

 关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|ResourceOwnerId|Long|否|173808452267\*\*\*\*|资源归属的阿里云账号ID。 |
|AggregatorId|String|是|ca-b1e6626622af00cb\*\*\*\*|账号组ID。

 关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |
|CompliancePackId|String|否|cp-f1e3326622af00cb\*\*\*\*|合规包ID。

 关于如何获取合规包ID，请参见[ListAggregateCompliancePacks](~~262059~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A6662516-D056-4325-B6A7-CD3E89C97C39|请求ID。 |
|EvaluationResults|Object| |规则评估结果集合。 |
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
|ResultRecordedTimestamp|Long|1624869013065|产生资源评估结果的时间戳。单位：毫秒。 |
|Annotation|String|\{\\"configuration\\":\\"LRS\\",\\"desiredValue\\":\\"ZRS\\",\\"operator\\":\\"StringEquals\\",\\"property\\":\\"$.DataRedundancyType\\"\}|不合规资源的补充信息。可能包含以下信息：

 -   `configuration`：资源当前实际配置，即资源不合规配置。
-   `desiredValue`：资源期望配置，即资源合规配置。
-   `operator`：资源当前配置和期望配置之间的比较运算符。
-   `property`：当前配置在资源属性结构体中的JSON路径。
-   `reason`：资源不合规原因。 |
|ConfigRuleInvokedTimestamp|Long|1624869012713|规则被触发执行评估的时间戳。单位：毫秒。 |
|InvokingEventMessageType|String|ScheduledNotification|规则触发机制。取值：

 -   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EvaluationResultIdentifier|Object| |规则评估结果标识符。 |
|OrderingTimestamp|Long|1624869012713|时间轴展示的时间戳。单位：毫秒。

 **说明：** 该时间为规则被触发执行评估的时间戳，即参数`ConfigRuleInvokedTimestamp`显示的时间。 |
|EvaluationResultQualifier|Object| |规则评估结果中的资源信息。 |
|ResourceOwnerId|Long|173808452267\*\*\*\*|资源归属的阿里云账号ID。 |
|ConfigRuleArn|String|acs:config::100931896542\*\*\*\*:rule/cr-888f626622af00ae\*\*\*\*|规则ARN。 |
|ResourceType|String|ACS::OSS::Bucket|资源类型。 |
|ConfigRuleName|String|OSS存储空间开启同城冗余存储|规则名称。 |
|ResourceId|String|Bucket-test|资源ID。 |
|ConfigRuleId|String|cr-888f626622af00ae\*\*\*\*|规则ID。 |
|ResourceName|String|Bucket-test|资源名称。 |
|RegionId|String|cn-hangzhou|资源归属的地域ID。 |
|CompliancePackId|String|cr-7263fd26622af00bc\*\*\*\*|规则所属的合规包ID。 |
|RemediationEnabled|Boolean|false|是否启用修正设置。取值：

 -   true
-   false |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAggregateConfigRuleEvaluationResults
&ConfigRuleId=cr-888f626622af00ae****
&AggregatorId=ca-b1e6626622af00cb****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListAggregateConfigRuleEvaluationResultsResponse>
    <RequestId>A6662516-D056-4325-B6A7-CD3E89C97C39</RequestId>
    <EvaluationResults>
        <NextToken>IWBjqMYSy0is7zSMGu16****</NextToken>
        <MaxResults>10</MaxResults>
        <EvaluationResultList>
            <RiskLevel>1</RiskLevel>
            <ComplianceType>NON_COMPLIANT</ComplianceType>
            <ResultRecordedTimestamp>1624869013065</ResultRecordedTimestamp>
            <Annotation>{\"configuration\":\"LRS\",\"desiredValue\":\"ZRS\",\"operator\":\"StringEquals\",\"property\":\"$.DataRedundancyType\"}</Annotation>
            <ConfigRuleInvokedTimestamp>1624869012713</ConfigRuleInvokedTimestamp>
            <InvokingEventMessageType>ScheduledNotification</InvokingEventMessageType>
            <EvaluationResultIdentifier>
                <OrderingTimestamp>1624869012713</OrderingTimestamp>
                <EvaluationResultQualifier>
                    <ConfigRuleArn>acs:config::100931896542****:rule/cr-888f626622af00ae****</ConfigRuleArn>
                    <ResourceType>ACS::OSS::Bucket</ResourceType>
                    <ConfigRuleName>OSS存储空间开启同城冗余存储</ConfigRuleName>
                    <ResourceId>Bucket-test</ResourceId>
                    <ConfigRuleId>cr-888f626622af00ae****</ConfigRuleId>
                    <ResourceName>Bucket-test</ResourceName>
                    <RegionId>cn-hangzhou</RegionId>
                    <CompliancePackId>cr-7263fd26622af00bc****</CompliancePackId>
                </EvaluationResultQualifier>
            </EvaluationResultIdentifier>
            <RemediationEnabled>false</RemediationEnabled>
        </EvaluationResultList>
    </EvaluationResults>
</ListAggregateConfigRuleEvaluationResultsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A6662516-D056-4325-B6A7-CD3E89C97C39",
  "EvaluationResults" : {
    "NextToken" : "IWBjqMYSy0is7zSMGu16****",
    "MaxResults" : 10,
    "EvaluationResultList" : [ {
      "RiskLevel" : 1,
      "ComplianceType" : "NON_COMPLIANT",
      "ResultRecordedTimestamp" : 1624869013065,
      "Annotation" : "{\\\"configuration\\\":\\\"LRS\\\",\\\"desiredValue\\\":\\\"ZRS\\\",\\\"operator\\\":\\\"StringEquals\\\",\\\"property\\\":\\\"$.DataRedundancyType\\\"}",
      "ConfigRuleInvokedTimestamp" : 1624869012713,
      "InvokingEventMessageType" : "ScheduledNotification",
      "EvaluationResultIdentifier" : {
        "OrderingTimestamp" : 1624869012713,
        "EvaluationResultQualifier" : {
          "ConfigRuleArn" : "acs:config::100931896542****:rule/cr-888f626622af00ae****",
          "ResourceType" : "ACS::OSS::Bucket",
          "ConfigRuleName" : "OSS存储空间开启同城冗余存储",
          "ResourceId" : "Bucket-test",
          "ConfigRuleId" : "cr-888f626622af00ae****",
          "ResourceName" : "Bucket-test",
          "RegionId" : "cn-hangzhou",
          "CompliancePackId" : "cr-7263fd26622af00bc****"
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
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|400|Invalid.CompliancePackId.Value|The specified CompliancePackId does not exist.|合规包ID不存在。|
|404|CloudConfigServiceRoleNotExisted|The CloudConfigServiceRole does not exist.|配置审计的服务角色不存在。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

