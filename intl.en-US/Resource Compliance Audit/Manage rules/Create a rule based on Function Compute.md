# Create a rule based on Function Compute

If the managed rules provided by Cloud Config cannot meet your requirements on resource auditing, you can create rules based on Function Compute to audit associated resources. When a rule is triggered, Cloud Config invokes the corresponding rule function to evaluate the associated resources and returns the compliance evaluation results of the resources.

Function Compute is activated. For more information, see [Rule definition and implementation]().

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

4.  On the **Create Rule** page, click **Create Custom Rule**.

5.  In the **Properties** step, set the Function ARN, Rule Name, Risk Level, Trigger Type, and Description parameters. Then, click **Next**.

    -   If you have created a rule function, directly select the ARN of the function.
    -   If you have not created a rule function, click to create a rule function in the Function Compute console. For more information, see [Overview](https://www.alibabacloud.com/help/doc-detail/52077.htm).

        When you create a rule function, set the **Function Type** parameter to **Event Function**, the **Runtime** parameter to **Python 3**, and the **Function Handler** parameter to the default value **index.handler**.

6.  In the **Assess Resource Scope** step, specify the resource types associated with the rule and click **Next**.

7.  In the **Parameters** step, click **Add Rule Parameter**, specify a name and an expected value for an input parameter, and then click **Next**.

    -   After you specify the resource types, Cloud Config monitors all your resources of the specified types based on the rule. Each rule can be applied to one or more resource types.
    -   The names of the input parameters must be the same as those of the configuration items to be evaluated.
8.  In the **Modify** step, click **Next**.

9.  In the **Preview and Save** step, check the configurations and click **Submit**.

10. Verify that the rule is created.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click the required account group tab.

4.  On the account group tab, click **Create Rule**.

5.  On the **Create Rule** page, click **Create Custom Rule**.

6.  In the **Properties** step, set the Function ARN, Rule Name, Risk Level, Trigger Type, and Description parameters. Then, click **Next**.

    -   If you have created a rule function, directly select the ARN of the function.
    -   If you have not created a rule function, click to create a rule function in the Function Compute console. For more information, see [Overview](https://www.alibabacloud.com/help/doc-detail/52077.htm).

        When you create a rule function, set the **Function Type** parameter to **Event Function**, the **Runtime** parameter to **Python 3**, and the **Function Handler** parameter to the default value **index.handler**.

7.  In the **Assess Resource Scope** step, specify the resource types associated with the rule and click **Next**.

8.  In the **Parameters** step, click **Add Rule Parameter**, specify a name and an expected value for an input parameter, and then click **Next**.

    -   After you specify the resource types, Cloud Config monitors all your resources of the specified types based on the rule. Each rule can be applied to one or more resource types.
    -   The names of the input parameters must be the same as those of the configuration items to be evaluated.
9.  In the **Modify** step, click **Next**.

10. In the **Preview and Save** step, check the configurations and click **Submit**.

11. Verify that the rule is created.

    -   Click **View Details**. On the page that appears, you can view the rule details on the **Rule Details**, **Result**, and **Correction Details** tabs.
    -   Click **Return to Rule List**. In the **Rules** list, you can view the status of the created rule in the Status column. In normal cases, the rule is in the **Active** state.

