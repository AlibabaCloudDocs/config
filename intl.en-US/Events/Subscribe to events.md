# Subscribe to events

You can subscribe to configuration change events, non-compliance events, and snapshot delivery events in Cloud Config. After you subscribe to an event, Cloud Config sends a notification to the specified Message Service \(MNS\) topic when the event occurs.

MNS is activated. For more information, see [Activate Message Service]().

For more information about MNS, see [What is MNS?]()

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Settings** \> **Send Notifications to MNS**.

3.  On the **Send Notifications to MNS** page, turn on **MNS Settings**.

4.  Specify an MNS topic to receive event notifications.

    The following table describes the parameters for specifying an MNS topic.

    |Parameter|Description|
    |---------|-----------|
    |**MNS Region**|The region where the MNS topic resides.|
    |**Topic Name**|The name of the MNS topic to receive event notifications. The name must be unique to an Alibaba Cloud account in a region.    -   If you select **Create a topic**, you must specify a topic name.

For more information about how to create a topic in MNS, see [Create a topic]().

    -   If you select **Select an existing topic of your account**, you must select an existing topic from the drop-down list. |
    |**Maximum Message Size \(Byte\)**|The maximum length of the message body to be sent to the MNS topic, in bytes. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192 to avoid message delivery failures due to the length limit. |
    |**Enable Logging**|Specifies whether to enable log management for the topic.|
    |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to subscribe to. Valid values:     -   **All Risk Levels**
    -   **High Risk**
    -   **Medium Risk**
    -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications about the non-compliance events at the **Medium Risk** and **High Risk** levels. The non-compliance events at the **Low Risk** level are ignored. |
    |**Resources to Subscribe**|The types of the resources whose events you want to subscribe to. Valid values:    -   **All Supported Resource Types**: You can subscribe to the events of all supported resource types. When a new service is connected to Cloud Config, the resource type of the service is automatically added to the monitoring scope.
    -   **Custom Resource Types**: You can subscribe to the events of the selected resource types. |

5.  Click **OK**.


