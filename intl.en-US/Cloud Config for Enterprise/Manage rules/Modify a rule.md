# Modify a rule

This topic describes how to modify a rule. If a rule does not meet your requirements, you can modify the keys and values of the input parameters.

The master account is used to log on to the Cloud Config for Enterprise console.

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, find the rule and click **Edit** in the **Actions** column.

4.  In the **Basic Settings** step, modify the description of the rule, and then click **Next**.

5.  In the **Parameter Settings** step, modify the settings as prompted, and then click **Submit**.

    -   If the **Method** is set to **Managed Rule** in the **Basic Settings** step, you can modify only the values of the input parameters.
    -   If the **Method** is set to **Function Compute** in the **Basic Settings** step, you can modify the resource types and the keys and values of the input parameters.
    -   If the **Method** is set to **Visual Editor** in the **Basic Settings** step, you can modify the resource types and values of the input parameters.
    -   The value of the Apply Rule to All Members parameter cannot be modified. If you modify a rule that applies to all member accounts, the modified rule also applies to all member accounts. Proceed with caution.
6.  View the rule modification result.

    In the **Complete** step, view the rule modification result.

    -   Click **View Details**. On the page that appears, you can view the **Basic Information**, **Trigger**, and **Compliance Result of Related Resources** of the modified rule.
    -   Click **Return to Rule List**. On the **Rules** page, you can view the modified rule. The status of the rule is **Active**.

