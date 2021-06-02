# Disable a rule

This topic describes how to disable a rule. You can disable a rule if you do not need it. You can disable only the created rules in the rule list. You cannot disable the preset rules in compliance packages.

The rules that you want to disable are in the **Active** state in the **Status** column.

After you enable a compliance package, rules whose names are prefixed with the compliance package name are automatically generated in the Cloud Config console. You cannot disable these rules.

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  Disable one or more rules as needed.

    -   Disable a single rule
        1.  On the **Rules** page, find the rule that you want to disable, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Disable Rule**.
        2.  In the **Are you sure you want to terminate the rule?** message, click **OK**.
    -   Disable multiple rules at a time
        1.  On the **Rules** page, find the rules that you want to disable, select the check boxes next to the rules, and then click the ![Disable icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2080062261/p260192.png) icon.
        2.  In the Disable Selected Rules message, click **OK**.
4.  View the status of the rules.

    On the **Rules** page, set filter conditions to search for the rules and check whether the rules are in the **Inactive** state. After a rule is disabled, it no longer takes effect. The compliance evaluation results that are returned before the rule is disabled are displayed.


## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  Disable one or more rules as needed.

    -   Disable a single rule
        1.  On the account group tab, find the rule that you want to disable, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Disable Rule**.
        2.  In the **Are you sure you want to terminate the rule?** message, click **OK**.
    -   Disable multiple rules at a time
        1.  On the account group tab, find the rules that you want to disable, select the check boxes next to the rules, and then click the ![Disable icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2080062261/p260192.png) icon.
        2.  In the Disable Selected Rules message, click **OK**.
5.  View the status of the rules.

    On the account group tab, set filter conditions to search for the rules and check whether the rules are in the **Inactive** state.


You can enable a rule that is in the **Inactive** state. After a rule is enabled, it enters the **Active** state again. To enable one or more disabled rules, perform the following steps:

-   Use an ordinary account
    -   Enable a single rule

        On the **Rules** page, find the rule that you want to enable, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Enable Rule**.

    -   Enable multiple rules at a time
        1.  On the **Rules** page, find the rules that you want to enable, select the check boxes next to the rules, and then click the ![Enable icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2080062261/p260200.png) icon.
        2.  In the Enable Selected Rules message, click **OK**.
-   Use a management account
    -   Enable a single rule

        On the account group tab, find the rule that you want to enable, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Enable Rule**.

    -   Enable multiple rules at a time
        1.  On the account group tab, find the rules that you want to enable, select the check boxes next to the rules, and then click the ![Enable icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2080062261/p260200.png) icon.
        2.  In the Enable Selected Rules message, click **OK**.

