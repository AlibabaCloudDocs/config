# Check whether specified tags are attached to your resources

You can create a rule to check whether your resources have specified tags.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Rules** step, select **Managed Rule** in the **Method** section, find and select the **required-tags** rule, select a risk level for the rule, and then click **Next**.

5.  In the **Parameter Settings** step, enter the key and value of a tag, and then click **Next**.

    If you want to check multiple tags, you can set multiple key-value pairs in sequence. You can set up to six key-value pairs. If all specified resources have specified tags, these resources are evaluated to be compliant based on the rule. If you want to check whether a specified tag is attached to specified resources, you must create a rule for each tag by selecting the required-tags rule.

    In this example, assume that the tag "Project=A" must be attached to all of your resources. You can use the **required-tags** rule to monitor all of your resources. If Cloud Config detects that the tag is not attached to one or more of your resources, these resources are evaluated to be non-compliant.

    **Note:** Default settings are used for the trigger type, related resources, and input parameters.

6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  In the **Complete** step, click **View Details** or **Return to Rule List** to view the compliance evaluation results that are returned based on the rule.


