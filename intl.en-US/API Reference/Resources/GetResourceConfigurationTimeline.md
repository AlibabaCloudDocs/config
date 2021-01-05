# GetResourceConfigurationTimeline

Queries the configuration timeline of a resource.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=GetResourceConfigurationTimeline&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetResourceConfigurationTimeline|The operation that you want to perform. Set the value to GetResourceConfigurationTimeline. |
|Region|String|Yes|cn-hangzhou|The ID of the region. |
|ResourceId|String|Yes|i-bp19xem7lt97h973\*\*\*\*|The ID of the resource. |
|ResourceType|String|Yes|ACS::ECS::Instance|The type of the resource. |
|StartTime|Long|No|1605489195000|The timestamp that specifies the beginning of the time range to query. By default, Cloud Config retrieves the configuration changes in the last 30 days for the specified resource. |
|EndTime|Long|No|1605489235000|The timestamp that specifies the end of the time range to query. By default, the value is the time when the GetResourceConfigurationTimeline operation is called. |
|Limit|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 100. Default value: 10. |
|MultiAccount|Boolean|No|true|Specifies whether to query the configuration timeline of the specified resource that belongs to the specified member account in the resource directory of the current master account. Valid values:

 -   true: Queries the configuration timeline of the specified resource within the specified member account in the resource directory of the current master account.
-   false \(default value\): Queries the configuration timeline of the specified resource that belongs to the current master account.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |
|MemberId|Long|No|123456789|The ID of the member account whose resource configuration timeline you want to query. This parameter must be specified if you set MultiAccount to true. Cloud Config retrieves the configuration timeline of the specified resource that belongs to the specified member account.

 **Note:** If you are using Cloud Config for individuals, you do not need to set this parameter. |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that is used to start the next query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB|The ID of the request. |
|ResourceConfigurationTimeline|Struct| |The information of the configuration timeline. |
|ConfigurationList|Array of ConfigurationList| |The configuration changes of the configuration timeline. |
|AccountId|Long|123456789|The ID of the Alibaba Cloud account that owns the resource. |
|AvailabilityZone|String|cn-hangzhou-h|The ID of the zone. |
|CaptureTime|String|1605316711000|The timestamp when the configuration change occurred. |
|ConfigurationDiff|String|\{\\"ExpiredTime\\":\[\\"2020-10-26T16:00Z\\",\\"2020-11-26T16:00Z\\"\]\}|The information of the changes to the configuration of the resource. |
|Region|String|cn-hangzhou|The ID of the region. |
|ResourceCreateTime|String|1605237751000|The time when the resource was created. |
|ResourceEventType|String|DISCOVERED|The type of the resource change event. Valid values:

 -   DISCOVERED: A resource was created.
-   MODIFY: A resource was modified.
-   REMOVE: A resource was deleted. |
|ResourceId|String|i-bp19xem7lt97h973\*\*\*\*|The ID of the resource. |
|ResourceName|String|ECS-test|The name of the resource. |
|ResourceType|String|ACS::ECS::Instance|The type of the resource. |
|Tags|String|"\{\\"\\"hc\\"\\":\[\\"\\"value2\\"\\"\]\}"|The tags of the resource. |
|Limit|Integer|10|The number of entries returned per page. Valid values: 1 to 100. |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|The token that was returned for the next query. |
|TotalCount|Long|100|The total number of configuration changes for the specified resource. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=GetResourceConfigurationTimeline
&Region=cn-hangzhou
&ResourceId=i-bp19xem7lt97h973****
&ResourceType=ACS::ECS::Instance
&<common request parameters>
```

Sample responses

`XML` format

```
<GetResourceConfigurationTimelineResponse>
		  <RequestId>ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB</RequestId>
		  <ResourceConfigurationTimeline>
			    <ConfigurationList>
				      <AccountId>100931896542****</AccountId>
				      <ResourceCreateTime>1605237751000</ResourceCreateTime>
				      <resourceEventType>DISCOVERED</resourceEventType>
                      <CaptureTime>1605316711000</CaptureTime>
				      <ConfigurationDiff>{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}</ConfigurationDiff>
				      <ResourceId>i-bp19xem7lt97h973****</ResourceId>
				      <ResourceName>ECS-test</ResourceName>
				      <Region>cn-hangzhou</Region>
				      <AvailabilityZone>cn-hangzhou-h</AvailabilityZone>
				      <ResourceType>ACS::ECS::Instance</ResourceType>
				      <Tags>{\"\"hc\"\":[\"\"value2\"\"]}</Tags>
			    </ConfigurationList>
			    <Limit>10</Limit>
			    <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
		  </ResourceConfigurationTimeline>
</GetResourceConfigurationTimelineResponse>
```

`JSON` format

```
{
  "RequestId": "ED9CD1B3-286C-4E05-A765-5E1E0B9BC2AB",  
  "ResourceConfigurationTimeline": {
    "ConfigurationList": [
      {
        "AccountId": "100931896542****",
        "ResourceCreateTime": "1605237751000",
        "resourceEventType": "DISCOVERED",
        "CaptureTime":"1605316711000",
        "ConfigurationDiff": "{\"ExpiredTime\":[\"2020-10-26T16:00Z\",\"2020-11-26T16:00Z\"]}",
        "ResourceId": "i-bp19xem7lt97h973****",
        "ResourceName": "ECS-test",
        "Region": "cn-hangzhou",
        "AvailabilityZone": "cn-hangzhou-h",
        "ResourceType": "ACS::ECS::Instance",
        "Tags": "{\"\"hc\"\":[\"\"value2\"\"]}"
      }
    ],
    "Limit": 10,
    "NextToken": "caeba0bbb2be03f84eb48b699f0a****"
  }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

