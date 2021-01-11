# Check whether trails in ActionTrail are enabled

You can create a rule to check whether trails in ActionTrail are enabled.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, select **Managed Rule** in the **Method** section, find and select the **actiontrail-enabled** rule, select a risk level for the rule, and then click **Next**.

    **Note:** To meet the compliance requirements, we recommend that you activate ActionTrail. This can be used to monitor the operations of your account on resources. It can also be used to record the operations logs as events in real time. You can use the actiontrail-enabled rule to check whether ActionTrail is activated for your account.

5.  In the **Parameter Settings** step, use the default settings for the trigger type and related resources, and then click **Next**.

6.  In the **Remediation Settings** step, select **Disable Remediation** in the Remediation Method section, and then click **Submit**.

7.  In the **Complete** step, click **View Details** or **Return to Rule List** to view the compliance evaluation results that are returned based on the rule.


