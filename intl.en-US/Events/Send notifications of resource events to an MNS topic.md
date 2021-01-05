# Send notifications of resource events to an MNS topic

You can send notifications of resource change events, resource non-compliance events, and resource snapshot delivery events to a specified Message Service \(MNS\) topic in Cloud Config. You can also specify the push method and content of the topic.

MNS is activated. For more information, see [Activate Message Service]().

For more information about MNS, see [What is MNS?]()

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Send Notifications to MNS**.

3.  On the **Send Notifications to MNS** page, turn on the **MNS Settings** switch.

4.  Set the required parameters to specify an MNS topic to receive event notifications.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**MNS Region**|The region where the topic resides.|
    |**Topic Name**|The name of the MNS topic. The topic name must be unique within an Alibaba Cloud account in a region.    -   If you select **Create a topic**, you must specify a topic name.
    -   If you select **Select an existing topic of your account**, you must select an existing topic from the Topic Name drop-down list. |
    |**Maximum Message Size \(Byte\)**|The maximum length of the message body that can be sent to the topic. Unit: bytes. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
    |**Enable Logging**|Specifies whether to enable log management for the topic.|
    |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to which you want to subscribe. Valid values:     -   **All Risk Levels**
    -   **High Risk**
    -   **Medium Risk**
    -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications for the resource non-compliance events of **Medium Risk** and **High Risk** levels. The resource non-compliance events of the **Low Risk** level are ignored. |
    |**Resources to Subscribe**|The types of resources whose events you want to subscribe to. Valid values:    -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
    -   **Custom Resource Types**: Subscribe to the events of the selected types of resources. |

5.  Click **OK**.


After the notifications of resource events are sent to the specified topic, you can log on to the MNS console to specify the push method and content of the topic. For more information, see [Publish a message]().

