# View compliance evaluation results

This topic describes how to view the compliance evaluation results of resources, rules, and member accounts. In the Cloud Config for Enterprise console, you can use the master account to view all non-compliant resources, and the rules and member accounts that are related to non-compliant resources in the resource directory. You can also view the configuration change snapshots of member accounts in a specified OSS bucket. A member account has only permissions to view non-compliant resources and related rules under the member account.

A rule is created. For more information, see [Create a rule](/intl.en-US/Resource Compliance Audit/Manage rules/Create a rule.md).

## View the rules related to non-compliant resources in the resource directory

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  View the rules based on which resources are evaluated as non-compliant.

    -   To view the rules on the **Member Account Overview** tab, perform the following steps:
        1.  On the **Overview** page, click **Member Account Overview**.
        2.  In the **Compliance** section of the Member Account Overview tab, find the member account and click the number in the **Non-compliant Rules** column. The **Rules** page of the member account appears.
        3.  On the **Rules** page, view all the rules based on which resources are evaluated as non-compliant under this member account.
    -   To view the rules on the **Rule Details** tab, perform the following steps:
        1.  In the left-side navigation pane, click **Rules**.
        2.  On the **Rules** page, click **master** in the left directory tree. On the page that appears, you can view all the rules that are created by using the master account and the compliance evaluation results.

            You can select a member account in the left directory tree to view the list of active rules and the compliance evaluation results of the member account.

        3.  In the rule list, find the rule, and then click the rule ID in the **Rule Name/Rule ID** column or **Details** in the **Actions** column.
        4.  On the **Rule Details** tab of the page that appears, view the basic information, trigger type, and compliance evaluation result of related resources of the rule.

## View non-compliant resources in the resource directory

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  View non-compliant resources.

    -   To view non-compliant rules on the **Member Account Overview** tab, perform the following steps:
        1.  On the **Overview** page, click **Member Account Overview**.
        2.  In the **Compliance** section of the Member Account Overview tab, find the member account and click the number in the **Non-compliant Resources** column. The **Resources** page of the member account appears.
        3.  On the **Resources** page, view all non-compliant resources in this member account.
    -   To view non-compliant resources on the **Resources** page, perform the following steps:
        1.  In the left-side navigation pane, click **Resources**.
        2.  On the **Resources** page, click **master** in the left directory tree. On the page that appears, view all the resources that belong to the master account and the compliance evaluation results of the resources.

            You can also click a member account in the directory tree to view the resource list of the member account and the compliance evaluation results of the resources.


