# Send notifications of resource events to an MNS topic

You can use a master account to send notifications of resource events within the master account and its member accounts in your resource directory to a Message Service \(MNS\) topic. The MNS topic must belong to the master account or a member account. Only master accounts are authorized to send notifications of resource events. No member accounts have the relevant permissions.

-   A master account is used to log on to the Cloud Config console.
-   MNS is activated. For more information, see [Activate Message Service]().

For more information about MNS, see [What is MNS?]()

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Send Notifications to MNS**.

3.  On the **Send Notifications to MNS** page, turn on the **MNS Settings** switch.

4.  Specify an MNS topic to receive event notifications.

    You can create an MNS topic within the current master account, or select an existing MNS topic that belongs to the master account or a member account. The specified MNS topic receives the notifications of resource events that occur within the master account and its member accounts.

    -   To send notifications of resource events to a topic that belongs to the master account, select **Create a topic** or **Select an existing topic of your account**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**MNS Region**|The region where the topic resides.|
        |**Topic Name**|The name of the MNS topic. The topic name must be unique within an Alibaba Cloud account in a region.        -   If you select **Create a topic**, you must specify a topic name.
        -   If you select **Select an existing topic of your account**, you must select an existing topic from the Topic Name drop-down list. |
        |**Maximum Message Size \(Byte\)**|The maximum length of the message body that can be sent to the topic. Unit: bytes. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
        |**Enable Logging**|Specifies whether to enable log management for the topic.|
        |**Minimum Risk Level of the Events to Subscribe**|If you have configured rules, you can receive notifications of resource non-compliance events. To filter the resource non-compliance events to be received, you can set **Minimum Risk Level of the Events to Subscribe**. Valid values:         -   **All Risk Levels**
        -   **High Risk**
        -   **Medium Risk**
        -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications for the resource non-compliance events of **Medium Risk** and **High Risk** levels. The resource non-compliance events of the **Low Risk** level are ignored. |
        |**Resources to Subscribe**|The types of resources whose events you want to subscribe to. Valid values:        -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
        -   **Custom Resource Types**: Subscribe to the events of the selected types of resources. |

    -   To send notifications of resource events to a topic that belongs to a member account, select **Select an existing topic of another account \(enterprise account only\)**, and then set the required parameters. Before you set the parameters, make sure that the member account has available topics. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the topic that belongs to the destination account**|The Alibaba Cloud Resource Name \(ARN\) of the specified topic in the member account, for example, `acs:mns:ap-southeast-1:178589740730****:/topics/topic1`.Before you set this parameter, make sure that you have obtained the ID of the member account, the region where the topic resides, and the name of the topic. Then, set the parameter based on the ARN format.

The ARN must be in the format of `acs:mns:{regionId}:{Aliuid}:/topics/{topicName}`, where:

        -   `{regionId}`: the ID of the region where the topic resides, for example, ap-southeast-1.
        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `{topicName}`: the name of the topic, for example, topic1. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, for example, `acs:ram::178589740730****:role/aliyunserviceroleforconfig`.Before you set this parameter, make sure that you have obtained the ID of the member account. Then, set the parameter based on the ARN format.

The ARN must be in the format of `acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`, where:

        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service-linked role that authorizes Cloud Config to send the notifications of resource events to the specified MNS topic. |

5.  Click **OK**.


After the notifications of resource events are sent to the specified topic, you can log on to the MNS console to specify the push method and content of the topic. For more information, see [Publish a message]().

