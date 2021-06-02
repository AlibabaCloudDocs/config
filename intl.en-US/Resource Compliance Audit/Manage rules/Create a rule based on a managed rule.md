# Create a rule based on a managed rule

A rule is a piece of logical judgment code that is stored in a rule function of Function Compute. You can create a rule based on a managed rule that is provided by Cloud Config to audit associated resources.

Before you create a rule, you must familiarize yourself with the definition of rules and how rules work. For more information, see [Rule definition and implementation]().

Cloud Config allows you to manage the following two types of rules:

-   Managed rules

    A managed rule is a rule function that Cloud Config creates in Function Compute. If you create a rule based on a managed rule, you can directly select the managed rule in the Cloud Config console. For more information about the managed rules that Cloud Config provides, see [Managed rules](/intl.en-US/Preset rules/Managed rules.md).

-   Custom rules

    A custom rule is created based on a rule function that you create in Function Compute. To create a rule based on a rule function, you must create the rule function in Function Compute and enter the Alibaba Cloud Resource Name \(ARN\) of the rule function in the Cloud Config console. For more information about the code and input parameters of a custom rule function, see [Create a custom rule by using Function Compute]().


## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  On the **Create Rule** page, search for a managed rule based on the rule name, tag, evaluation logic, or risk level.

5.  Click **Apply Rule**.

6.  In the **Properties** step, set the Rule Name, Risk Level, and Description parameters. Then, click **Next**.

    The Rule Name, Risk Level, and Trigger Type parameters have default values. You can change the values of the Rule Name and Risk Level parameters.

7.  In the **Access Resource Scope** step, keep the default resource type and click **Next**.

8.  In the **Parameters** step, click **Next**.

    If the managed rule has an input parameter, you must set an expected value for the input parameter.

9.  In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [t1877224.md\#](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [t1877298.md\#](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

10. In the **Preview and Save** step, check the configurations and click **Submit**.

11. Verify that the rule is created.

    -   Click . On the page that appears, you can view the rule details on the , , and tabs.
    -   Click . In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  On the account group tab, click **Create Rule**.

5.  On the **Create Rule** page, search for a managed rule based on the rule name, tag, evaluation logic, or risk level.

6.  Click **Apply Rule**.

7.  In the **Properties** step, set the Rule Name, Risk Level, and Description parameters. Then, click **Next**.

    The Rule Name, Risk Level, and Trigger Type parameters have default values. You can change the values of the Rule Name and Risk Level parameters.

8.  In the **Access Resource Scope** step, keep the default resource type and click **Next**.

9.  In the **Parameters** step, click **Next**.

    If the managed rule has an input parameter, you must set an expected value for the input parameter.

10. In the **Modify** step, click **Next**.

    For managed rules that allow you to modify the remediation settings, you can select the check box next to **Modify** and set the remediation method, remediation type, and parameters involved. For more information, see [t1877224.md\#](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) or [t1877298.md\#](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

11. In the **Preview and Save** step, check the configurations and click **Submit**.

12. Verify that the rule is created.

    -   Click . On the page that appears, you can view the rule details on the , , and tabs.
    -   Click . In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

