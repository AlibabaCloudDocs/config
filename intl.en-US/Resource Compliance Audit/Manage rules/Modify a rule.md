# Modify a rule

If existing rules cannot meet your compliance requirements, you can modify the rules as needed. You can modify only the created rules in the rule list. You cannot modify the preset rules in compliance packages.

After you enable a compliance package, rules whose names are prefixed with the compliance package name are automatically generated in the Cloud Config console. You cannot directly modify, delete, enable, or disable these rules. However, you can modify the compliance package to update the parameter settings of these rules. For more information, see [Edit a compliance package](/intl.en-US/Resource compliance packages/Edit a CIS compliance package.md).

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, find the rule that you want to modify and click **Edit** in the **Actions** column.

4.  In the **Properties** step, modify the description of the rule and click **Next**.

5.  In the **Assess Resource Scope** step, click **Next**.

    For managed rules that are associated with tags and custom rules, you can modify the related resources.

6.  In the **Parameters** step, modify the expected value of the input parameter and click **Next**.

    You can modify both the name and expected value of the input parameter of a custom rule.

7.  In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

8.  In the **Preview and Save** step, check the configurations and click **Submit**.

9.  View the modification result.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  On the account group tab, find the rule that you want to modify and click **Edit** in the **Actions** column.

5.  In the **Properties** step, modify the description of the rule and click **Next**.

6.  In the **Assess Resource Scope** step, click **Next**.

    For managed rules that are associated with tags and custom rules, you can modify the related resources.

7.  In the **Parameters** step, modify the expected value of the input parameter and click **Next**.

    You can modify both the name and expected value of the input parameter of a custom rule.

8.  In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

9.  In the **Preview and Save** step, check the configurations and click **Submit**.

10. View the modification result.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

