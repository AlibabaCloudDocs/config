# Resource snapshot delivery events

When a resource snapshot is delivered to a specified Object Storage Service \(OSS\) bucket, Cloud Config sends a resource snapshot delivery event to a specified topic of Message Service \(MNS\). Then, MNS sends a notification to you based on the push method of the topic. This topic describes the parameters and sample code in successful and failed delivery of resource snapshot delivery events to MNS.

## Successful delivery of resource snapshot delivery events to MNS

The following table describes the parameters.

|Parameter|Description|
|---------|-----------|
|requestId|The request ID of the resource snapshot delivery event.|
|eventName|The name of the resource snapshot delivery event.|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a resource change event.
-   ResourceCompliance: indicates a resource non-compliance event.
-   SnapshotDelivery: indicates a resource snapshot delivery event. |
|notificationCreationTime|The timestamp when the resource delivery event is created.|

The following sample code is used:

```
{
    "requestId":"c33f24e9-c715-4c43-b635-e6d1c48b913e",
    "eventName":"SnapshotDeliverySuccess",
    "eventType":"SnapshotDelivery",
    "notificationCreationTime":1605863441996
}
```

## Failed delivery of resource snapshot delivery events to MNS

The following table describes the parameters.

|Parameter|Description|
|---------|-----------|
|requestId|The request ID of the resource snapshot delivery event.|
|eventName|The name of the resource snapshot delivery event.|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a resource change event.
-   ResourceCompliance: indicates a resource non-compliance event.
-   SnapshotDelivery: indicates a resource snapshot delivery event. |
|errorCause|The reason why the resource snapshot delivery event fails to be delivered.|
|notificationCreationTime|The timestamp when the resource delivery event is created.|

The value of the errorCause parameter is NoSuchBucket, which indicates that the specified destination bucket does not exist. The following sample code is used:

```
{
    "errorCause": "NoSuchBucket",
    "requestId": "9ad74955-4195-4f0a-938c-afd5c56477ea",
    "eventName": "SnapshotDeliveryFailed",
    "eventType": "SnapshotDelivery",
    "notificationCreationTime": 1606189671571
}
```

