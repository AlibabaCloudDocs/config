# Send notifications of resource events to an MNS topic

Cloud Config allows you to specify a Message Service \(MNS\) topic to receive the notifications of resource change events, resource non-compliance events, and resource snapshot delivery events. You can also specify the push method and content of the topic.

MNS is activated. For more information, see [Activate MNS and authorize RAM users to access MNS]().

## Use an ordinary account

You can specify an MNS topic to receive the notifications of the resource events that belong to your Alibaba Cloud account.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Subscribe to Resource Events**.

3.  On the Subscribe to Resource Events page, turn on **MNS Settings**.

4.  Set the required parameters to specify an MNS topic to receive event notifications.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**MNS Region**|The region where the MNS topic resides.|
    |**Topic Name**|The name of the MNS topic. The topic name must be unique within your Alibaba Cloud account in the specified region.     -   If you select **Create a topic in the account**, you must specify a topic name.
    -   If you select **Select an existing topic from the account**, you must select an existing topic from the Topic Name drop-down list. |
    |**Maximum Message Size \(Byte\)**|The maximum length of the notification body that can be sent to the topic. Unit: byte. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
    |**Enable Logging**|Specifies whether to store the operations logs of the MNS topic in the associated Log Service Logstore. The operations logs are generated when notifications are received, forwarded, and deleted.|
    |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to which you want to subscribe. Valid values:     -   **All Risk Levels**
    -   **High Risk**
    -   **Medium Risk**
    -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications of the non-compliance events at the **Medium Risk** and **High Risk** levels. The non-compliance events at the **Low Risk** level are ignored. |
    |**Resources to Subscribe**|The types of the resources whose events you want to subscribe to. Valid values:    -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
    -   **Custom Resource Types**: Subscribe to the events of the specified types of resources. |

5.  Click **OK**.


## Use a management account

You can use a management account to specify an MNS topic to receive the notifications of the resource events of the management account and its member accounts. Only management accounts are authorized to configure the subscription settings of resource events. No member accounts have the relevant permissions.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Subscribe to Resource Events**.

3.  On the Subscribe to Resource Events page, turn on **MNS Settings**.

4.  Set the required parameters to specify an MNS topic to receive event notifications.

    You can create an MNS topic within the management account, or select an existing MNS topic that belongs to the management account or a member account. The specified MNS topic receives the notifications of the resource events that occur within the management account and its member accounts.

    -   To send notifications of resource events to a topic that belongs to the management account, select **Create a topic in the account** or **Select an existing topic from the account**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**MNS Region**|The region where the MNS topic resides.|
        |**Topic Name**|The name of the MNS topic. The topic name must be unique within the management account in the specified region.         -   If you select **Create a topic in the account**, you must specify a topic name.
        -   If you select **Select an existing topic from the account**, you must select an existing topic from the Topic Name drop-down list. |
        |**Maximum Message Size \(Byte\)**|The maximum length of the notification body that can be sent to the topic. Unit: byte. Valid values: 1024 to 65536. Default value: 65536. **Note:** We recommend that you set this parameter to a value greater than or equal to 8192. Otherwise, the notification delivery may fail due to the length limit. |
        |**Enable Logging**|Specifies whether to store the operations logs of the MNS topic in the associated Log Service Logstore. The operations logs are generated when notifications are received, forwarded, and deleted.|
        |**Minimum Risk Level of the Events to Subscribe**|The lowest risk level of the events to which you want to subscribe. If you have configured rules, you can receive resource non-compliance events. You can set the **Minimum Risk Level of the Events to Subscribe** parameter to filter the resource non-compliance events to be received. Valid values:         -   **All Risk Levels**
        -   **High Risk**
        -   **Medium Risk**
        -   **Low Risk**
For example, if you select **Medium Risk**, Cloud Config sends notifications of the non-compliance events at the **Medium Risk** and **High Risk** levels. The non-compliance events at the **Low Risk** level are ignored. |
        |**Resources to Subscribe**|The types of the resources whose events you want to subscribe to. Valid values:        -   **All Supported Resource Types**: Subscribe to the events of all supported types of resources. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
        -   **Custom Resource Types**: Subscribe to the events of the specified types of resources. |

    -   To send notifications of resource events to a topic that belongs to a member account, select **Select an existing topic from other enterprise management accounts**, and then set the required parameters. Before you set the parameters, make sure that the member account has available topics. The following table describes the parameters that are used to specify the Alibaba Cloud Resource Name \(ARN\) of the topic within the member account and the ARN of the role to be assumed by the member account.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the topic that belongs to the destination account**|The ARN of the topic in the member account, such as `acs:mns:ap-southeast-1:178589740730****:/topics/topic1`. The ARN must be in the format of `acs:mns:{regionId}:{AccountID}:/topics/{topicName}`. The following list describes the fields:

        -   `{regionId}`: the ID of the region where the topic resides, such as ap-southeast-1. For more information about how to view the region where a topic resides, see [Create a topic]().
        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*. For more information about how to view the ID of a member account, see [View the detailed information of a member account]().
        -   `{topicName}`: the name of the topic, such as topic1. For more information about how to view the name of a topic, see [Create a topic](). |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, such as `acs:ram::178589740730****:role/aliyunserviceroleforconfig`. The ARN must be in the format of `acs:ram::{AccountID}:role/aliyunserviceroleforconfig`. The following list describes the fields:

        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*. For more information about how to view the ID of a member account, see [View the detailed information of a member account]().
        -   `aliyunserviceroleforconfig`: the role that authorizes Cloud Config to access other Alibaba Cloud services. |

5.  Click **OK**.


After the notifications of resource events are sent to the specified topic, you can log on to the MNS console to specify the push method and content of the topic. For more information, see [Publish a message]().

