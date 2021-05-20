# DescribeConfigRule

Queries the details of a rule.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeConfigRule&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeConfigRule|The operation that you want to perform. Set the value to **DescribeConfigRule**. |
|ConfigRuleId|String|Yes|cr-7bc06457e0d90041\*\*\*\*|The ID of the rule. |
|MultiAccount|Boolean|No|false|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|Long|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99|The ID of the request. |
|ConfigRule|Object| |The details of the rule. |
|RiskLevel|Integer|3|The risk level of the resources that are not compliant with the rule. Valid values:

 -   1: high risk
-   2: medium risk
-   3: low risk |
|InputParameters|Map| |The settings of the input parameters for the rule. |
|Source|Object| |The information about the trigger of the rule. |
|SourceDetails|Array of SourceDetails| |The source details of the rule. |
|MessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|EventSource|String|aliyun.config|The event source of the rule.

 **Note:** Only events related to Cloud Config are supported. Set the value to aliyun.config. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

 -   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|Owner|String|ALIYUN|Indicates whether you or Alibaba Cloud owns and manages the rule. Valid values:

 -   CUSTOM\_FC: The rule is a custom rule that you own.
-   ALIYUN: The rule is a managed rule of Alibaba Cloud. |
|SourceConditions|Array of SourceConditions| |The trigger conditions configured for the rule. |
|DesiredValue|String|2|The expected value of the input parameter for the rule. |
|Tips|String|Instance status|The description of the input parameter. |
|Operator|String|GreaterOrEquals|The operator used to compare the actual value with the input parameter value of the rule. The operator varies based on the type of data returned for the SelectPath parameter.

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
|Name|String|cpuCount|The name of the input parameter for the rule. |
|Identifier|String|rds-cpu-min-count-limit|The identifier of the rule.

 -   For a managed rule, the value is the name of the managed rule.
-   For a custom rule, the value is the Alibaba Cloud Resource Name \(ARN\) of the custom rule. |
|ConfigRuleState|String|ACTIVE|The status of the rule. Valid values:

 -   ACTIVE: The rule is being used to monitor resource configurations.
-   EVALUATING: The rule is triggered and is being used to evaluate the compliance of resources.
-   INACTIVE: The rule is disabled and is no longer used to monitor resource configurations. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

 -   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|ManagedRule|Object| |The details of the managed rule. |
|SourceDetails|Array of SourceDetails| |The details of the managed rule. |
|MessageType|String|ConfigurationItemChangeNotification|The trigger type of the rule. Valid values:

 -   ConfigurationItemChangeNotification: The rule is triggered by configuration changes.
-   ScheduledNotification: The rule is triggered as scheduled. |
|EventSource|String|aliyun.config|The event source of the rule.

 **Note:** Only events related to Cloud Config are supported. Set the value to aliyun.config. |
|MaximumExecutionFrequency|String|Six\_Hours|The frequency at which the rule is executed. Valid values:

 -   One\_Hour: 1 hour
-   Three\_Hours: 3 hours
-   Six\_Hours: 6 hours
-   Twelve\_Hours: 12 hours
-   TwentyFour\_Hours: 24 hours |
|Description|String|This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.|The description of the managed rule. |
|Labels|Array of String|\["RDS","CPU"\]|The tags of the managed rule. |
|Identifier|String|rds-cpu-min-count-limit|The identifier of the managed rule. |
|OptionalInputParameterDetails|Map| |The details of the optional parameters for the managed rule. |
|ManagedRuleName|String|rds-cpu-min-count-limit|The name of the managed rule. |
|CompulsoryInputParameterDetails|Map| |The details of the required parameters for the managed rule. |
|ConfigRuleArn|String|acs:config::120886317861\*\*\*\*:rule/cr-7bc06457e0d90041\*\*\*\*|The ARN of the rule. |
|Description|String|This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.|The description of the rule. |
|ConfigRuleName|String|The number of CPU cores for each ApsaraDB RDS instance within your account meets the minimum requirements.|The name of the rule. |
|Scope|Object| |The monitoring scope of the rule. |
|ComplianceResourceTypes|Array of String|\["ACS::RDS::DBInstance"\]|The types of the resources to be evaluated. |
|ComplianceResourceId|String|vpc-6weoy5flv41pj4wvr\*\*\*\*|The ID of the resource to be evaluated. |
|ConfigRuleEvaluationStatus|Object| |The status of resource compliance evaluations based on the rule. |
|LastErrorCode|String|FunctionNotFound|The error code returned for the last failed evaluation. |
|LastSuccessfulEvaluationTimestamp|Long|1618901957876|The timestamp when the last successful evaluation of the rule ended. |
|FirstActivatedTimestamp|Long|1618901952341|The timestamp when the rule was first triggered. |
|FirstEvaluationStarted|Boolean|true|Indicates whether resources were evaluated based on the rule. Valid values:

 -   true \(default value\)
-   false |
|LastSuccessfulInvocationTimestamp|Long|1618901957395|The timestamp when the last successful invocation of the rule started. |
|LastErrorMessage|String|function 'funtionName' does not exist in service 'serviceName'|The error message returned for the last failed evaluation. |
|LastFailedEvaluationTimestamp|Long|1602819143913|The timestamp when the last failed evaluation of the rule ended. |
|LastFailedInvocationTimestamp|Long|1602819143910|The timestamp when the last failed invocation of the rule started. |
|ConfigRuleId|String|cr-7bc06457e0d90041\*\*\*\*|The ID of the rule. |
|ModifiedTimestamp|Long|1602992721000|The last timestamp when the rule was modified. |
|CreateTimestamp|Long|1602818964884|The timestamp when the rule was created. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=DescribeConfigRule
&ConfigRuleId=cr-7bc06457e0d90041****
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeConfigRuleResponse>
	<RequestId>A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99</RequestId>
	<ConfigRule>
		<ManagedRule>
			<ManagedRuleName>rds-cpu-min-count-limit</ManagedRuleName>
			<OptionalInputParameterDetails />
			This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold. </Description>
			<Identifier>rds-cpu-min-count-limit</Identifier>
			<CompulsoryInputParameterDetails>
				<cpuCount>
					<defaultValue>2</defaultValue>
					<type>integer</type>
				</cpuCount>
			</CompulsoryInputParameterDetails>
			<Labels>RDS</Labels>
			<Labels>CPU</Labels>
			<SourceDetails>
				<EventSource>aliyun.config</EventSource>
				<MessageType>ConfigurationItemChangeNotification</MessageType>
			</SourceDetails>
		</ManagedRule>
		<ConfigRuleEvaluationStatus>
			<FirstActivatedTimestamp>1618901952341</FirstActivatedTimestamp>
			<LastSuccessfulEvaluationTimestamp>1618901957876</LastSuccessfulEvaluationTimestamp>
			<FirstEvaluationStarted>true</FirstEvaluationStarted>
			<LastSuccessfulInvocationTimestamp>1618901957395</LastSuccessfulInvocationTimestamp>
		</ConfigRuleEvaluationStatus>
		<ConfigRuleState>ACTIVE</ConfigRuleState>
		<Source>
			<Owner>ALIYUN</Owner>
			<Identifier>rds-cpu-min-count-limit</Identifier>
			<SourceConditions>
				<Operator>GreaterOrEquals</Operator>
				<DesiredValue>2</DesiredValue>
				<Required>true</Required>
				<SelectPath>$.DBInstanceCPU</SelectPath>
			</SourceConditions>
			<SourceDetails>
				<EventSource>aliyun.config</EventSource>
				<MessageType>ConfigurationItemChangeNotification</MessageType>
			</SourceDetails>
		</Source>
		<OrganizationRule>false</OrganizationRule>
		<ConfigRuleId>cr-7bc06457e0d90041****</ConfigRuleId>
		<Scope>
			<ComplianceResourceTypes>ACS::RDS::DBInstance</ComplianceResourceTypes>
		</Scope>
		<ConfigRuleArn>acs:config::120886317861****:rule/cr-7bc06457e0d90041****</ConfigRuleArn>
		<ConfigRuleName>The number of CPU cores for each ApsaraDB RDS instance within your account meets the minimum requirements</ConfigRuleName>
		<RiskLevel>3</RiskLevel>
		<InputParameters>
			<cpuCount>2</cpuCount>
		</InputParameters>
	</ConfigRule>
</DescribeConfigRuleResponse>
```

`JSON` format

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A68DD98C-DE65-46AC-B2D2-04A4A9AB5B99",
  "ConfigRule" : {
    "ManagedRule" : {
      "ManagedRuleName" : "rds-cpu-min-count-limit",
      "OptionalInputParameterDetails" : { },
      "Description": "This rule is evaluated to be compliant if the number of CPU cores for each ApsaraDB RDS instance within your account is greater than or equal to a specified threshold.",
      "Identifier" : "rds-cpu-min-count-limit",
      "CompulsoryInputParameterDetails" : {
        "cpuCount" : {
          "defaultValue" : "2",
          "type" : "integer"
        }
      },
      "Labels" : [ "RDS", "CPU" ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "ConfigRuleEvaluationStatus" : {
      "FirstActivatedTimestamp" : 1618901952341,
      "LastSuccessfulEvaluationTimestamp" : 1618901957876,
      "FirstEvaluationStarted" : true,
      "LastSuccessfulInvocationTimestamp" : 1618901957395
    },
    "ConfigRuleState" : "ACTIVE",
    "Source" : {
      "Owner" : "ALIYUN",
      "Identifier" : "rds-cpu-min-count-limit",
      "SourceConditions" : [ {
        "Operator" : "GreaterOrEquals",
        "DesiredValue" : "2",
        "Required" : true,
        "SelectPath" : "$.DBInstanceCPU"
      } ],
      "SourceDetails" : [ {
        "EventSource" : "aliyun.config",
        "MessageType" : "ConfigurationItemChangeNotification"
      } ]
    },
    "OrganizationRule" : false,
    "ConfigRuleId" : "cr-7bc06457e0d90041****",
    "Scope" : {
      "ComplianceResourceTypes" : [ "ACS::RDS::DBInstance" ]
    },
    "ConfigRuleArn" : "acs:config::120886317861****:rule/cr-7bc06457e0d90041****",
    "ConfigRuleName": "The number of CPU cores for each ApsaraDB RDS instance within your account meets the minimum requirements.",
    "RiskLevel" : 3,
    "InputParameters" : {
      "cpuCount" : "2"
    }
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|ConfigRuleNotExists|The ConfigRule does not exist.|The error message returned because the specified rule does not exist.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

