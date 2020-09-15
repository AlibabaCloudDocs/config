# PutDeliveryChannel

Creates or modifies a delivery method.

****

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=PutDeliveryChannel&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|PutDeliveryChannel|The operation that you want to perform. Set the value to PutDeliveryChannel. |
|DeliveryChannelAssumeRoleArn|String|Yes|acs:ram::100931896542\*\*\*\*:role/aliyunserviceroleforconfig|The Alibaba Cloud Resource Name \(ARN\) of the role to be assumed by the delivery method. This parameter is required when you create a delivery method.

**Note:** If the delivery method assumes the service linked role for Cloud Config, you can specify the ARN in the format of the provided example and replace the account ID with the ID of your Alibaba Cloud account. |
|DeliveryChannelTargetArn|String|Yes|acs:oss:cn-hangzhou:100931896542\*\*\*\*:20171130--1|The ARN of the delivery destination. This parameter is required when you create a delivery method. The value must be in one of the following formats:

-   `acs:oss:{RegionId}:{Aliuid}:{bucketName}` if your delivery destination is an Object Storage Service \(OSS\) bucket.
-   `acs:mns:{RegionId}:{Aliuid}:/topics/{topicName}` if your delivery destination is a Message Service \(MNS\) topic.
-   `acs:log:{RegionId}:{Aliuid}:project/{projectName}/logstore/{logstoreName}` if your delivery destination is a Log Service Logstore. |
|DeliveryChannelType|String|Yes|OSS|The type of the delivery method. This parameter is required when you create a delivery method. Valid values:

-   OSS
-   MNS
-   SLS |
|ClientToken|String|No|1594295238-f9361358-5843-4294-8d30-b5183fac\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate a token, but you must make sure that it is unique among different requests. The token cannot exceed 64 characters in length and can only contain ASCII characters. |
|DeliveryChannelId|String|No|cdc-193f6457e0d90080\*\*\*\*|The ID of the delivery method. This parameter is required when you modify a delivery method. |
|DeliveryChannelName|String|No|testoss|The name of the delivery method. |
|DeliveryChannelCondition|String|No|\[\{"filterType":"ResourceType","values":\["ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage","ACS::CDN::Domain","ACS::CEN::CenBandwidthPackage","ACS::CEN::CenInstance","ACS::CEN::Flowlog","ACS::DdosCoo::Instance"\],"multiple":true\}\]|The rule attached to the delivery method. This parameter is applicable only to delivery methods of the MNS type.

This parameter allows you to specify the lowest risk level for the events to subscribe to and the resource types for which you want to subscribe to events.

-   To specify the lowest risk level for the events to subscribe to, use the following format:`{"filterType":"RuleRiskLevel","value":"1","multiple":false}.`

The value field indicates the lowest risk level and can be set to 1, 2, or 3, which indicates the high risk level, the medium risk level, and the low risk level, respectively.

-   To specify the resource types for which you want to subscribe to events, use the following format:`{"filterType":"ResourceType","values":["ACS::ACK::Cluster","ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage"],"multiple":true}.`

The values field indicates the resource types. Its value is a JSON array.

Example: `[{"filterType":"ResourceType","values":["ACS::ActionTrail::Trail","ACS::CBWP::CommonBandwidthPackage","ACS::CDN::Domain","ACS::CEN::CenBandwidthPackage","ACS::CEN::CenInstance","ACS::CEN::Flowlog","ACS::DdosCoo::Instance"],"multiple":true}]` |
|Description|String|No|My OSS delivery.|The description of the delivery method. |
|Status|Integer|No|1|The status of the delivery method. Valid values:

-   0: The delivery method is disabled.
-   1: The delivery destination is enabled. This is the default value. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DeliveryChannelId|String|cdc-ee0f626622af0069\*\*\*\*|The ID of the delivery method that you created or the updated ID of the delivery method that you modified. |
|RequestId|String|0D6B9E0A-AD53-4732-922B-0F584ECA5FAB|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=PutDeliveryChannel
&DeliveryChannelAssumeRoleArn=acs:ram::100931896542****:role/aliyunserviceroleforconfig
&DeliveryChannelTargetArn=acs:oss:cn-hangzhou:100931896542****:20171130--1
&DeliveryChannelType=OSS
&<Common request parameters>
```

Sample success responses

`XML` format

```
<PutDeliveryChannelResponse>
      <RequestId>0D6B9E0A-AD53-4732-922B-0F584ECA5FAB</RequestId>
      <DeliveryChannelId>cdc-ee0f626622af0069****</DeliveryChannelId>
</PutDeliveryChannelResponse>
```

`JSON` format

```
{
    "RequestId": "0D6B9E0A-AD53-4732-922B-0F584ECA5FAB",
    "DeliveryChannelId": "cdc-ee0f626622af0069****"
}
```

## Errors codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|400|DeliveryChannelNotExists|The delivery channel does not exist.|The error message returned because the specified delivery method does not exist.|
|400|Invalid.DeliveryChannelName.Empty|You must specify DeliveryChannelName.|The error message returned because the DeliveryChannelName parameter is not set.|
|400|Invalid.DeliveryChannelType.Empty|You must specify DeliveryChannelType.|The error message returned because the DeliveryChannelType parameter is not set.|
|400|Invalid.DeliveryChannelAssumeRoleArn.Empty|You must specify DeliveryChannelAssumeRoleArn.|The error message returned because the DeliveryChannelAssumeRoleArn parameter is not set.|
|400|Invalid.DeliveryChannelAssumeRoleArn.Format|The specified format of DeliveryChannelAssumeRoleArn is invalid.|The error message returned because the value of DeliveryChannelAssumeRoleArn is specified in an invalid format.|
|400|Invalid.DeliveryChannelTargetArn.Empty|You must specify DeliveryChannelTargetArn.|The error message returned because the DeliveryChannelTargetArn parameter is not set.|
|400|Invalid.DeliveryChannelTargetArn.Format|The specified format of DeliveryChannelTargetArn is invalid.|The error message returned because the value of DeliveryChannelTargetArn is specified in an invalid format.|
|400|Invalid.DeliveryChannelCondition.Format|The specified format of DeliveryChannelCondition is invalid.|The error message returned because the value of DeliveryChannelCondition is specified in an invalid format.|
|400|MemberNotBelongToMaster|The specified member does not belong to your organization.|The error message returned because the specified member account does not belong to your resource directory.|
|400|DeliveryChannelAccountNotSupport|Cross-account delivery that is not in the RD is not supported.|The error message returned because Cloud Config does not support event delivery across accounts that are in different resource directories.|
|400|DeliveryChannelMnsUnreachable|The MNS topic is unreachable.|The error message returned because the delivery request to the specified MNS topic failed.|
|400|DeliveryChannelOssUnreachable|The OSS bucket is unreachable.|The error message returned because the delivery request to the specified OSS bucket failed.|
|400|DeliveryChannelSlsUnreachable|SLS logstore is unreachable.|The error message returned because the delivery request to the specified Log Service Logstore failed.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

