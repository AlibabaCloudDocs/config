# Create a rule

This topic describes how to create a rule. A rule is a piece of logic judgment code that is stored in a rule function of Function Compute. You can create a rule based on a managed rule that is provided by Cloud Config. You can also create a rule by using Function Compute or Visual Editor. If you require other managed rules, you can submit a ticket to Alibaba Cloud. If the rules are appropriate, Alibaba Cloud will support them and implement rules with universal applicability as managed rules in Cloud Config.

Before you create a rule, you must familiarize yourself with the definition of rules and how rules work. For more information, see [Rule definition and implementation](/intl.en-US/Resource Compliance Audit/Rule definition and implementation.md).

## Create a rule by using a managed rule

You can create a rule based on an existing rule function in Function Compute. For more information, see [Managed rules](/intl.en-US/Resource Compliance Audit/Preset rules/Managed rules.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Managed Rule**, select a managed rule and risk level in the **Managed rule** and **Risk Level** sections, and then click **Next**.

    ![Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

5.  In the **Parameter Settings** step, specify the threshold values of the input parameters and click **Next**.

    ![Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

    **Note:** When you create a rule by using a managed rule, the default settings for the trigger type, related resources, and input parameters are used.

6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

## Create a rule by using Function Compute

You can create a rule function in Function Compute and use the rule function to create a rule. For more information, see [Create a custom rule by using Function Compute](/intl.en-US/Resource Compliance Audit/Develop custom rules/Create a custom rule by using Function Compute.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Function Compute**, enter a rule name in the **Rule Name** field, select a function from the **Function ARN** drop-down list, select a risk level in the **Risk Level** section, and then click **Next**.

    ![Function Compute: Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p92989.png)

    You can select a function only after you have created one in Function Compute. If you have not created a function in Function Compute, click **Create New Function** to create a function in the Function Compute console.For more information, see [Function operations](https://www.alibabacloud.com/help/doc-detail/52077.htm).

5.  In the **Parameter Settings** step, select the trigger type and related resources, specify the input parameters, and then click **Next**.

    ![Function Compute: Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p92993.png)

    -   After you select the resource types, Cloud Config monitors all your resources of the specified types based on the rule. Each rule can be applied to one or more resource types.
    -   You can click Add Rule Parameter to add an input parameter. You must enter the key and value for each input parameter in the **Key** and **Value** fields. The key of an input parameter must be the same as the configuration name of the resource.
6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

## Create a rule by using Visual Editor

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Visual Editor**, enter a rule name in the **Rule Name** field, select a risk level in the **Risk Level** section, and then click **Next**.

    ![Visual Editor: Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2280333061/p96932.png)

5.  In the **Parameter Settings** step, select the related resource, specify the input parameters, and then click **Next**.

    ![Visual Editor: Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2280333061/p111563.png)

    -   After you select a resource type, Cloud Config monitors all your resources of the specified type based on the rule. Each rule can be applied to one resource type.
    -   You must set the **Key**, **Relation**, and **Value** parameters for the input parameters.
6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

