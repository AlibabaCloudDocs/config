# DescribeConfigRule

Queries the details of a rule.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeConfigRule&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeConfigRule|The operation that you want to perform. Set the value to DescribeConfigRule. |
|ConfigRuleId|String|Yes|cr-2a914fcf617e00c9\*\*\*\*|The ID of the rule. To query the details of a rule that belongs to a member account, set MultiAccount to true and MemberId to the ID of the member account. |
|MultiAccount|Boolean|No|false|Specifies whether to query the details of the rules that belong to the member accounts of the current master account. Valid values:

-   true: Queries the details of the rules that belong to the member accounts in the resource directory of the current master account.
-   false \(default value\): Queries the details of the rules that belong to the current master account.

**Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose rule details you want to query. This parameter is unspecified by default. It is available only when MultiAccount is set to true.

-   If MemberId is unspecified, the system queries the details of the specified rule that belongs to the current master account and its member accounts.
-   If MemberId is specified, the system queries the details of the specified rule that belongs to the specified member account.

**Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A7A0FFF8-0B44-40C6-8BBF-3A185EFDF3D0|The ID of the request. |
|ConfigRule|Struct| |The details of the rule. |
|ConfigRuleArn|String|acs:config::120886317863\*\*\*\*:config-rule/cr-e4b06457e0d900df\*\*\*\*|The Alibaba Cloud Resource Name \(ARN\) of the rule. |
|ConfigRuleEvaluationStatus|Struct| |The status of resource compliance evaluations based on the rule. |
|FirstActivatedTimestamp|Long|1602818958115|The timestamp when the rule was first triggered. |
|FirstEvaluationStarted|Boolean|true|Indicates whether resources were evaluated based on the rule. Valid values:

-   true \(default value\)
-   false |
|LastErrorCode|String|FunctionNotFound|The error code returned for the last failed evaluation. |
|LastErrorMessage|String|function 'funtionName' does not exist in service 'serviceName'|The error message returned for the last failed evaluation. |
|LastFailedEvaluationTimestamp|Long|1602819143913|The timestamp when the last failed evaluation of the rule ended. |
|LastFailedInvocationTimestamp|Long|1602819143910|The timestamp when the last failed invocation of the rule started. |
|LastSuccessfulEvaluationTimestamp|Long|1602818964889|The timestamp when the last successful evaluation of the rule ended. |
|LastSuccessfulInvocationTimestamp|Long|1602818964884|The timestamp when the last successful invocation of the rule started. |
|ConfigRuleId|String|cr-2a914fcf617e00c9\*\*\*\*|The ID of the rule. |
|ConfigRuleName|String|rds-cpu-min-count-limit-rd|The name of the rule. |
|ConfigRuleState|String|ACTIVE|The status of the rule. Valid values:

-   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|CreateBy|Struct| |The information of the created rule. |
|ConfigRuleSceneId|String|level3\_protection|The ID of the scenario in which the rule was created.

**Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|ConfigRuleSceneName|String|level3\_protection|The name of the scenario in which the rule was created.

**Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorId|String|level3\_protection|The ID of the account that was used to create the rule.

**Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorName|String|level3\_protection|The name of the account that was used to create the rule.

**Note:** A value is returned for this parameter if CreatorType is set to CONFIG\_RULE\_SCENE. |
|CreatorType|String|CONFIG\_RULE\_SCENE|The type of the rule creator. Valid values:

-   RESOURCE\_DIRECTORY: indicates a master account. If you are using Cloud Config for Enterprise, you can create rules by using a master account.
-   CONFIG\_RULE\_SCENE: indicates the system. If you are using Cloud Config for individuals, the system automatically creates rules in specific scenarios, such as classified protection precheck, OSS compliance baseline, and CIS compliance check. |
|CreateTimestamp|Long|1602818964884|The timestamp when the rule was created. |
|Description|String|This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.|The description of the rule. |
|InputParameters|Map|\{"cpuCount": "2" \}|The settings of the input parameters for the rule. |
|ManagedRule|Struct| |The details of the managed rule. |
|CompulsoryInputParameterDetails|Map|\{"cpuCount":\{"type":"integer","defaultValue":"2"\}\}|The details of the required parameters for the managed rule. |
|Description|String|This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.|The description of the managed rule. |
|Identifier|String|rds-cpu-min-count-limit|The identifier of the managed rule. |
|Labels|List|\["RDS","CPU"\]|The tags of the managed rule. |
|ManagedRuleName|String|rds-cpu-min-count-limit|The name of the managed rule. |
|OptionalInputParameterDetails|Map|\{"tag1Value":\{"type":"string","defaultValue":""\},"tag2Key":\{"type":"string","defaultValue":""\}\}|The details of the optional parameters for the managed rule. |
|SourceDetails|Array of SourceDetails| |The details of the managed rule. |
|EventSource|String|aliyun.config|The event source of the rule.

**Note:** Only events related to Cloud Config are supported. Set the value to aliyun.config. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

-   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|MessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

-   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

-   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|ModifiedTimestamp|Long|1602992721000|The last timestamp when the rule was modified. |
|RiskLevel|Integer|1|The risk level of the resources that are not compliant with the rule. Valid values:

-   1: high risk
-   2: medium risk
-   3: low risk |
|Scope|Struct| |The monitoring scope of the rule. |
|ComplianceResourceId|String|vpc-6weoy5flv41pj4wvr\*\*\*\*|The ID of the resource to be evaluated.

**Note:** If this parameter returns a null value, the rule evaluates all the resources of the specified type. |
|ComplianceResourceTypes|List|\["ACS::RDS::DBInstance"\]|The types of the resources to be evaluated. |
|Source|Struct| |The information about the trigger of the rule. |
|Identifier|String|rds-cpu-min-count-limit|The identifier of the rule.

-   For a managed rule, the value is the name of the managed rule.
-   For a custom rule, the value is the ARN of the custom rule. |
|Owner|String|ALIYUN|Indicates the owner of the rule. Valid values:

-   CUSTOM\_FC: The rule is a custom rule that you own.
-   ALIYUN: The rule is a managed rule of Alibaba Cloud. |
|SourceConditions|Array of SourceConditions| |The trigger conditions configured for the rule.

**Note:** This parameter is valid only for rules whose execution method is set to Visual Editor. |
|DesiredValue|String|1|The expected value of the input parameter for the rule. |
|Name|String|status|The name of the input parameter for the rule. |
|Operator|String|Equals|The operator used to compare the actual value with the input parameter value of the rule. The operator varies based on the type of data returned for the SelectPath parameter.

-   Valid values for the String data type:
    -   StringEquals: The actual value is equal to the input parameter value.
    -   NotStringEquals: The actual value is not equal to the input parameter value.
    -   StringIn: The actual value exists in the input parameter value.
    -   NotStringIn: The actual value does not exist in the input parameter value.
    -   StringContains: The actual value contains the input parameter value.
    -   NotStringContains: The actual value does not contain the input parameter value.
-   Valid values for the Number data type:
    -   Equals: The actual value is equal to the input parameter value.
    -   NotEquals: The actual value is not equal to the input parameter value.
    -   Less: The actual value is less than the input parameter value.
    -   LessOrEquals: The actual value is less than or equal to the input parameter value.
    -   Greater: The actual value is greater than the input parameter value.
    -   GreaterOrEquals: The actual value is greater than or equal to the input parameter value.
-   Valid values for the Base64String data type that indicates a Base64-encoded string:
    -   Base64Contains: The actual value contains the input parameter value.
    -   NotBase64Contains: The actual value does not contain the input parameter value.
    -   Base64ContainsAll: The actual value contains all elements of the input parameter value.
    -   Base64ExcludeAll: The actual value excludes all elements of the input parameter value.
-   Valid values for the Array data type:
    -   Contains: The actual value contains the input parameter value.
    -   NotContains: The actual value does not contain the input parameter value.
    -   In: The actual value exists in the input parameter value.
    -   NotIn: The actual value does not exist in the input parameter value.
    -   ContainsAll: The actual value contains all elements of the input parameter value.
    -   ExcludeAll: The actual value excludes all elements of the input parameter value.
    -   IsEmpty: The actual value is null. |
|Tips|String|Instance status|The description of the input parameter. |
|SourceDetails|Array of SourceDetails| |The source details of the rule. |
|EventSource|String|aliyun.config|The event source of the rule.

**Note:** Only events related to Cloud Config are supported. Set the value to aliyun.config. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

-   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|MessageType|String|ScheduledNotification|The trigger type of the rule. Valid values:

-   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeConfigRule
&ConfigRuleId=cr-2a914fcf617e00c9****
&<common request parameters>
```

Sample responses

`XML` format

```
<DescribeConfigRuleResponse>
      <RequestId>F63DFAFD-CE84-495D-A800-9E94B22C2346</RequestId>
      <ConfigRule>
            <ManagedRule>
                  <ManagedRuleName>rds-desired-instance-type</ManagedRuleName>
                  <Description>This rule is evaluated to be compliant if all types of ApsaraDB RDS instances are included in the parameter value. </Description>
                  <Identifier>rds-desired-instance-type</Identifier>
                  <CompulsoryInputParameterDetails>
                        <instanceTypes>
                              <defaultValue>rds.mysql.s2.large</defaultValue>
                              <description>instance type</description>
                              <type>string</type>
                        </instanceTypes>
                  </CompulsoryInputParameterDetails>
                  <Labels>RDS</Labels>
                  <SourceDetails>
                        <EventSource>aliyun.config</EventSource>
                        <MessageType>ConfigurationItemChangeNotification</MessageType>
                  </SourceDetails>
                  <HelpUrl>https://www.alibabacloud.com/help/doc-detail/147676.htm#title-rt6-m9w-a52</HelpUrl>
            </ManagedRule>
            <Description>This rule is evaluated to compliant if all types of ApsaraDB RDS instances are included in the parameter value. </Description>
            <ConfigRuleEvaluationStatus>
                  <FirstActivatedTimestamp>1602818958115</FirstActivatedTimestamp>
                  <LastSuccessfulEvaluationTimestamp>1602818964884</LastSuccessfulEvaluationTimestamp>
                  <FirstEvaluationStarted>false</FirstEvaluationStarted>
            </ConfigRuleEvaluationStatus>
            <ConfigRuleState>ACTIVE</ConfigRuleState>
            <Source>
                  <Owner>ALIYUN</Owner>
                  <Identifier>rds-desired-instance-type</Identifier>
                  <SourceConditions>
                        <Operator>In</Operator>
                        <DesiredValue>rds.mysql.s2.large</DesiredValue>
                        <Required>true</Required>
                        <SelectPath>$.DBInstanceClass</SelectPath>
                  </SourceConditions>
                  <SourceDetails>
                        <EventSource>aliyun.config</EventSource>
                        <MessageType>ConfigurationItemChangeNotification</MessageType>
                  </SourceDetails>
            </Source>
            <ConfigRuleId>cr-138e6457e0d90072cc14</ConfigRuleId>
            <Scope>
                  <ComplianceResourceTypes>ACS::RDS::DBInstance</ComplianceResourceTypes>
            </Scope>
            <ConfigRuleArn>acs:config::1208863178612953:config-rule/cr-138e6457e0d90072cc14</ConfigRuleArn>
            <ConfigRuleName>rds-desired-instance-type</ConfigRuleName>
            <RiskLevel>1</RiskLevel>
            <InputParameters>
                  <instanceTypes>rds.mysql.s2.large</instanceTypes>
            </InputParameters>
      </ConfigRule>
</DescribeConfigRuleResponse>
```

`JSON` format

```
{
    "RequestId": "F63DFAFD-CE84-495D-A800-9E94B22C2346",
    "ConfigRule": {
        "ManagedRule": {
            "ManagedRuleName": "rds-desired-instance-type",
            "Description": "This rule is evaluated to be compliant if all types of ApsaraDB RDS instances are included in the parameter value.",
            "Identifier": "rds-desired-instance-type",
            "CompulsoryInputParameterDetails": {
                "instanceTypes": {
                    "defaultValue": "rds.mysql.s2.large",
                    "description": "instance type",
                    "type": "string"
                }
            },
            "Labels": [
                "RDS"
            ],
            "SourceDetails": [
                {
                    "EventSource": "aliyun.config",
                    "MessageType": "ConfigurationItemChangeNotification"
                }
            ],
            "HelpUrl": "https://www.alibabacloud.com/help/doc-detail/147676.htm#title-rt6-m9w-a52"
        },
        "Description": "This rule is evaluated to compliant if all types of ApsaraDB RDS instances are included in the parameter value.",
        "ConfigRuleEvaluationStatus": {
            "FirstActivatedTimestamp": 1602818958115,
            "LastSuccessfulEvaluationTimestamp": 1602818964884,
            "FirstEvaluationStarted": false
        },
        "ConfigRuleState": "ACTIVE",
        "Source": {
            "Owner": "ALIYUN",
            "Identifier": "rds-desired-instance-type",
            "SourceConditions": [
                {
                    "Operator": "In",
                    "DesiredValue": "rds.mysql.s2.large",
                    "Required": true,
                    "SelectPath": "$.DBInstanceClass"
                }
            ],
            "SourceDetails": [
                {
                    "EventSource": "aliyun.config",
                    "MessageType": "ConfigurationItemChangeNotification"
                }
            ]
        },
        "ConfigRuleId": "cr-138e6457e0d90072cc14",
        "Scope": {
            "ComplianceResourceTypes": [
                "ACS::RDS::DBInstance"
            ]
        },
        "ConfigRuleArn": "acs:config::1208863178612953:config-rule/cr-138e6457e0d90072cc14",
        "ConfigRuleName": "rds-desired-instance-type",
        "RiskLevel": 1,
        "InputParameters": {
            "instanceTypes": "rds.mysql.s2.large"
        }
    }
}
```

## Errors codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|The error message returned because the specified rule does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

