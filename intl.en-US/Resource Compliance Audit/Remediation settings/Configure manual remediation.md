# Configure manual remediation

When you create a rule, you can associate the rule with a remediation template and select Manual Execution for the template. If a resource configuration is non-compliant, you can manually run the template to correct the configuration.

This following section describes how to configure manual remediation. In this topic, the **required-tags** rule is selected.

The **required-tags** rule is a managed rule that you can use to check whether specified tags are attached to a resource. For example, the tag "Project=A" must be attached to all Elastic Compute Service \(ECS\) instances. You can use the **required-tags** rule to monitor all ECS instances. If Cloud Config detects that the tag is not attached to one or more ECS instances, the rule evaluates the ECS instances as **Non-compliant**. If you subscribe to non-compliance events, Cloud Config sends non-compliance alerts to the Message Service \(MNS\) topic that you specify. For more information, see [Send notifications of resource events to an MNS topic](/intl.en-US/Events/Subscribe to events.md).

1.  Configure the remediation settings.

    1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

    2.  In the left-side navigation pane, click **Rules**.

    3.  On the **Rules** page, click **Create Rule**.

    4.  In the **Basic Settings** step, set the **Method** parameter to **Managed Rule**, search for and select the **required-tags** rule, select a risk level for the rule, and then click **Next**.

        ![Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

    5.  In the **Parameter Settings** step, use default settings for the trigger type, related resources, and input parameters. Enter the keys and values of the tags, and then click **Next**.

        ![Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

        If you need to check multiple tags, you can set multiple key-value pairs one by one. You can set up to six key-value pairs. The rule evaluates resources to which the rule is applied as **Compliant** only when all specified tags are attached to the resources. If you need to check whether a tag in a tag group is attached to a resource type, you must create a rule for each tag.

        Assume that the tag "Project=A" must be attached to all your resources. You can use the **required-tags** rule to monitor all your resources. If Cloud Config detects that the tag is not attached to one or more of your resources, the rule evaluates the resources as **Non-compliant**.

        **Note:** When you create a rule by using a managed rule, the default settings for the trigger type, related resources, and input parameters are used.

    6.  In the **Remediation Settings** step, set the Remediation Method parameter to **Manual Remediation**, select the default template from the **Workflow** drop-down list, authorize Logic Composer to assume the RAM roles, confirm the settings of the parameters, and then click **Submit**.

        ![Manual remediation](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7412333061/p95309.png)

    7.  View the rule creation result.

        In the **Complete** step, you can view the creation result of the rule. You can also go to the Rules page to view and manage the rule.

        -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
        -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.
2.  Remediate non-compliant resources.

    If you receive a non-compliance alert or find non-compliant resources, you can manually trigger the remediation template on the **Correction Details** tab of the details page of the specified rule. The configurations of the non-compliant resources are automatically changed to your preset value. To manually remediate non-compliant resources, perform the following steps:

    1.  On the **Rules** page, find the rule, and click **Details** in the **Actions** column or the rule ID in the **Rule Name/Rule ID** column.

    2.  On the details page of the rule, click the **Correction Details** tab.

    3.  On the **Correction Details** tab, click **Perform Manual Correction**, which is displayed when the **Remediation Method** parameter is set to Manual.

3.  View the remediation results.

    If a rule evaluates resources to which the rule is applied as **Non-compliant**, Cloud Config triggers the remediation template. The configurations of the non-compliant resources are automatically changed to your preset value.

    -   View the remediation results on the **Rules** page.
        1.  On the **Rules** page, filter the rules based on which resources are evaluated as **Non-compliant** in the **Compliance** column.
        2.  Click **Details** in the **Actions** column or the rule ID in the **Rule Name/Rule ID** column.
        3.  Click the **Correction Details** tab. On the Correction Details tab, you can view the remediation settings and remediation history.
    -   View the remediation results on the **Resources** page.
        1.  On the **Resources** page, search for or filter the non-compliant resources.
        2.  Click the resource ID in the **Resource ID / Resource Name** column. On the **Details** tab, you can view the latest compliance evaluation result.
        3.  In the **Most Recent Evaluation** section, click the rule ID in the **Rule Name** column. The **Rule Details** tab of the details page of the rule appears.
        4.  Click the **Correction Details** tab. On the Correction Details tab, you can view the remediation settings and remediation history.
    **Note:**

    -   If you modify the parameter settings of a remediation template and save the settings, the remediation results and remediation history are deleted.
    -   If you modify the remediation method of a remediation template, the remediation results and remediation history are retained.

