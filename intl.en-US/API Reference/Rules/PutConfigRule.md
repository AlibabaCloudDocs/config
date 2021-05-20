# PutConfigRule

Creates or modifies a rule.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=PutConfigRule&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|PutConfigRule|The operation that you want to perform. Set the value to **PutConfigRule**. |
|ConfigRuleId|String|No|cr-2a914fcf617e00c9\*\*\*\*|The ID of the rule. |
|ConfigRuleName|String|Yes|The number of CPU cores for each ApsaraDB RDS instance within your account meets the minimum requirements.|The name of the rule. |
|Description|String|No|This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.|The description of the rule. |
|InputParameters|String|No|\{"cpuCount": "2"\}|The settings of the input parameters for the rule. |
|SourceOwner|String|Yes|ALIYUN|Indicates whether you or Alibaba Cloud owns and manages the rule. Valid values:

 -   CUSTOM\_FC: The rule is a custom rule that you own.
-   ALIYUN: The rule is a managed rule of Alibaba Cloud. |
|SourceIdentifier|String|Yes|rds-cpu-min-count-limit|The identifier of the rule.

 -   For a managed rule, the value is the name of the managed rule.
-   For a custom rule, the value is the Alibaba Cloud Resource Name \(ARN\) of the custom rule. |
|SourceDetailMessageType|String|Yes|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|SourceMaximumExecutionFrequency|String|No|Twelve\_Hours|The frequency at which the rule is executed. Valid values:

 -   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|ScopeComplianceResourceId|String|No|vpc-6weoy5flv41pj4wvr\*\*\*\*|The ID of the resource to be evaluated.

 -   If you do not set this parameter, the rule evaluates resources of all the types specified by ScopeComplianceResourceTypes.
-   If you specify a resource ID, the rule evaluates the resource identified by the ID. |
|ScopeComplianceResourceTypes|String|Yes|\["ACS::RDS::DBInstance"\]|The types of the resources to be evaluated. |
|RiskLevel|Integer|Yes|1|The risk level of the non-compliant resource. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|ClientToken|String|No|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can contain only ASCII characters and cannot exceed 64 characters in length. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConfigRuleId|String|cr-76ac4fcfb57e00c9\*\*\*\*|The ID of the rule. |
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=PutConfigRule
&ConfigRuleName=The number of CPU cores for each ApsaraDB RDS instance within your account meets the minimum requirements.
&RiskLevel=1
&ScopeComplianceResourceTypes=["ACS::RDS::DBInstance"]
&SourceDetailMessageType=ConfigurationItemChangeNotification
&SourceIdentifier=rds-cpu-min-count-limit
&SourceOwner=ALIYUN
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<PutConfigRuleResponse>
	<ConfigRuleId>cr-76ac4fcfb57e00c9****</ConfigRuleId>
	<RequestId>A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7</RequestId>
</PutConfigRuleResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ConfigRuleId" : "cr-76ac4fcfb57e00c9****",
  "RequestId" : "A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3F7"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|ExceedMaxRuleCount|The maximum number of rules is exceeded.|The error message returned because the number of created rules has reached the upper limit.|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|The error message returned because the specified rule does not exist.|
|400|ConfigRuleExists|The ConfigRule already exists.|The error message returned because the name of the rule already exists.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

