# Create a rule by using Visual Editor

This topic describes how to create a rule by using Visual Editor. If the managed rules that Cloud Config provides do not meet your requirements, you can use Visual Editor to create a custom rule. Visual Editor can retrieve the parameters of resources. You can compose a rule logic by selecting input parameters, logical operators, and parameter values.

-   Cloud Config creates a rule function in Function Compute based on the logic that you compose.
-   The rule function is managed by Cloud Config. You are not charged for the rule function.
-   When a custom rule is triggered, Cloud Config evaluates the resources based on the rule function and displays the compliance evaluation result.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Visual Editor**, enter a rule name in the **Rule Name** field, select a risk level for the rule, and then click **Next**.

    ![Visual Editor: Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2280333061/p96932.png)

5.  **Parameter Settings** step, select the related resource, specify the input parameters, and then click **Next**.

    ![Visual Editor: Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2280333061/p111563.png)

    -   After you select a resource type, Cloud Config monitors all your resources of the specified type based on the rule. Each rule can be applied to one type of resources. For example, you can select the ACS::ActionTrail::Trail resource type.
    -   You can specify the input parameters as required. For example, you can set the **Key** parameter to **Tracking Status**, the **Relation** parameter to **Equals To**, and the **Value** parameter to **Enable** to check whether the tracking feature is enabled in ActionTrail.
    **Note:** Different resources have different parameters and parameter values. You can learn the specific meanings of parameters and possible parameter values based on the API of each service.

6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  View the rule creation result.

    In the **Complete** step, view the creation result.

    -   Click **View Details**. The details page of the rule appears. You can view the detailed information on the **Rule Details** and **Correction Details** tabs.
    -   Click **Return to Rule List**. The **Rules** page appears, where you can view the information of the rule. The rule is in the **Active** state.

