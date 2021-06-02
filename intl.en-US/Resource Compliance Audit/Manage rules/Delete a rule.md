# Delete a rule

When you no longer need a rule, you can delete it. You can delete a rule in the Cloud Config console. After you delete the rule, all of its configurations are deleted. You can delete only the rules that you create in the rule list. You cannot delete the preset rules in compliance packages.

The rule that you want to delete is disabled. For more information, see [Disable a rule](/intl.en-US/Resource Compliance Audit/Manage rules/Disable a rule.md).

After you enable a compliance package, rules whose names are prefixed with the compliance package name are automatically generated in the Cloud Config console. You cannot directly delete these rules. To delete such a rule, you must delete the compliance package of the rule or turn off the ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png) switch for the rule. For information about how to delete a compliance package, see [Delete a compliance package](/intl.en-US/Resource compliance packages/Delete a CIS compliance package.md).

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, set filter conditions to find the rules in the **Inactive** state.

4.  Delete one or more rules as required.

    -   To delete a single rule, perform the following steps:
        1.  Find the rule that you want to delete, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Delete**.
        2.  In the **Are you sure you want to delete the rule?** message, click **Delete**.
    -   To delete multiple rules at a time, perform the following steps:
        1.  Select the rules that you want to delete and click the ![Delete](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3471333061/p170205.png) icon.
        2.  In the Delete Selected Rules message, click **OK**.
5.  Verify that the rule is deleted.

    After you delete a rule, it is no longer displayed on the **Rules** page.


## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  On the account group tab, set filter conditions to find the rules in the **Inactive** state.

5.  Delete one or more rules as required.

    -   To delete a single rule, perform the following steps:
        1.  Find the rule that you want to delete, move the pointer over the ![More icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3060019951/p93049.png) icon in the **Actions** column, and then select **Delete**.
        2.  In the **Are you sure you want to delete the rule?** message, click **Delete**.
    -   To delete multiple rules at a time, perform the following steps:
        1.  Select the rules that you want to delete and click the ![Delete](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3471333061/p170205.png) icon.
        2.  In the Delete Selected Rules message, click **OK**.
6.  Verify that the rule is deleted.

    After you delete a rule, it is no longer displayed on the account group tab.


