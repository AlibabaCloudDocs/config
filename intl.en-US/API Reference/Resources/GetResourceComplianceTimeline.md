# GetResourceComplianceTimeline

Queries the compliance timeline of a resource.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetResourceComplianceTimeline&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetResourceComplianceTimeline|The operation that you want to perform. Set the value to GetResourceComplianceTimeline. |
|Region|String|Yes|cn-hangzhou|The ID of the region. |
|ResourceId|String|Yes|i-uf6072y75i2cevjq\*\*\*\*|The ID of the resource. |
|ResourceType|String|Yes|ACS::ECS::Instance|The type of the resource. |
|StartTime|Long|No|1593599340010|The timestamp that specifies the beginning of the time range to query. By default, Cloud Config retrieves the compliance evaluations in the last 30 days for the specified resource. |
|EndTime|Long|No|1593599342230|The timestamp that specifies the end of the time range to query. By default, the value is the time when the GetResourceComplianceTimeline operation is called. |
|Limit|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. Default value: 10. |
|MultiAccount|Boolean|No|true|Specifies whether to query the compliance timeline of the specified resource under the specified member account in the resource directory of the current master account. Valid values:

-   true: Query the compliance timeline of the specified resource under the specified member account in the resource directory of the current master account.
-   false: Query the compliance timeline of the specified resource under the current master account. This is the default value.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|MemberId|String|No|123456789|The ID of the member account whose resource compliance timeline is to be queried. This parameter must be set to a specific value if you set MultiAccount to true. Cloud Config retrieves the compliance timeline of the specified resource under the specified member account.

**Note:** If you are using Cloud Config for individuals, ignore this parameter. |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that is used to start the next query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|DE9FFFE5-FCAD-4B24-9546-BF49273C562B|The ID of the request. |
|ResourceComplianceTimeline|Struct| |The information about the compliance timeline. |
|ComplianceList|Array of ComplianceList| |The compliance evaluations in the compliance timeline. |
|AccountId|String|120390217529\*\*\*\*|The ID of the Alibaba Cloud account that owns the resource. |
|AvailabilityZone|String|cn-hangzhou-f|The ID of the zone. |
|CaptureTime|Long|1203902175292305|The timestamp when the compliance evaluation occurred. |
|Configuration|String|\{\\"managetest-required-tags\\":\[\{\},\{\\"configRuleId\\":\\"cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleName\\":\\"managetest-required-tags\\",\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"riskLevel\\":1,\\"annotation\\":\\"\{\\\\\\"desiredValue\\\\\\":\\\\\\"key1\\\\\\",\\\\\\"reason\\\\\\":\\\\\\"No tag with name key1\\\\\\"\}\\",\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|The information about the rules triggered for the resource and the compliance evaluation results. |
|ConfigurationDiff|String|\{\\"Compliance\\":\{\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"count\\":2\},\\"ConfigRuleList\\":\[\{\\"configRuleId\\":\\"cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleName\\":\\"required-tags\\",\\"complianceType\\":\\"COMPLIANT\\",\\"riskLevel\\":1,\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|The information about the changes to the compliance evaluation results, including the information about the triggered rules. |
|Region|String|cn-hangzhou|The ID of the region. |
|ResourceCreateTime|Long|1203902175293610|The timestamp when the resource was created. |
|ResourceId|String|i-uf6072y75i2cevjq\*\*\*\*|The ID of the resource. |
|ResourceName|String|test-resource|The name of the resource. |
|ResourceStatus|String|Running|The status of the resource. The parameter value varies with the resource type and may be left empty. Examples:

-   If ResourceType is set to ACS::ECS::Instance, the resource is an Elastic Compute Service \(ECS\) instance which has a specific state. In this case, valid values of this parameter include Running and Stopped.
-   If ResourceType is set to ACS::OSS::Bucket, the resource is an Object Storage Service \(OSS\) bucket which does not have a specific state. In this case, this parameter is left empty. |
|ResourceType|String|ACS::ECS::Instance|The type of the resource. |
|Tags|String|\{\\"project\\":\[\\"efg\\"\]\}|The tags of the resource. |
|Limit|Integer|10|The number of entries returned per page. Valid values: 1 to 100. |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that is returned for the next query. |
|TotalCount|Long|100|The total number of the compliance evaluations for the specified resource. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=GetResourceComplianceTimeline
&Region=cn-hangzhou
&ResourceId=i-uf6072y75i2cevjq****
&ResourceType=ACS::ECS::Instance
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ResourceComplianceTimelineResponse>
      <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
      <ComplianceList>
            <AccountId>120390217529****</AccountId>
            <CaptureTime>1203902175292305</CaptureTime>
            <ConfigurationDiff>{\"Compliance\":{\"complianceType\":\"NON_COMPLIANT\",\"count\":2},\"ConfigRuleList\":[{\"configRuleId\":\"cr-7b6e5180a8d100cc****\",\"configRuleArn\":\"acs:config::120390217529****:config-rule/cr-7b6e5180a8d100cc****\",\"configRuleName\":\"required-tags\",\"complianceType\":\"COMPLIANT\",\"riskLevel\":1,\"invokingEventMessageType\":\"ConfigurationItemChangeNotification\"}]}</ConfigurationDiff>
            <Configuration>{\"managetest-required-tags\":[{},{\"configRuleId\":\"cr-656d5180a8d1009c****\",\"configRuleArn\":\"acs:config::120390217529****:config-rule/cr-656d5180a8d1009c****\",\"configRuleName\":\"managetest-required-tags\",\"complianceType\":\"NON_COMPLIANT\",\"riskLevel\":1,\"annotation\":\"{\\\"desiredValue\\\":\\\"key1\\\",\\\"reason\\\":\\\"No tag with name key1\\\"}\",\"invokingEventMessageType\":\"ConfigurationItemChangeNotification\"}]}</Configuration>
            <ResourceId>i-uf6072y75i2cevjq****</ResourceId>
            <ResourceName>test-resource</ResourceName>
            <AvailabilityZone>cn-hangzhou-f</AvailabilityZone>
            <Region>cn-hangzhou</Region>
            <ResourceStatus>Running</ResourceStatus>
            <ResourceType>ACS::ECS::Instance</ResourceType>
            <ResourceCreateTime>1203902175293610</ResourceCreateTime>
            <Tags>{\"project\":[\"efg\"]}</Tags>
      </ComplianceList>
      <Limit>10</Limit>
      <RequestId>DE9FFFE5-FCAD-4B24-9546-BF49273C562B</RequestId>
</ResourceComplianceTimelineResponse>
```

`JSON` format

```
{
    "ResourceComplianceTimeline": {
        "NextToken": "caeba0bbb2be03f84eb48b699f0a****",
        "ComplianceList": [
            {
                "AccountId": "120390217529****",
                "CaptureTime": "1203902175292305",
                "ConfigurationDiff": "{\\\"Compliance\\\":{\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"count\\\":2},\\\"ConfigRuleList\\\":[{\\\"configRuleId\\\":\\\"cr-7b6e5180a8d100cc****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-7b6e5180a8d100cc****\\\",\\\"configRuleName\\\":\\\"required-tags\\\",\\\"complianceType\\\":\\\"COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
                "Configuration": "{\\\"managetest-required-tags\\\":[{},{\\\"configRuleId\\\":\\\"cr-656d5180a8d1009c****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-656d5180a8d1009c****\\\",\\\"configRuleName\\\":\\\"managetest-required-tags\\\",\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"annotation\\\":\\\"{\\\\\\\"desiredValue\\\\\\\":\\\\\\\"key1\\\\\\\",\\\\\\\"reason\\\\\\\":\\\\\\\"No tag with name key1\\\\\\\"}\\\",\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
                "ResourceId": "i-uf6072y75i2cevjq****",
                "ResourceName": "test-resource",
                "AvailabilityZone": "cn-hangzhou-f",
                "Region": "cn-hangzhou",
                "ResourceStatus": "Running",
                "ResourceType": "ACS::ECS::Instance",
                "ResourceCreateTime": "1203902175293610",
                "Tags": "{\\\"project\\\":[\\\"efg\\\"]}"
            }
        ],
        "Limit": 10
    },
    "RequestId": "DE9FFFE5-FCAD-4B24-9546-BF49273C562B"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

