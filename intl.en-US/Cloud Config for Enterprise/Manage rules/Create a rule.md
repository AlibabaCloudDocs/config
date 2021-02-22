# Create a rule

This topic describes how to create a rule. A rule is a piece of logic judgment code that is stored in a rule function of Function Compute. You can create a rule based on a managed rule that is provided by Cloud Config. You can also create a rule by using Function Compute or Visual Editor.

The master account is used to log on to the Cloud Config for Enterprise console.

Before you create a rule, you must familiarize yourself with the definition of rules and how rules work. For more information, see [Rule definition and implementation](/intl.en-US/Resource Compliance Audit/Rule definition and implementation.md).

## Create a rule by using a managed rule

For more information about the managed rules that Cloud Config provides, see [Managed rules](/intl.en-US/Resource Compliance Audit/Preset rules/Managed rules.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Managed Rule**. Select a managed rule and risk level, specify whether to apply the rule to all member accounts, and then click **Next**.

    ![Managed rule: Basic Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3708478851/p97236.png)

5.  In the **Parameter Settings** step, specify the value of the input parameter and click **Submit**.

    **Note:** When you create a rule by using a managed rule, the default settings for the trigger type, related resources, and input parameters are used.

6.  If you have set the Apply Rule to All Members parameter to Yes in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the information in the **Basic Information**, **Trigger**, and **Compliance Result of Related Resources** sections.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the created rule. The status of the rule is **Active**.

## Create a rule by using Function Compute

You can create a rule function in Function Compute and use the rule function to create a rule. For more information, see [Create a custom rule by using Function Compute](/intl.en-US/Resource Compliance Audit/Develop custom rules/Create a custom rule by using Function Compute.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Function Compute**. Enter a rule name, select a risk level, specify a function and whether to apply the rule to all member accounts, and then click **Next**.

    ![Function Compute: Basic Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3708478851/p97246.png)

    You can select a function only after you have created one in Function Compute. If you have not created a function in Function Compute, click **Create New Function** to create a function in the Function Compute console. For more information, see [Function operations](https://www.alibabacloud.com/help/doc-detail/52077.htm).

5.  In the **Parameter Settings** step, select the trigger type and related resources, specify the input parameters, and then click **Submit**.

    -   After you select the resource types, Cloud Config monitors all your resources of the specified types based on the rule. Each rule can be applied to one or more resource types.
    -   You can click Add Rule Parameter to add an input parameter. You must enter the key and value for each input parameter in the **Key** and **Value** fields. The key of an input parameter must be the same as the configuration name of the resource.
6.  If you have set the Apply Rule to All Members parameter to Yes in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the information in the **Basic Information**, **Trigger**, and **Compliance Result of Related Resources** sections.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the created rule. The status of the rule is **Active**.

## Create a rule by using Visual Editor

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Visual Editor**. Enter a rule name, select a risk level, specify whether to apply the rule to all member accounts, and then click **Next**.

5.  In the **Parameter Settings** step, select the related resource, specify the input parameters, and then click **Submit**.

6.  If you have set the Apply Rule to All Members parameter to Yes in the **Basic Settings** step, a message appears. In the message, click **OK**. Then, the rule is applied to all member accounts. You can specify the Apply Rule to All Members parameter only when you create a rule. The parameter cannot be modified after the rule is created.

    ![Confirmation message](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4708478851/p97243.png)

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. On the page that appears, you can view the information in the **Basic Information**, **Trigger**, and **Compliance Result of Related Resources** sections.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the created rule. The status of the rule is **Active**.

