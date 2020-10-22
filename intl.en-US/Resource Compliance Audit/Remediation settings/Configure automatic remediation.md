# Configure automatic remediation

When you create a rule, you can associate the rule with a remediation template and select Automatic Execution for the template. If a resource configuration is non-compliant, the template automatically runs to correct the configuration.

The following section describes how to configure automatic remediation. In this topic, the **required-tags** rule is selected.

The **required-tags** rule is a managed rule that you can use to check whether specified tags are attached to a resource. For example, the tag "Project=A" must be attached to all Elastic Compute Service \(ECS\) instances. You can use the **required-tags** rule to monitor all ECS instances. If Cloud Config detects that the tag is not attached to one or more ECS instances, the rule evaluates the ECS instances as **Non-compliant**. If you subscribe to non-compliance events, Cloud Config sends non-compliance alerts to the Message Service \(MNS\) topic that you specify. For more information, see [Send notifications of resource events to an MNS topic](/intl.en-US/Events/Subscribe to events.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Rules** step, set the **Method** parameter to **Managed Rule**, search for and select the **required-tags** rule, select a risk level for the rule, and then click **Next**.

    ![Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

5.  In the **Parameter Settings** step, enter the key and value of the tag, and then click **Next**.

    ![Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

    If you need to check multiple tags, you can set multiple key-value pairs one by one. You can set up to six key-value pairs. The rule evaluates resources to which the rule is applied as **Compliant** only when all specified tags are attached to the resources. If you need to check whether a tag in a tag group is attached to a resource type, you must create a rule for each tag.

    Assume that the tag "Project=A" must be attached to all your resources. You can use the **required-tags** rule to monitor all your resources. If Cloud Config detects that the tag is not attached to one or more of your resources, the rule evaluates the resources as **Non-compliant**.

    **Note:** When you create a rule by using a managed rule, the default settings for the trigger type, related resources, and input parameters are used.

6.  In the **Remediation Settings** step, set the Remediation Method parameter to **Automatic Remediation**, select the default template from the **Workflow** drop-down list, authorize Logic Composer to assume the RAM roles, confirm the settings of the parameters, and then click **Submit**.

    ![Remediation Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7791333061/p94789.png)

7.  View the remediation results.

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

