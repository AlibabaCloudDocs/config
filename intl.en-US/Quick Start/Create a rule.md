# Create a rule

This topic describes how to create a rule. Cloud Config evaluates the compliance of resources based on rules. You can create a rule to evaluate your resources based on your business requirements.

Before you create a rule, you must familiarize yourself with the definition of rules and how rules work. For more information, see [Rule definition and implementation](/intl.en-US/Resource Compliance Audit/Rule definition and implementation.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, specify **Method**, set the relevant parameters, and then click **Next**.

    ![Basic Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

    -   If you select **Managed Rule**, you can select a managed rule that Cloud Config provides, and then select a risk level.
    -   If you select **Function Compute**, you must enter a rule name, select the Alibaba Cloud Resource Name \(ARN\) of a function, and then select a risk level.

        Before you can select a function, you must create a function in the Function Compute console. For more information, see [Function operations](https://www.alibabacloud.com/help/doc-detail/52077.htm).

    -   If you select **Visual Editor**, you must enter a rule name and select a risk level.
5.  In the **Parameter Settings** step, set relevant parameters and click **Next**.

    ![Parameter Settings step](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

    -   If you set the **Method** parameter to **Managed Rule** in the **Basic Settings** step, you can specify only the threshold values of the input parameters.
    -   If you set the **Method** parameter to **Function Compute** in the **Basic Settings** step, you can specify the trigger type, resource type, and input parameters of the rule.

        You must specify the key and value of each input parameter based on the logic of the custom function. The input parameters of the rule must be the same as the input parameters of the custom function and the configuration items of the resource.

    -   If you set the **Method** parameter to **Visual Editor** in the **Basic Settings** step, you can specify the resource type and compliance conditions.
6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

