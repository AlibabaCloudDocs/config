# Resource snapshot delivery events

When a resource snapshot is delivered to a specified Object Storage Service \(OSS\) bucket, Cloud Config for Enterprise sends a notification to you by using Message Service \(MNS\). This topic describes the sample code in successful and failed delivery of resource snapshot delivery events. This topic also describes the related parameters.

## Successful delivery of resource snapshot delivery events

The following table describes the parameters in successful delivery of resource snapshot delivery events.

|Parameter|Description|
|---------|-----------|
|requestId|The request ID of the resource snapshot delivery event.|
|eventName|The name of the resource snapshot delivery event.|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a resource change event.
-   ResourceCompliance: indicates a resource non-compliance event.
-   SnapshotDelivery: indicates a resource snapshot delivery event. |
|notificationCreationTime|The timestamp when the resource snapshot delivery event is created. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|

In this example, the resource snapshot delivery event is named SnapshotDeliverySuccess, and the delivery to MNS is successful. The following sample code is used:

```
{
    "requestId":"90e5deb6-3acf-48ce-9d28-56d93fe1****",
    "eventName":"SnapshotDeliverySuccess",
    "eventType":"SnapshotDelivery",
    "notificationCreationTime":1605863441996
}
```

## Failed delivery of resource snapshot delivery events

The following table describes the parameters in failed delivery of resource snapshot delivery events.

|Parameter|Description|
|---------|-----------|
|requestId|The request ID of the resource snapshot delivery event.|
|eventName|The name of the resource snapshot delivery event.|
|eventType|The type of the event. Valid values:-   ResourceChange: indicates a resource change event.
-   ResourceCompliance: indicates a resource non-compliance event.
-   SnapshotDelivery: indicates a resource snapshot delivery event. |
|errorCause|The reason why the resource snapshot delivery event fails to be delivered.|
|notificationCreationTime|The timestamp when the resource snapshot delivery event is created. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|

In this example, the resource snapshot delivery event is named SnapshotDeliveryFailed, and the delivery to MNS is failed. The value of the errorCause parameter is NoSuchBucket, which indicates that the specified destination bucket does not exist. The following sample code is used:

```
{
    "errorCause": "NoSuchBucket",
    "requestId": "9ad74955-4195-4f0a-938c-afd5c56477ea",
    "eventName": "SnapshotDeliveryFailed",
    "eventType": "SnapshotDelivery",
    "notificationCreationTime": 1606189671571
}
```

