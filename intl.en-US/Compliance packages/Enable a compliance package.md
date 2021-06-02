# Enable a compliance package

A compliance package template is a scenario-specific collection of managed rules that Cloud Config assembles to evaluate the compliance of resources. You can enable a compliance package based on a compliance package template. After you enable a compliance package, you can view the compliance evaluation results of associated resources based on the specified account and rule.

Cloud Config provides eight compliance package templates. For more information, see [Overview](/intl.en-US/Compliance packages/Overview.md).

After you enable a compliance package, rules whose names are prefixed with the compliance package name are automatically generated in the Cloud Config console. You cannot directly modify, delete, enable, or disable these rules.

When you use a compliance package, pay attention to the following rules:

-   If you use an ordinary account, you can enable a maximum of five compliance packages.
-   If you use a management account, you can enable a maximum of five compliance packages on the Current Account tab or each account group tab.

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click **Enable Compliance Package** in the upper-right corner.

4.  In the **Select a compliance package template** dialog box, click **Use** corresponding to the compliance package template based on which you want to enable a compliance package.

    In the **Select a compliance package template** dialog box, the following compliance package templates are available: **ClassifiedProtectionPreCheck**, **CISComplianceCheck**, **BestPracticesForOSS**, **BestPracticesForNetwork**, **BestPracticesForAccountGovernance**, **BestPracticesForDataBase**, **BestPracticesForECS**, and **RMiTComplianceCheck**.

5.  On the compliance package settings page, set the name, risk level, and rules of the compliance package.

    **Note:**

    -   Each compliance package name must be unique.
    -   By default, all the rules of the compliance package are enabled. To disable a rule that you no longer require, turn off the ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png) switch for the rule. To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
6.  Click **Enable Compliance Package** in the upper-right corner to enable the compliance package.

    On the **BestPracticesForOSS** page, you can view the name, status, risk level, and description of the compliance package. You can also edit, delete, or view the compliance package.


## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click the required account group tab.

4.  On the account group tab, click **Enable Compliance Package** in the upper-right corner.

5.  In the **Select a compliance package template** dialog box, click **Use** corresponding to the compliance package template based on which you want to enable a compliance package.

    In the **Select a compliance package template** dialog box, the following compliance package templates are available: **ClassifiedProtectionPreCheck**, **CISComplianceCheck**, **BestPracticesForOSS**, **BestPracticesForNetwork**, **BestPracticesForAccountGovernance**, **BestPracticesForDataBase**, **BestPracticesForECS**, and **RMiTComplianceCheck**.

6.  On the compliance package settings page, set the name, risk level, and rules of the compliance package.

    **Note:**

    -   Each compliance package name must be unique.
    -   By default, all the rules of the compliance package are enabled. To disable a rule that you no longer require, turn off the ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png) switch for the rule. To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
7.  Click **Enable Compliance Package** in the upper-right corner to enable the compliance package.

    On the account group tab, you can view the name, status, risk level, and description of the compliance package. You can also edit, delete, or view the compliance package.


