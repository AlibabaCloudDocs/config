# Quick start for management accounts

This topic helps you get started with Cloud Config by using a management account.

## Procedure

The following table describes the steps to get started with Cloud Config by using a management account.

|Step|Description|
|----|-----------|
|[Step 1: Authorize Cloud Config to access your resources](#section_wkj_d35_7ty)|Before you use Cloud Config, you must authorize Cloud Config to access your resources.|
|[Step 2: Create an account group](#section_z6u_afk_zhv)|You can use a management account to create an account group and add all or some member accounts in your resource directory to the account group. This way, you can manage the resources, compliance packages, and rules of multiple member accounts in an account group in a centralized manner.|
|[Step 3: View the resource list](#section_n9b_25s_mja)|You can use a management account to view the resources of all member accounts in a specified account group.|
|[Step 4: Enable a compliance package](#section_lbc_wui_i6x)|You can use a management account to enable a compliance package based on a compliance package template for a specified account group. After you enable a compliance package, you can view the compliance evaluation results of associated resources based on the specified account and rule.|
|[Step 5: Create a rule](#section_4s0_f3p_72v)|You can use a management account to create a rule based on a managed rule for a specified account group.|
|[Step 6: Configure the delivery settings of resource data](#section_jby_8o5_nd0)|You can use a management account to specify an Object Storage Service \(OSS\) bucket to receive the resource snapshots of the management account and its member accounts. This way, resource snapshots can be managed in a centralized manner. Only management accounts are authorized to configure the delivery settings of resource snapshots. No member accounts have the relevant permissions.|
|[Step 7: Configure the subscription settings of resource events](#section_z5g_1m0_3f2)|You can use a management account to specify a Message Service \(MNS\) topic to receive the notifications of the resource events of the management account and its member accounts. This way, notifications of resource events can be managed in a centralized manner. Only management accounts are authorized to configure the subscription settings of resource events. No member accounts have the relevant permissions.|

## Step 1: Authorize Cloud Config to access your resources

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the Authorize step, click **Allow** to create the service-linked role that authorizes Cloud Config to access your resources.

    ![Authorize](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7635560951/p89255.png)

    **Note:** Cloud Config needs 2 to 10 minutes to scan your resources and generate a resource list.


## Step 2: Create an account group

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Account Group**.

3.  On the **Account Group** page, click **Create**.

4.  On the **Create** page, configure a name and description for the account group, and then click **Add Member**.

5.  Specify member accounts from the resource directory and click **OK**.

6.  Click **Submit**.

    In the **Account Group** list, find the account group that you created. If the status of the account group is **Created**, the account group is created. You can also view the name, description, member account quantity, type, and creation time of the account group.


## Step 3: View the resource list

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, click the required account group tab.

4.  On the account group tab, set filter conditions or enter a resource ID to search for the specified resource. You can filter resources based on the resource type, owner, region, compliance status, and resource status.

5.  Find the resource that you want to manage and click the resource ID in the **Resource ID / Resource Name** column.

6.  On the **Details** tab, view the basic information, core configuration, and latest compliance evaluation result of the resource.

    -   In the **Basic Information** section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Configuration Details** section, you can click **View JSON** to view the core configuration in the JSON format.
    -   In the **Most Recent Evaluation** section, you can view the latest compliance evaluation result of the resource.

## Step 4: Enable a compliance package

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click the required account group tab.

4.  On the account group tab, click **Enable Compliance Package** in the upper-right corner.

5.  In the **Select a compliance package template.** dialog box, click **Use** corresponding to the compliance package template based on which you want to enable a compliance package.

    In the **Select a compliance package template.** dialog box, the following compliance package templates are available: **ClassifiedProtectionPreCheck**, **CISComplianceCheck**, **BestPracticesForOSS**, **BestPracticesForNetwork**, **BestPracticesForAccountGovernance**, **BestPracticesForDataBase**, **BestPracticesForECS**, and **RMiTComplianceCheck**.

6.  On the compliance package settings page, set the name, risk level, and rules of the compliance package.

    **Note:**

    -   Each compliance package name must be unique.
    -   By default, all the rules of the compliance package are enabled. To disable a rule that you no longer require, turn off the ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png) switch for the rule. To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
7.  Click **Enable Compliance Package** in the upper-right corner to enable the compliance package.

    On the account group tab, you can view the name, status, risk level, and description of the compliance package. You can also edit, delete, or view the compliance package.


## Step 5: Create a rule

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  On the account group tab, click **Create Rule**.

5.  On the **Create Rule** page, search for a managed rule based on the rule name, tag, evaluation logic, or risk level.

6.  Click **Apply Rule**.

7.  In the **Properties** step, set the Rule Name, Risk Level, and Description parameters. Then, click **Next**.

    The Rule Name, Risk Level, and Trigger Type parameters have default values. You can change the values of the Rule Name and Risk Level parameters.

8.  In the **Access Resource Scope** step, keep the default resource type and click **Next**.

9.  In the **Parameters** step, click **Next**.

    If the managed rule has an input parameter, you must set an expected value for the input parameter.

10. In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

11. In the **Preview and Save** step, check the configurations and click **Submit**.

12. Verify that the rule is created.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

## Step 6: Configure the delivery settings of resource data

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Set the required parameters to specify an OSS bucket to store resource snapshots.

    You can create an OSS bucket within the management account, or select an existing OSS bucket that belongs to the management account or a member account. The OSS bucket stores the resource snapshots within the management account and its member accounts.

    -   To deliver resource snapshots to an OSS bucket that belongs to the management account, select **Create Bucket** or **Select Buckets**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Region**|The region where the OSS bucket resides.|
        |**Bucket**|The name of the OSS bucket. The bucket name must be unique.         -   If you select **Create Bucket**, you must specify a bucket name.
        -   If you select **Select Buckets**, you must select an existing bucket from the Bucket drop-down list. |
        |**Server-side Encryption**|Specifies whether to encrypt objects in the OSS bucket. This parameter must be specified if you select **Create Bucket**. Valid values:

        -   **No**
        -   **AES256**
        -   **KMS** |

    -   To deliver resource snapshots to an OSS bucket that belongs to a member account, select **Select Buckets from Other Enterprise Management Accounts**, and then set the required parameters. Before you set the parameters, make sure that the member account has available buckets. The following table describes the parameters that are used to specify the Alibaba Cloud Resource Name \(ARN\) of the bucket within the member account and the ARN of the role to be assumed by the member account.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the bucket that belongs to the destination account**|The ARN of the bucket in the member account, such as `acs:oss:ap-southeast-1:178589740730****:test123`. The ARN must be in the format of `acs:oss:{regionId}:{AccountID}:{bucketName}`. The following list describes the fields:

        -   `{regionId}`: the ID of the region where the bucket resides, such as ap-southeast-1.
        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `{bucketName}`: the name of the bucket, such as test123. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, such as `acs:ram::178589740730****:role/aliyunserviceroleforconfig`. Before you set this parameter, make sure that you have obtained the ID of the member account. Then, set the parameter based on the required format.

The ARN must be in the format of `acs:ram::{AccountID}:role/aliyunserviceroleforconfig`. The following list describes the fields:

        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the role that authorizes Cloud Config to access other Alibaba Cloud services. |

5.  Click **OK**.


## Step 7: Configure the subscription settings of resource events

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


