# Check whether specified tags are attached to a resource

This topic describes how to create a rule to check whether specified tags are attached to a resource under your Alibaba Cloud account. You can configure the rule for the following Alibaba Cloud services: ApsaraDB for RDS, Elastic Compute Service \(ECS\), Server Load Balancer \(SLB\), Object Storage Service \(OSS\), ApsaraDB for Redis, PolarDB, and ApsaraDB for MongoDB.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Rules**.

3.  On the **Rules** page, click **Create Rule**.

4.  In the **Rules** step, set the **Method** parameter to **Managed Rule**, search for and select the **required-tags** rule, select a risk level for the rule, and then click **Next**.

    ![Basic Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86601.png)

5.  In the **Parameter Settings** step, enter the key and value of the tag, and then click **Next**.

    ![Parameter Settings step](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9741333061/p86602.png)

    If you need to check multiple tags, you can set multiple key-value pairs one by one. You can set up to six key-value pairs. The rule evaluates resources to which the rule is applied as **Compliant** only when all specified tags are attached to the resources. If you need to check whether a tag in a tag group is attached to a resource type, you must create a rule for each tag.

    Assume that the tag "Project=A" must be attached to all your resources. You can use the **required-tags** rule to monitor all your resources. If Cloud Config detects that the tag is not attached to one or more of your resources, the rule evaluates the resources as **Non-compliant**.

    **Note:** When you create a rule by using a managed rule, the default settings for the trigger type, related resources, and input parameters are used.

6.  In the **Remediation Settings** step, set the **Remediation Method** parameter to **Disable Remediation** and click **Submit**.

    You can associate a remediation template with the rule. For more information, see [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md) and [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md).

7.  In the **Complete** step, click **View Details** or **Return to Rule List** to view the compliance evaluation results returned by the rule.


