# Send notifications of resource events to an MNS topic

This topic describes how to send notifications of resource events to a Message Service \(MNS\) topic. You can subscribe to configuration change events, non-compliance events, and snapshot delivery events in Cloud Config. After you subscribe to the events of specific types of resources, Cloud Config sends a notification to the specified MNS topic when an event occurs.

MNS is activated. For more information, see [Activate Message Service]().

For more information about MNS, see [What is MNS?]()

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Send Notifications to MNS**.

3.  On the **Send Notifications to MNS** page, turn on **MNS Settings**.

4.  Specify an MNS topic to receive event notifications.

    The following table describes the parameters for specifying an MNS topic.

    |Parameter|Description|
    |---------|-----------|
    |**MNS Region**|The region where the MNS topic resides.|
    |**Topic Name**|The name of the MNS topic to receive event notifications. The name must be unique to an Alibaba Cloud account in a region.    -   If you select **Create a topic**, you must specify a topic name.

For more information about how to create a topic in MNS, see [Create a topic]().

    -   If you select **Select an existing topic of your account**, you must select an existing topic from the Topic Name drop-down list. |
    |**Maximum Message Size \(Byte\)**|The maximum length of the notification body to be sent to the MNS topic, in bytes. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
    |**Enable Logging**|Specifies whether to enable log management for the topic.|
    |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to subscribe to. Valid values:     -   **All Risk Levels**
    -   **High Risk**
    -   **Medium Risk**
    -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications about the non-compliance events at the **Medium Risk** and **High Risk** levels. The non-compliance events at the **Low Risk** level are ignored. |
    |**Resources to Subscribe**|The types of resources of which you want to subscribe to events. Valid values:    -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
    -   **Custom Resource Types**: Subscribe to the events of the selected types of resources. |

5.  Click **OK**.


