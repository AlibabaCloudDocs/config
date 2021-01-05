# Resource non-compliance events

Cloud Config for Enterprise automatically evaluates the compliance of a resource. If a resource is evaluated to be **non-compliant**, Cloud Config for Enterprise sends a notification to you by using Message Service \(MNS\). This topic describes the sample code of resource non-compliance events. This topic also describes the related parameters.

The following table describes the parameters of resource non-compliance events.

|Parameter|Description|
|---------|-----------|
|annotation|The description of the non-compliant resource.|
|configuration|The actual configurations of the resource.|
|desiredValue|The expected configurations of the resource.|
|operator|The operator that compares the current configurations with the expected configurations of the resource.|
|property|The JSON path of the configurations in the resource property struct, for example, `$.AccessControlList.Grant`.|
|accountId|The ID of the Alibaba Cloud account that owns the resource.|
|riskLevel|The risk level of the resource that is not compliant with the rule. Valid values:-   Info: low risk.
-   Warning: medium risk.
-   Critical: high risk. |
|evaluationResultIdentifier|The details of the compliance evaluation result.|
|resourceId|The ID of the resource.|
|configRuleName|The name of the rule.|
|configRuleArn|The Alibaba Cloud Resource Name \(ARN\) of the rule.|
|configRuleId|The ID of the rule.|
|regionId|The ID of the region where the resource resides.|
|resourceOwnerId|The ID of the Alibaba Cloud account that owns the resource.|
|resourceType|The type of the resource. For more information about supported resource types, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a resource change event.
-   ResourceCompliance: indicates a resource non-compliance event.
-   SnapshotDelivery: indicates a resource snapshot delivery event. |
|complianceType|The compliance evaluation result of the resource. Valid values:-   COMPLIANT: The resource is evaluated to be compliant.
-   NON\_COMPLIANT: The resource is evaluated to be non-compliant. |

In this example, a rule named test-oss-bucket-public-read-prohibited is created by using a master account in Cloud Config for Enterprise. The rule is used to evaluate the read and write permissions of an Object Storage Service \(OSS\) bucket named config-snapshot that resides in the Singapore \(Singapore\) region. The actual configurations of the bucket named config-snapshot are public-read. The expected configurations are NotContains read. The evaluation result is NonCompliant. The following sample code is used:

```
{
  "annotation": "{\"configuration\":\"public-read\",\"desiredValue\":\"read\",\"operator\":\"NotContains\",\"property\":\"$.AccessControlList.Grant\"}",
  "accountId": 169827232854****,
  "riskLevel": "Critical",
  "resultRecordedTimestamp": 1595419396740,
  "eventName": "NonCompliant",
  "evaluationResultIdentifier": {
    "orderingTimestamp": 1595419392092,
    "evaluationResultQualifier": {
      "resourceId": "config-snapshot",
      "configRuleName": "test-oss-bucket-public-read-prohibited",
      "configRuleArn": "acs:config::169827232854****:config-rule/cr-610ad6e0007300a8****",
      "configRuleId": "cr-610ad6e0007300a8****",
      "regionId": "ap-southeast-1",
      "resourceName":"config-snapshot",
      "resourceOwnerId":169827232854****,
      "resourceType": "ACS::OSS::Bucket"
    }
  },
  "eventType": "ResourceCompliance",
  "invokingEventMessageType": "ConfigurationItemChangeNotification",
  "configRuleInvokedTimestamp": 1595419392092,
  "notificationCreationTime": 1595419396769,
  "complianceType": "NON_COMPLIANT"
}
```

