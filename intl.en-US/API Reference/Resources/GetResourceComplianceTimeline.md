# GetResourceComplianceTimeline

Queries the compliance timeline of a resource.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetResourceComplianceTimeline&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetResourceComplianceTimeline|The operation that you want to perform. Set the value to **GetResourceComplianceTimeline**. |
|ResourceType|String|Yes|ACS::ECS::Instance|The type of the resource. |
|ResourceId|String|Yes|i-uf6072y75i2cevjq\*\*\*\*|The ID of the resource. |
|StartTime|Long|No|1593599340010|The timestamp that specifies the beginning of the time range to query. By default, Cloud Config retrieves the configuration changes in the last 30 days for the specified resource. |
|EndTime|Long|No|1593599342230|The timestamp that specifies the end of the time range to query. By default, the value is the time when the GetResourceConfigurationTimeline operation is called. |
|Limit|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. Default value: 10. |
|MultiAccount|Boolean|No|true|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|MemberId|String|No|123456789|This parameter is scheduled to be removed before 00:00:00, June 30, 2021. Account group-related APIs will be provided as an alternative before 00:00:00, May 30, 2021. If you are using this parameter, we recommend that you switch to account group-related APIs after 00:00:00, May 30, 2021. For more information, see [Account groups](~~211534~~). |
|Region|String|Yes|cn-hangzhou|The ID of the region. |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that is used to start the next query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|DE9FFFE5-FCAD-4B24-9546-BF49273C562B|The ID of the request. |
|ResourceComplianceTimeline|Object| |The information about the compliance timeline. |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that was returned for the next query. |
|Limit|Integer|10|The number of entries returned on each page. Valid values: 1 to 100. |
|ComplianceList|Array of ComplianceList| |The compliance evaluations in the compliance timeline. |
|Tags|String|\{\\"project\\":\[\\"efg\\"\]\}|The tags of the resource. |
|AccountId|String|120390217529\*\*\*\*|The ID of your Alibaba Cloud account. |
|AvailabilityZone|String|cn-hangzhou-f|The ID of the zone. |
|ResourceType|String|ACS::ECS::Instance|The type of the resource. |
|ResourceCreateTime|Long|1203902175293610|The timestamp when the resource was created. |
|Region|String|cn-hangzhou|The ID of the region. |
|Configuration|String|\{\\"managetest-required-tags\\":\[\{\},\{\\"configRuleId\\":\\"cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-656d5180a8d1009c\*\*\*\*\\",\\"configRuleName\\":\\"managetest-required-tags\\",\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"riskLevel\\":1,\\"annotation\\":\\"\{\\\\\\"desiredValue\\\\\\":\\\\\\"key1\\\\\\",\\\\\\"reason\\\\\\":\\\\\\"No tag with name key1\\\\\\"\}\\",\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|The information about the rules triggered for the resource and the compliance evaluation results. |
|CaptureTime|Long|1203902175292305|The timestamp when the compliance evaluation occurred. |
|ConfigurationDiff|String|\{\\"Compliance\\":\{\\"complianceType\\":\\"NON\_COMPLIANT\\",\\"count\\":2\},\\"ConfigRuleList\\":\[\{\\"configRuleId\\":\\"cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleArn\\":\\"acs:config::120390217529\*\*\*\*:config-rule/cr-7b6e5180a8d100cc\*\*\*\*\\",\\"configRuleName\\":\\"required-tags\\",\\"complianceType\\":\\"COMPLIANT\\",\\"riskLevel\\":1,\\"invokingEventMessageType\\":\\"ConfigurationItemChangeNotification\\"\}\]\}|The information about the changes to the compliance evaluation results, including the information about the triggered rules. |
|ResourceId|String|i-uf6072y75i2cevjq\*\*\*\*|The ID of the resource. |
|ResourceName|String|test-resource|The name of the resource. |
|ResourceStatus|String|Running|The status of the resource. The parameter value varies with the resource type and may be left empty. Examples:

 -   If ResourceType is set to ACS::ECS::Instance, the resource is an Elastic Compute Service \(ECS\) instance which has a specific state. In this case, valid values of this parameter include Running and Stopped.
-   If ResourceType is set to ACS::OSS::Bucket, the resource is an Object Storage Service \(OSS\) bucket which does not have a specific state. In this case, this parameter is left empty. |
|TotalCount|Long|100|The total number of the compliance evaluations for the specified resource. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=GetResourceComplianceTimeline
&Region=cn-hangzhou
&ResourceId=i-uf6072y75i2cevjq****
&ResourceType=ACS::ECS::Instance
&<Common request parameters>
```

Sample success responses

`XML` format

```
HTTP/1.1 200 OK
Content-Type:application/xml

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
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ResourceComplianceTimeline" : {
    "NextToken" : "caeba0bbb2be03f84eb48b699f0a****",
    "ComplianceList" : [ {
      "AccountId" : "120390217529****",
      "CaptureTime" : "1203902175292305",
      "ConfigurationDiff" : "{\\\"Compliance\\\":{\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"count\\\":2},\\\"ConfigRuleList\\\":[{\\\"configRuleId\\\":\\\"cr-7b6e5180a8d100cc****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-7b6e5180a8d100cc****\\\",\\\"configRuleName\\\":\\\"required-tags\\\",\\\"complianceType\\\":\\\"COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
      "Configuration" : "{\\\"managetest-required-tags\\\":[{},{\\\"configRuleId\\\":\\\"cr-656d5180a8d1009c****\\\",\\\"configRuleArn\\\":\\\"acs:config::120390217529****:config-rule/cr-656d5180a8d1009c****\\\",\\\"configRuleName\\\":\\\"managetest-required-tags\\\",\\\"complianceType\\\":\\\"NON_COMPLIANT\\\",\\\"riskLevel\\\":1,\\\"annotation\\\":\\\"{\\\\\\\"desiredValue\\\\\\\":\\\\\\\"key1\\\\\\\",\\\\\\\"reason\\\\\\\":\\\\\\\"No tag with name key1\\\\\\\"}\\\",\\\"invokingEventMessageType\\\":\\\"ConfigurationItemChangeNotification\\\"}]}",
      "ResourceId" : "i-uf6072y75i2cevjq****",
      "ResourceName" : "test-resource",
      "AvailabilityZone" : "cn-hangzhou-f",
      "Region" : "cn-hangzhou",
      "ResourceStatus" : "Running",
      "ResourceType" : "ACS::ECS::Instance",
      "ResourceCreateTime" : "1203902175293610",
      "Tags" : "{\\\"project\\\":[\\\"efg\\\"]}"
    } ],
    "Limit" : 10
  },
  "RequestId" : "DE9FFFE5-FCAD-4B24-9546-BF49273C562B"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

