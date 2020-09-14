# Permission verification

This topic describes the API operations that can be authorized in Cloud Config and the Alibaba Cloud Resource Name \(ARN\) format of the resources involved in each API operation.

Before an API operation is called, permissions are verified to ensure that the caller is authorized to call the API operation to manage specific resources.

The following table describes the API operations that can be authorized in Cloud Config and the ARN format of the resources involved in each API operation.

|Operation|ARN format|
|:--------|:---------|
|config:StartConfigurationRecorder|`acs:config:${region}:${AccountId}:*`|
|config:DescribeConfigurationRecorder|`acs:config:${region}:${AccountId}:*`|
|config:GetDiscoveredResourceCounts|`acs:config:${region}:${AccountId}:*`|
|config:GetSupportedResourceTypes|`acs:config:${region}:${AccountId}:*`|
|config:ListDiscoveredResources|`acs:config:${region}:${AccountId}:*`|
|config:DescribeDiscoveredResource|`acs:config:${region}:${AccountId}:*`|
|config:GetResourceConfigHistory|`acs:config:${region}:${AccountId}:*`|
|config:DescribeConfigRule|`acs:config:${region}:${AccountId}:*`|
|config:ListConfigRules|`acs:config:${region}:${AccountId}:*`|
|config:PutConfigRule|`acs:config:${region}:${AccountId}:*`|
|config:DeleteConfigRules|`acs:config:${region}:${AccountId}:*`|
|config:StartConfigRuleEvaluation|`acs:config:${region}:${AccountId}:*`|
|config:PutEvaluations|`acs:config:${region}:${AccountId}:*`|
|config:DescribeEvaluationResults|`acs:config:${region}:${AccountId}:*`|
|config:DescribeCompliance|`acs:config:${region}:${AccountId}:*`|
|config:DescribeComplianceSummary|`acs:config:${region}:${AccountId}:*`|

