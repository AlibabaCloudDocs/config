# Resource non-compliance events

If you have configured rules, Cloud Config evaluates your resources based on the rules at regular intervals or when resource configuration changes. If a resource is evaluated as **non-compliant**, Cloud Config will send a notification to you in a timely manner.

The following table describes the parameters for resource non-compliance events.

|Parameter|Description|
|---------|-----------|
|annotation|The description of the non-compliant configuration.|
|configuration|The current configuration of the resource.|
|desiredValue|The desired configuration of the resource.|
|operator|The operator that compares the current configuration with the desired configuration of the resource.|
|property|The JSON path of the current configuration.|
|accountId|The ID of the Alibaba Cloud account to which the resource belongs.|
|riskLevel|The risk level of the resource that is not compliant with the rule. Valid values:-   Info: low risk.
-   Warning: medium risk.
-   Critical: high risk. |
|evaluationResultIdentifier|The detailed information about the compliance evaluation result.|
|resourceId|The ID of the resource.|
|configRuleName|The name of the rule.|
|configRuleArn|The Alibaba Cloud Resource Name \(ARN\) of the rule.|
|configRuleId|The ID of the rule.|
|regionId|The ID of the region where the resource resides.|
|resourceType|The type of the resource.|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a configuration change event.
-   ResourceCompliance: indicates a non-compliance event.
-   SnapshotDelivery: indicates a snapshot delivery event. |
|complianceType|The compliance evaluation result of the resource. Valid values:-   COMPLIANT: The resource is evaluated as compliant.
-   NON\_COMPLIANT: The resource is evaluated as non-compliant. |

Example

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
      "regionId": "Singapore",
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

