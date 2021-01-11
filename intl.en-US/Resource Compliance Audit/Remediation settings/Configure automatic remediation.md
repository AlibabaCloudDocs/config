# Configure automatic remediation

When you create a rule, you can configure a remediation template for the rule. You can configure automatic remediation for the template. If a resource is evaluated to be non-compliant, the template automatically runs to remediate the configurations of the resource.

This topic describes how to configure automatic remediation by creating a managed rule named **required-tags**.

The **required-tags** rule is a managed rule that you can use to check whether associated resources have specified tags. In this example, assume that the tag "Project=A" must be attached to all Elastic Compute Service \(ECS\) instances. You can use the **required-tags** rule to monitor all ECS instances. If Cloud Config detects that the tag is not attached to one or more ECS instances, these resources are evaluated to be non-compliant based on the rule. If you subscribe to resource non-compliance events, Cloud Config sends notifications of resource non-compliance events to a specified Message Service \(MNS\) topic. For more information, see [Send notifications of resource events to an MNS topic](/intl.en-US/Events/Send notifications of resource events to an MNS topic.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Rules** step, select **Managed Rule** in the **Method** section, find and select the **required-tags** rule, select a risk level for the rule, and then click **Next**.

    ![Basic Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

5.  In the **Parameter Settings** step, enter the key and value of a tag, and then click **Next**.

    ![Parameter Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

    If you want to check multiple tags, you can set multiple key-value pairs in sequence. You can set up to six key-value pairs. If all specified resources have specified tags, these resources are evaluated to be compliant based on the rule. If you want to check whether a specified tag is attached to specified resources, you must create a rule for each tag by selecting the required-tags rule.

    In this example, assume that the tag "Project=A" must be attached to all of your resources. You can use the **required-tags** rule to monitor all of your resources. If Cloud Config detects that the tag is not attached to one or more of your resources, these resources are evaluated to be non-compliant.

    **Note:** Default settings are used for the trigger type, related resources, and input parameters.

6.  In the **Remediation Settings** step, select **Automatic Remediation** in the Remediation Method section, select the default template from the **Workflow** drop-down list, authorize Logic Composer to assume the RAM roles, confirm the settings of the parameters, and then click **Submit**.

    ![Remediation Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9356430161/p94789.png)

7.  View the remediation results.

    If a resource is evaluated to be **non-compliant** based on the rule, Cloud Config triggers the remediation template. The configurations of the non-compliant resource are automatically changed to the preset values.

    -   View the remediation results on the **Rules** page.
        1.  On the **Rules** page, filter the rules whose **Compliance** column displays **Non-compliant**.
        2.  Click **Details** in the **Actions** column or the rule ID in the **Rule Name/Rule ID** column.
        3.  Click the **Correction Details** tab. On the Correction Details tab, you can view the remediation settings and remediation history.
    -   View the remediation results on the **Resources** page.
        1.  In the left-side navigation pane, click **Resources**.
        2.  On the **Resources** page, search for or filter the non-compliant resources.
        3.  Click the resource ID in the **Resource ID / Resource Name** column. On the **Details** tab, you can view the latest compliance evaluation result.
        4.  In the **Most Recent Evaluation** section, click the rule ID in the **Rule Name** column. The **Rule Details** tab of the details page for the rule appears.
        5.  Click the **Correction Details** tab. On the Correction Details tab, you can view the remediation settings and remediation history.
    **Note:**

    -   If you modify the parameter settings of a remediation template and save the settings, the remediation results and remediation history are deleted.
    -   If you modify the remediation method of a remediation template, the remediation results and remediation history are retained.

