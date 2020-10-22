# Check whether ApsaraDB for RDS instances can be accessed from the Internet

This topic describes how to create a rule to check whether ApsaraDB for RDS instances can be accessed from the Internet.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Basic Settings** step, set the **Method** parameter to **Managed Rule**, search for and select the **rds-public-access-check** rule, select a risk level for the rule, and then click **Next**.

5.  In the **Parameter Settings** step, use the default settings for the trigger type and related resources, and then click **Next**.

6.  In the **Remediation Settings** step, set the Remediation Method parameter to **Disable Remediation**, and then click **Submit**.

7.  Check the compliance evaluation results that are returned by the rule.

    In the **Complete** step, click **View Details** or **Return to Rule List** to view the compliance evaluation results that are returned by the rule.


