# Manually re-evaluate resources

This topic describes how to manually re-evaluate resources. After you modify a rule in the Cloud Config for Enterprise console, you can manually re-evaluate resources if you want to immediately view the latest compliance evaluation result. If you do not manually re-evaluate the resources, you can view the compliance evaluation result only after resource configurations are changed or the associated rule is triggered at the scheduled time.

-   The master account is used to log on to the Cloud Config for Enterprise console.
-   The rule that you want to use to re-evaluate resources is in the **Active** state in the **Status** column.

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, set the filters to find the specific rule.

4.  Click the rule ID in the **Rule Name/Rule ID** column or click **Details** in the **Actions** column.

5.  On the **Rule Details** tab, click **Re-evaluate** in the upper-right corner.

    If the rule has been applied to all member accounts, it immediately re-evaluates the resources under all these accounts.


