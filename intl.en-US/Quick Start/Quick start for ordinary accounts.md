# Quick start for ordinary accounts

This topic helps you get started with Cloud Config by using an ordinary account.

## Procedure

The following table describes the steps to get started with Cloud Config by using an ordinary account.

|Step|Description|
|----|-----------|
|[Step 1: Authorize Cloud Config to access your resources](#section_wkj_d35_7ty)|Before you use Cloud Config, you must authorize Cloud Config to access your resources.|
|[Step 2: View the resource list](#section_n9b_25s_mja)|You can view and manage the resources within your account.|
|[Step 3: Enable a compliance package](#section_lbc_wui_i6x)|You can enable a compliance package based on a compliance package template. After you enable a compliance package, you can view the compliance evaluation results of associated resources based on the specified rule.|
|[Step 4: Create a rule](#section_4s0_f3p_72v)|You can create a rule based on a managed rule.|
|[Step 5: \(Optional\) Set the monitoring scope](#section_vm5_dqw_qdp)|By default, Cloud Config monitors all supported types of resources. You can specify the types of resources to be monitored by Cloud Config.|
|[Step 6: Configure the delivery settings of resource data](#section_jby_8o5_nd0)|You can specify an Object Storage Service \(OSS\) bucket to receive resource snapshots within your account. This way, resource snapshots can be managed in a centralized manner.|
|[Step 7: Configure the subscription settings of resource events](#section_z5g_1m0_3f2)|You can specify a Message Service \(MNS\) topic to receive notifications of resource events within your account. This way, notifications of resource events can be managed in a centralized manner.|

## Step 1: Authorize Cloud Config to access your resources

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the Authorize step, click **Allow** to create the service-linked role that authorizes Cloud Config to access your resources.

    ![Authorize](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7635560951/p89255.png)

    **Note:** Cloud Config needs 2 to 10 minutes to scan your resources and generate a resource list.


## Step 2: View the resource list

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, set filter conditions or enter a resource ID to search for the specified resource. You can filter resources based on the resource type, region, compliance status, and resource status.

4.  Find the resource that you want to manage and click the resource ID in the **Resource ID / Resource Name** column.

5.  On the **Details** tab, view the basic information, core configuration, and latest compliance evaluation result of the resource.

    -   In the **Basic Information** section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Configuration Details** section, you can click **View JSON** to view the core configuration in the JSON format.
    -   In the **Most Recent Evaluation** section, you can view the latest compliance evaluation result of the resource.

## Step 3: Enable a compliance package

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click **Enable Compliance Package** in the upper-right corner.

4.  In the **Select a compliance package template** dialog box, click **Use** corresponding to the compliance package template based on which you want to enable a compliance package.

    In the **Select a compliance package template** dialog box, the following compliance package templates are available: **ClassifiedProtectionPreCheck**, **CISComplianceCheck**, **BestPracticesForOSS**, **BestPracticesForNetwork**, **BestPracticesForAccountGovernance**, **BestPracticesForDataBase**, **BestPracticesForECS**, and **RMiTComplianceCheck**.

5.  On the compliance package settings page, set the name, risk level, and rules of the compliance package.

    **Note:**

    -   Each compliance package name must be unique.
    -   By default, all the rules of the compliance package are enabled. To disable a rule that you no longer require, turn off the ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png) switch for the rule. To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
6.  Click **Enable Compliance Package** in the upper-right corner to enable the compliance package.

    On the **BestPracticesForOSS** page, you can view the name, status, risk level, and description of the compliance package. You can also edit, delete, or view the compliance package.


## Step 4: Create a rule

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  On the **Create Rule** page, search for a managed rule based on the rule name, tag, evaluation logic, or risk level.

5.  Click **Apply Rule**.

6.  In the **Properties** step, set the Rule Name, Risk Level, and Description parameters. Then, click **Next**.

    The Rule Name, Risk Level, and Trigger Type parameters have default values. You can change the values of the Rule Name and Risk Level parameters.

7.  In the **Access Resource Scope** step, keep the default resource type and click **Next**.

8.  In the **Parameters** step, click **Next**.

    If the managed rule has an input parameter, you must set an expected value for the input parameter.

9.  In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

10. In the **Preview and Save** step, check the configurations and click **Submit**.

11. Verify that the rule is created.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

## Step 5: \(Optional\) Set the monitoring scope

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Settings** \> **Monitoring Scope**.

3.  On the **Monitoring Scope** page, click the **Edit** icon in the upper-right corner.

4.  Specify the types of resources to be monitored.

    -   If you select **All Supported Resource Types**, Cloud Config monitors all supported types of resources that belong to your Alibaba Cloud account. If a new service is integrated with Cloud Config, the resource type of the service is automatically added to the monitoring scope.
    -   If you select **Custom Resource Types**, you can specify the types of resources to be monitored. In this case, Cloud Config monitors only the specified types of resources that belong to your Alibaba Cloud account.
5.  Click **OK**.


## Step 6: Configure the delivery settings of resource data

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Set the required parameters to specify an OSS bucket to store resource snapshots.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Region**|The region where the OSS bucket resides.|
    |**Bucket**|The name of the OSS bucket. The bucket name must be unique.     -   If you select **Create Bucket**, you must specify a bucket name.
    -   If you select **Select Buckets**, you must select an existing bucket from the Bucket drop-down list. |
    |**Server-side Encryption**|Specifies whether to encrypt objects in the OSS bucket. This parameter must be specified if you select **Create Bucket**. Valid values:

    -   **No**
    -   **AES256**
    -   **KMS** |

5.  Click **OK**.


## Step 7: Configure the subscription settings of resource events

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


