# GetAggregateConfigRule

调用GetAggregateConfigRule接口查询指定账号组内指定规则详情。

本文将提供一个示例，查询账号组`ca-7f00626622af0041****`内规则`cr-7f7d626622af0041****`的详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetAggregateConfigRule&type=RPC&version=2020-09-07)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAggregateConfigRule|要执行的操作，取值：**GetAggregateConfigRule**。 |
|ConfigRuleId|String|是|cr-7f7d626622af0041\*\*\*\*|规则ID。

关于如何获取规则ID，请参见[ListAggregateConfigRules](~~264148~~)。 |
|AggregatorId|String|是|ca-7f00626622af0041\*\*\*\*|账号组ID。

关于如何获取账号组ID，请参见[ListAggregators](~~255797~~)。 |

关于公共请求参数的详情，请参见[公共参数](~~251751~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|811234F4-C3AB-4D15-B90B-F55016D1B5AA|请求ID。 |
|ConfigRule|Object| |规则列表。 |
|RiskLevel|Integer|1|规则风险等级。取值：

-   1：高风险。
-   2：中风险。
-   3：低风险。 |
|InputParameters|Map| |规则参数信息。 |
|Source|Object| |规则来源信息。 |
|SourceDetails|Array of SourceDetails| |规则来源详情。 |
|MessageType|String|ConfigurationItemChangeNotification|规则触发机制。取值：

-   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EventSource|String|aliyun.config|事件来源。

**说明：** 目前仅支持配置审计事件：aliyun.config。 |
|MaximumExecutionFrequency|String|One\_Hour|规则执行周期。取值：

-   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|Owner|String|ALIYUN|规则来源的归属。取值：

-   CUSTOM\_FC：自定义规则。
-   ALIYUN：托管规则。 |
|SourceConditions|Array of SourceConditions| |规则执行条件。 |
|DesiredValue|String|True|规则参数值。 |
|Tips|String|ECS的实例规格|规则参数提示信息。 |
|Operator|String|StringEqualsIn|规则参数操作符。不同数据类型对应不同的操作符。取值：

-   当数据类型为String时，取值：
    -   StringEquals：等于。
    -   NotStringEquals：不等于。
    -   StringIn：存在。
    -   NotStringIn：不存在。
    -   StringContains：包含。
    -   NotStringContains：不包含。
-   当数据类型为Number时，取值：
    -   Equals：等于。
    -   NotEquals：不等于。
    -   Less：小于。
    -   LessOrEquals：小于等于。
    -   Greater：大于。
    -   GreaterOrEquals：大于等于。
-   当数据类型为基于Base64进制编码的Base64 String时，取值：
    -   Base64Contains：包含。
    -   NotBase64Contains：不包含。
    -   Base64ContainsAll：包含全部。
    -   Base64ExcludeAll：排除全部。
-   当数据类型为Array时，取值：
    -   Contains：包含。
    -   NotContains：不包含。
    -   In：存在。
    -   NotIn：不存在。
    -   ContainsAll：包含全部。
    -   ExcludeAll：排除全部。
    -   IsEmpty：为空。 |
|Name|String|instanceTypes|规则参数名称。 |
|Identifier|String|acs:fc:cn-hangzhou:100931896542\*\*\*\*:services/ConfigService.LATEST/functions/specific-config|规则标识。

-   如果是托管规则，该参数为托管规则标识。
-   如果是自定义规则，该参数为函数ARN。 |
|ConfigRuleState|String|ACTIVE|规则运行状态。取值：

-   ACTIVE：应用中。
-   DELETING：删除中。
-   EVALUATING：评估中。
-   INACTIVE：已停用。 |
|MaximumExecutionFrequency|String|One\_Hour|规则执行周期。

-   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|ManagedRule|Object| |托管规则详情。 |
|SourceDetails|Array of SourceDetails| |托管规则来源详情。 |
|MessageType|String|ConfigurationItemChangeNotification|规则触发机制。取值：

-   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |
|EventSource|String|aliyun.config|事件来源。

**说明：** 目前仅支持配置审计事件：aliyun.config。 |
|MaximumExecutionFrequency|String|One\_Hour|规则执行周期。

-   One\_Hour：1小时。
-   Three\_Hours：3小时。
-   Six\_Hours：6小时。
-   Twelve\_Hours：12小时。
-   TwentyFour\_Hours：24小时。 |
|Description|String|ECS磁盘未因欠费或安全等原因而被锁定，视为“合规”。|托管规则描述。 |
|Labels|Array of String|\["RAM","USer"\]|托管规则标签。 |
|Identifier|String|ram-user-mfa-check|托管规则标识。 |
|OptionalInputParameterDetails|Map| |托管规则可选参数详情。 |
|ManagedRuleName|String|RAM用户开启MFA|托管规则名称。 |
|CompulsoryInputParameterDetails|Map| |托管规则必选参数详情。 |
|ConfigRuleArn|String|acs:config::100931896542\*\*\*\*:rule/cr-7f7d626622af0041\*\*\*\*|托管规则ARN。 |
|Description|String|RAM用户开启MFA，视为“合规”。|托管规则描述。 |
|CreateBy|Object| |规则创建者信息。 |
|CompliancePackId|String|cp-541e626622af008\*\*\*\*|合规包ID。 |
|AggregatorName|String|Test\_Group|账号组名称。 |
|CompliancePackName|String|OSS合规基线|合规包名称。 |
|CreatorName|String|Alice|规则创建者名称。 |
|CreatorType|String|AGGREGATOR|规则创建者类型。仅支持AGGREGATOR（账号组）。 |
|CreatorId|String|100931896542\*\*\*\*|规则创建者的账号ID。 |
|AggregatorId|String|ca-04b3fd170e340007\*\*\*\*|账号组ID。 |
|ConfigRuleName|String|RAM用户开启MFA|规则名称。 |
|ConfigRuleEvaluationStatus|Object| |规则执行状态。 |
|LastErrorCode|String|TimeOut|规则最近一次执行的错误码。 |
|LastSuccessfulEvaluationTimestamp|Long|1624932227486|规则最近一次调用成功的结束时间戳。单位：毫秒。 |
|FirstActivatedTimestamp|Long|1624932221993|规则首次激活时间戳。 |
|FirstEvaluationStarted|Boolean|true|规则是否已执行过评估。取值：

-   true
-   false |
|LastSuccessfulInvocationTimestamp|Long|1624932227476|规则最近一次调用成功的开始时间戳。单位：毫秒。 |
|LastErrorMessage|String|time out|规则最近一次执行的错误信息。 |
|LastFailedEvaluationTimestamp|Long|1614687022000|规则最近一次调用失败的结束时间戳。单位：毫秒。 |
|LastFailedInvocationTimestamp|Long|1614687022000|规则最近一次调用失败的开始时间戳。单位：毫秒。 |
|ConfigRuleId|String|cr-7f7d626622af0041\*\*\*\*|规则ID。 |
|ModifiedTimestamp|Long|1614687022000|规则最近一次更新的时间戳。单位：毫秒。 |
|CreateTimestamp|Long|1604684022000|创建规则的时间戳。单位：毫秒。 |
|ResourceTypesScope|String|ACS::RAM::User|规则评估的资源类型。 |
|RegionIdsScope|String|global|规则只评估所属地域ID的资源。 |
|ExcludeResourceIdsScope|String|23642660635687\*\*\*\*|规则评估排除的资源ID。 |
|ResourceGroupIdsScope|String|rg-aekzdibsjjc\*\*\*\*|规则只评估所属资源组ID的资源。 |
|TagKeyScope|String|RAM|规则只评估所属标签键的资源。 |
|TagValueScope|String|MFA|规则只评估所属标签值的资源。 |
|ConfigRuleTriggerTypes|String|ConfigurationItemChangeNotification|规则触发机制。取值：

-   ConfigurationItemChangeNotification：配置变更。
-   ScheduledNotification：周期执行。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetAggregateConfigRule
&ConfigRuleId=cr-7f7d626622af0041****
&AggregatorId=ca-7f00626622af0041****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetAggregateConfigRuleResponse>
    <RequestId>811234F4-C3AB-4D15-B90B-F55016D1B5AA</RequestId>
    <ConfigRule>
        <ManagedRule>
            <ManagedRuleName>RAM用户开启MFA</ManagedRuleName>
            <OptionalInputParameterDetails />
            <Description>RAM用户开启MFA，视为“合规”。</Description>
            <Identifier>ram-user-mfa-check</Identifier>
            <CompulsoryInputParameterDetails />
            <Labels>RAM</Labels>
            <Labels>USer</Labels>
            <SourceDetails>
                <EventSource>aliyun.config</EventSource>
                <MessageType>ConfigurationItemChangeNotification</MessageType>
            </SourceDetails>
        </ManagedRule>
        <Description>RAM用户开启MFA，视为“合规”。</Description>
        <CreateBy>
            <CreatorId>100931896542****</CreatorId>
            <CreatorType>AGGREGATOR</CreatorType>
            <CreatorName>Alice</CreatorName>
            <AggregatorName>Test_Group</AggregatorName>
            <AggregatorId>ca-04b3fd170e340007****</AggregatorId>
        </CreateBy>
        <ConfigRuleEvaluationStatus>
            <LastSuccessfulEvaluationTimestamp>1624932227486</LastSuccessfulEvaluationTimestamp>
            <FirstActivatedTimestamp>1624932221993</FirstActivatedTimestamp>
            <FirstEvaluationStarted>true</FirstEvaluationStarted>
            <LastSuccessfulInvocationTimestamp>1624932227476</LastSuccessfulInvocationTimestamp>
        </ConfigRuleEvaluationStatus>
        <ConfigRuleState>ACTIVE</ConfigRuleState>
        <Source>
            <Owner>ALIYUN</Owner>
            <Identifier>ram-user-mfa-check</Identifier>
            <SourceConditions>
                <Operator>StringEquals</Operator>
                <DesiredValue>True</DesiredValue>
                <Required>true</Required>
            </SourceConditions>
            <SourceDetails>
                <EventSource>aliyun.config</EventSource>
                <MessageType>ConfigurationItemChangeNotification</MessageType>
            </SourceDetails>
        </Source>
        <ConfigRuleId>cr-7f7d626622af0041****</ConfigRuleId>
        <Scope>
            <ComplianceResourceTypes>ACS::RAM::User</ComplianceResourceTypes>
        </Scope>
        <ConfigRuleArn>acs:config::100931896542****:rule/cr-7f7d626622af0041****</ConfigRuleArn>
        <ConfigRuleTriggerTypes>ConfigurationItemChangeNotification</ConfigRuleTriggerTypes>
        <ConfigRuleName>RAM用户开启MFA</ConfigRuleName>
        <RiskLevel>1</RiskLevel>
        <ResourceTypesScope>ACS::RAM::User</ResourceTypesScope>
        <InputParameters>
            <tag1Key>RAM</tag1Key>
            <tag1Value>test</tag1Value>
        </InputParameters>
    </ConfigRule>
</GetAggregateConfigRuleResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "811234F4-C3AB-4D15-B90B-F55016D1B5AA",
  "ConfigRule" : {
    "ManagedRule" : {
      "ManagedRuleName" : "RAM用户开启MFA",
      "OptionalInputParameterDetails" : { },
      "Description" : "RAM用户开启MFA，视为“合规”。",
      "Identifier" : "ram-user-mfa-check",
      "CompulsoryInputParameterDetails" : { },
      "Labels" : [ "RAM", "USer" ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "Description" : "RAM用户开启MFA，视为“合规”。",
    "CreateBy" : {
      "CreatorId" : "100931896542****",
      "CreatorType" : "AGGREGATOR",
      "CreatorName" : "Alice",
      "AggregatorName" : "Test_Group",
      "AggregatorId" : "ca-04b3fd170e340007****"
    },
    "ConfigRuleEvaluationStatus" : {
      "LastSuccessfulEvaluationTimestamp" : 1624932227486,
      "FirstActivatedTimestamp" : 1624932221993,
      "FirstEvaluationStarted" : true,
      "LastSuccessfulInvocationTimestamp" : 1624932227476
    },
    "ConfigRuleState" : "ACTIVE",
    "Source" : {
      "Owner" : "ALIYUN",
      "Identifier" : "ram-user-mfa-check",
      "SourceConditions" : [ {
        "Operator" : "StringEquals",
        "DesiredValue" : "True",
        "Required" : true
      } ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "ConfigRuleId" : "cr-7f7d626622af0041****",
    "Scope" : {
      "ComplianceResourceTypes" : [ "ACS::RAM::User" ]
    },
    "ConfigRuleArn" : "acs:config::100931896542****:rule/cr-7f7d626622af0041****",
    "ConfigRuleTriggerTypes" : "ConfigurationItemChangeNotification",
    "ConfigRuleName" : "RAM用户开启MFA",
    "RiskLevel" : 1,
    "ResourceTypesScope" : "ACS::RAM::User",
    "InputParameters" : {
      "tag1Key" : "RAM",
      "tag1Value" : "test"
    }
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|此规则不存在。|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.AggregatorId.Value|The specified AggregatorId is invalid.|账号组ID不存在或无权限使用该账号组。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

