# Send notifications of resource events to an MNS topic

This topic describes how to send notifications of resource events to a Message Service \(MNS\) topic in Cloud Config for Enterprise. You can use a master account to specify an MNS topic to receive notifications of events that occur under the master account and the member accounts in the resource directory. You cannot use a member account to specify an MNS topic to receive event notifications. The notifications of events that occur under the member account are sent to the MNS topic that is specified by using the master account.

-   The master account is used to log on to the Cloud Config for Enterprise console.
-   MNS is activated. For more information, see [Activate Message Service]().

For more information about MNS, see [What is MNS?]()

The following table describes the types of events that Cloud Config for Enterprise supports.

|Even type|Description|
|---------|-----------|
|[Resource change events](/intl.en-US/Events/Event types/Resource change events.md)|If the resources of the specified types are added or deleted, or the resource configurations are changed, Cloud Config for Enterprise will send notifications to you at the earliest opportunity.|
|[Resource non-compliance events](/intl.en-US/Events/Event types/Resource non-compliance events.md)|If you have configured rules, Cloud Config for Enterprise evaluates your resources based on the rules at regular intervals or when resource configurations are changed. If the resources are evaluated as **Non-compliant**, Cloud Config for Enterprise will send notifications to you at the earliest opportunity.|
|[Resource snapshot delivery events](/intl.en-US/Events/Event types/Resource snapshot delivery events.md)|If you have enabled the snapshot feature, Cloud Config for Enterprise delivers the snapshots of resource configuration changes as objects to the specified Object Storage Service \(OSS\) bucket at regular intervals. Cloud Config for Enterprise will send the delivery notifications to you at the earliest opportunity when such an event occurs.|

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Send Notifications to MNS**.

3.  On the **Send Notifications to MNS** page, turn on **MNS Settings**.

4.  Specify an MNS topic to receive event notifications.

    You can create an MNS topic or select an existing MNS topic to receive notifications of events that occur under the master account and each member account. You can specify an MNS topic that belongs to the master account or a member account.

    -   To specify a topic that belongs to the master account, select **Create a topic** or **Select an existing topic of your account**, and set the parameters as described in the following table.

        |Parameter|Description|
        |---------|-----------|
        |**MNS Region**|The region where the MNS topic resides.|
        |**Topic Name**|The name of the MNS topic to receive event notifications. The name must be unique to an Alibaba Cloud account in a region.        -   If you select **Create a topic**, you must specify a topic name.
        -   If you select **Select an existing topic of your account**, you must select an existing topic from the Topic Name drop-down list.

For more information about how to create a topic in MNS, see [Create a topic](). |
        |**Maximum Message Size \(Byte\)**|The maximum length of the notification body to be sent to the MNS topic, in bytes. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
        |**Enable Logging**|Specifies whether to enable log management for the topic.|
        |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to subscribe to. Valid values:         -   **All Risk Levels**
        -   **High Risk**
        -   **Medium Risk**
        -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config for Enterprise sends notifications about the non-compliance events at the **Medium Risk** and **High Risk** levels. The non-compliance events at the **Low Risk** level are ignored. |
        |**Resources to Subscribe**|The types of resources of which you want to subscribe to events. Valid values:        -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
        -   **Custom Resource Types**: Subscribe to the events of the selected types of resources. |

    -   To specify a topic that belongs to a member account, select **Select an existing topic of another account \(enterprise account only\)** and set the parameters as described in the following table. Make sure that the specified member account has an available MNS topic.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the topic that belongs to the destination account**|The Alibaba Cloud Resource Name \(ARN\) of the specified topic in the member account.The ARN must be in the format of `acs:mns:{regionId}:{Aliuid}:/topics/{topicName}`. The following content describes the fields in the format:

        -   `{regionId}`: the region where the MNS topic resides, such as cn-shanghai.
        -   `{Aliuid}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `{topicName}`: the name of the topic, such as topic1.
An example of a topic ARN is acs:mns:cn-shanghai:178589740730\*\*\*\*:/topics/topic1. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account.The ARN of the role must be in the format of `acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`. The following content describes the fields in the format:

        -   `{Aliuid}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service linked role that authorizes Cloud Config to send the notifications of resource events to the specified MNS topic.
An example of a role ARN is acs:ram::178589740730\*\*\*\*:role/aliyunserviceroleforconfig. |

5.  Click **OK**.


