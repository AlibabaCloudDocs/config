# Modify a rule

This topic describes how to modify a rule. If a rule does not meet your requirements, you can modify the keys and values of the input parameters.

The master account is used to log on to the Cloud Config for Enterprise console.

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, find the rule that you want to modify and click **Edit** in the **Actions** column.

4.  In the **Basic Settings** step, modify the description of the rule and click **Next**.

5.  In the **Parameter Settings** step, modify the configuration as required and click **Submit**.

    -   If the **Method** parameter is set to **Managed Rule** in the **Basic Settings** step, you can modify only the values of the input parameters.
    -   If the **Method** parameter is set to **Function Compute** in the **Basic Settings** step, you can modify the resource types and the values of the existing input parameters. You can also specify new input parameters as required.
    -   If the **Method** parameter is set to **Visual Editor** in the **Basic Settings** step, you can modify the resource types and the values of the input parameters.
    -   The value of the Apply Rule to All Members parameter cannot be modified. If you modify a rule that applies to all member accounts, the modified rule still applies to all member accounts. Proceed with caution.
6.  View the modification result.

    In the **Complete** step, view the modification result.

    -   Click **View Details**. On the page that appears, you can view the updated information in the **Basic Information**, **Trigger**, and **Compliance Result of Related Resources** sections.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the modified rule. The status of the rule is **Active**.

