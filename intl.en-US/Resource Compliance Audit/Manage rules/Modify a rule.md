# Modify a rule

This topic describes how to modify a rule. If a rule does not meet your requirements, you can modify the parameter settings of the rule.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, find the rule that you want to modify and click **Edit** in the **Actions** column.

4.  In the **Basic Settings** step, modify the description of the rule and click **Next**.

5.  In the **Parameter Settings** step, modify the configuration as required and click **Next**.

    -   If the **Method** parameter is set to **Managed Rule** in the **Basic Settings** step, you can modify only the values of the input parameters.
    -   If the **Method** parameter is set to **Function Compute** in the **Basic Settings** step, you can modify the resource types and the values of the existing input parameters. You can also specify new input parameters as required.
    -   If the **Method** parameter is set to **Visual Editor** in the **Basic Settings** step, you can modify the values of the input parameters.
6.  In the **Remediation Settings** step, set the Remediation Method parameter to **Disable Remediation** and click **Submit**.

    You can modify the configuration of the **required-tags** rule. In the Remediation Settings step, set the **Remediation Method** parameter to **Automatic Remediation** or **Manual Remediation**, select a remediation template from the **Workflow** drop-down list, complete authorization as required, and then click **Submit**.

7.  View the rule modification result.

    In the **Complete** step, view the rule modification result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

