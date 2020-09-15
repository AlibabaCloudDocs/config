# DescribeDeliveryChannels

Queries the details of delivery methods.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=DescribeDeliveryChannels&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDeliveryChannels|The operation that you want to perform. Set the value to DescribeDeliveryChannels. |
|DeliveryChannelIds|String|No|cdc-d9106457e0d900b1\*\*\*\*,cdc-d9106457e0d900b1\*\*\*\*|The IDs of the delivery methods. Separate multiple IDs with commas \(,\). For more information, see [PutDeliveryChannel](~~174253~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DeliveryChannels|Array of DeliveryChannel| |The information about the delivery method. |
|DeliveryChannelAssumeRoleArn|String|acs:ram::120886317861\*\*\*\*:role/aliyunserviceroleforconfig|The Alibaba Cloud Resource Name \(ARN\) of the role assumed by delivery method. |
|DeliveryChannelCondition|String|\[\{"filterType":"ResourceType","values":\["ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage","ACS::CDN::Domain","ACS::CEN::CenBandwidthPackage","ACS::CEN::CenInstance","ACS::CEN::Flowlog","ACS::DdosCoo::Instance"\],"multiple":true\}\]|The rule attached to the delivery method. This parameter is applicable only to delivery methods of the Message Service \(MNS\) type.

This parameter indicates the lowest risk level for the events to subscribe to and the resource types for which you subscribe to events.

-   The setting of the lowest risk level for the events to subscribe to is in the following format:`{"filterType":"RuleRiskLevel","value":"1","multiple":false}.`

The value field indicates the lowest risk level and can be set to 1, 2, or 3, which indicates the high risk level, the medium risk level, and the low risk level, respectively.

-   The setting of the resource types for which you subscribe to events is in the following format:`{"filterType":"ResourceType","values":["ACS::ACK::Cluster","ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage"],"multiple":true}.`

The values field indicates the resource types. Its value is a JSON array.

Example: `[{"filterType":"ResourceType","values":["ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage","ACS::CDN::Domain","ACS::CEN::CenBandwidthPackage","ACS::CEN::CenInstance","ACS::CEN::Flowlog","ACS::DdosCoo::Instance"],"multiple":true}]` |
|DeliveryChannelId|String|cdc-d9106457e0d900b1\*\*\*\*|The ID of the delivery method. |
|DeliveryChannelName|String|myDeliveryChannel|The name of the delivery method. |
|DeliveryChannelTargetArn|String|acs:oss:cn-shanghai:120886317861\*\*\*\*:text123457|The ARN of the delivery destination.

-   If DeliveryChannelType is set to OSS, the value of this parameter is the ARN of the destination Object Storage Service \(OSS\) bucket.
-   If DeliveryChannelType is set to MNS, the value of this parameter is the ARN of the destination MNS topic.
-   If DeliveryChannelType is set to SLS, the value is the ARN of the destination Log Service Logstore. |
|DeliveryChannelType|String|OSS|The type of the delivery method. Valid values:

-   OSS
-   MNS
-   SLS |
|Description|String|My OSS delivery.|The description of the delivery method. |
|Status|Integer|1|The status of the delivery method. Valid values:

-   0: The delivery method is disabled.
-   1: The delivery destination is enabled. |
|RequestId|String|8300C16A-5DCA-4DB4-88C1-DE0493EC409C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeDeliveryChannels
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDeliveryChannelsResponse>
      <DeliveryChannels>
            <Status>1</Status>
            <Description></Description>
            <DeliveryChannelId>cdc-d9106457e0d900b1****</DeliveryChannelId>
            <DeliveryChannelName></DeliveryChannelName>
            <DeliveryChannelTargetArn>acs:oss:cn-shanghai:120886317861****:text123457</DeliveryChannelTargetArn>
            <DeliveryChannelAssumeRoleArn>acs:ram::120886317861****:role/aliyunserviceroleforconfig</DeliveryChannelAssumeRoleArn>
            <DeliveryChannelType>OSS</DeliveryChannelType>
            <DeliveryChannelCondition></DeliveryChannelCondition>
      </DeliveryChannels>
      <DeliveryChannels>
            <Status>1</Status>
            <Description></Description>
            <DeliveryChannelId>cdc-d9106457e0d900b1****</DeliveryChannelId>
            <DeliveryChannelName></DeliveryChannelName>
            <DeliveryChannelTargetArn>acs:mns:cn-hangzhou:120886317861****:/topics/testmns001</DeliveryChannelTargetArn>
            <DeliveryChannelAssumeRoleArn>acs:ram::120886317861****:role/aliyunserviceroleforconfig</DeliveryChannelAssumeRoleArn>
            <DeliveryChannelType>MNS</DeliveryChannelType>
            <DeliveryChannelCondition>[{"filterType":"RuleRiskLevel","value":"1","multiple":false}]</DeliveryChannelCondition>
      </DeliveryChannels>
      <RequestId>8300C16A-5DCA-4DB4-88C1-DE0493EC409C</RequestId>
</DescribeDeliveryChannelsResponse>
```

`JSON` format

```
{
  "DeliveryChannels": [
    {
      "Status": 1,
      "Description": "",
      "DeliveryChannelId": "cdc-d9106457e0d900b1****",
      "DeliveryChannelName": "",
      "DeliveryChannelTargetArn": "acs:oss:cn-shanghai:120886317861****:text123457",
      "DeliveryChannelAssumeRoleArn": "acs:ram::120886317861****:role/aliyunserviceroleforconfig",
      "DeliveryChannelType": "OSS",
      "DeliveryChannelCondition": ""
    },
    {
      "Status": 1,
      "Description": "",
      "DeliveryChannelId": "cdc-d9106457e0d900b1****",
      "DeliveryChannelName": "",
      "DeliveryChannelTargetArn": "acs:mns:cn-hangzhou:120886317861****:/topics/testmns001",
      "DeliveryChannelAssumeRoleArn": "acs:ram::120886317861****:role/aliyunserviceroleforconfig",
      "DeliveryChannelType": "MNS",
      "DeliveryChannelCondition": "[{\"filterType\":\"RuleRiskLevel\",\"value\":\"1\",\"multiple\":false}]"
    }
  ],
  "RequestId": "8300C16A-5DCA-4DB4-88C1-DE0493EC409C"
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|DeliveryChannelNotExists|The delivery channel does not exist.|The error message returned because the specified delivery method does not exist.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

