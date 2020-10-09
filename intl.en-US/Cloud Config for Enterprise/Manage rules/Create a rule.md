# Create a rule

This topic describes how to create a rule. The evaluation logic of a rule is implemented based on functions in the Function Compute service. You can create a rule based on a managed rule that is provided by Cloud Config. You can also create a custom rule by using Function Compute and the visual editor.

The master account is used to log on to the Cloud Config for Enterprise console.

Before you create a rule, you must familiarize yourself with the definition of rules and how rules work. For more information, see [Rule definition and implementation](/intl.en-US/Resource Compliance Audit/Rule definition and implementation.md).

## Create a rule based on a managed rule

For the list of managed rules, see [Managed rules](/intl.en-US/Resource Compliance Audit/Preset rules/Managed rules.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set **Method** to **Managed Rule**. Select a rule and risk level, determine whether to apply the rule to all member accounts, and then click **Next**.

    ![Create a rule based on a managed rule](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3708478851/p97236.png)

5.  In the **Parameter Settings** step, specify the value of the input parameter, and then click **Submit**.

    **Note:** Default settings are used for the trigger type, related resources, and the key of input parameter.

6.  If you have selected Yes for the Apply Rule to All Members parameter in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the created rule.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the **Basic Information**, **Trigger**, and **Compliance Result for Related Resources** of the rule.
    -   Click **Return to Rule List**. On the **Rules** page, you can view the rule, the status of which is **Active**.

## Create a rule by using Function Compute

You can create a function in Function Compute and use the function to create a rule. For more information, see [Create a custom rule](/intl.en-US/Resource Compliance Audit/Develop custom rules/Create a custom rule.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set **Method** to **Function Compute**. Enter a rule name, select a function ARN and risk level, specify whether to apply the rule to all member accounts, and then click **Next**.

    ![Create a rule by using Function Compute](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3708478851/p97246.png)

    You can select a function only after you have created one in the Function Compute console. To create a function in the Function Compute console, click **Create New Function**. For more information, see [Function operations](https://www.alibabacloud.com/help/doc-detail/52077.htm).

5.  In the **Parameter Settings** step, select a trigger type and related resources, specify the rule parameter, and then click **Submit**.

    -   After you select a resource type, the rule monitors all your resources of the specified type. Each rule can be applied to one or more resource types.
    -   You can click Add Rule Parameter to add an input parameter. You must specify the **Key** and **Value** for each input parameter. The key of the input parameter must be the same as the configuration item of the resource.
6.  If you have selected Yes for the Apply Rule to All Members parameter in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the created rule.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the **Basic Information**, **Trigger**, and **Compliance Result for Related Resources** of the rule.
    -   Click **Return to Rule List**. On the **Rules** page, you can view the rule, the status of which is **Active**.

## Create a rule by using Visual Editor

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set **Method** to **Visual Editor**. Enter the rule name, select a risk level, specify whether to apply the rule to all member accounts, and then click **Next**.

5.  In the **Parameter Settings** step, select the related resources, specify the rule parameter, and then click **Submit**.

6.  If you have selected Yes for the Apply Rule to All Members parameter in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the created rule.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the **Basic Information**, **Trigger**, and **Compliance Result for Related Resources** of the rule.
    -   Click **Return to Rule List**. On the **Rules** page, you can view the rule, the status of which is **Active**.

