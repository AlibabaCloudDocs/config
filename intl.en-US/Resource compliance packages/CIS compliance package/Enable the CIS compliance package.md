# Enable the CIS compliance package

Cloud Config supports the Center for Internet Security \(CIS\) compliance check feature. This feature allows the system to continuously check whether your Alibaba Cloud resources meet the requirements of the CIS Controls. Compliance to the CIS Controls allows you to reduce network security risks.

CIS stands for Center for Internet Security. For more information, visit [the CIS official website](https://www.cisecurity.org/).

The CIS Controls describe top 20 controls that enterprises must meet to implement basic network security. The following table describes the check items that are supported by the CIS compliance check feature.

|Item|Description|
|----|-----------|
|Account|Performs security checks on Alibaba Cloud accounts and RAM users from multiple aspects. These aspects include password settings and permission policies.|
|Network|Performs security checks on networks from multiple aspects. These aspects include the network ownership of instances, settings for security groups, open ports, and traffic monitoring.|
|Instances|Performs compliance checks on instances from multiple aspects. These aspects include the disk encryption, open ports, system updates, and endpoint protection.|
|OSS buckets|Performs security checks on buckets from multiple aspects. These aspects include the read/write settings for buckets, secure transmission, and content encryption.|
|Database|Performs security checks on databases from multiple aspects. These aspects include the connection types, data encryption, database audit.|

## Standard account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click **Enable Compliance Package** in the upper-right corner of the page.

4.  In the **Select a compliance package template.** dialog box, click **Use** in the **CISComplianceCheck** section.

5.  On the **CISComplianceCheck** page, set the required compliance scenario name, risk level, and rules.

    **Note:**

    -   Each compliance scenario name must be unique.
    -   By default, all the rules of the CIS compliance check feature are enabled. To disable a rule that you no longer require, turn off the related switch ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png). To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
6.  Click **Enable Compliance Package** in the upper-right corner of the page to enable the CIS compliance check feature.

    On the **Compliance Package** page, you can view the name, status, risk level, description of the compliance package. You can also edit, delete, or view the compliance package.


## Enterprise management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Compliance Package**.

3.  On the **Compliance Package** page, click the required account group tab.

4.  On the account group tab, click **Enable Compliance Package** in the upper-right corner of the tab.

5.  In the **Select a compliance package template.** dialog box, click **Use** in the **CISComplianceCheck** section.

6.  On the **CISComplianceCheck** page, set the required compliance scenario name, risk level, and rules.

    **Note:**

    -   Each compliance scenario name must be unique.
    -   By default, all the rules of the CIS compliance check feature are enabled. To disable a rule that you no longer require, turn off the related switch ![Switch](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252177.png). To set a rule, click the ![Arrow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5327607161/p252180.png) icon and set the required parameters.
7.  Click **Enable Compliance Package** in the upper-right corner of the tab to enable the CIS compliance check feature.

    On the account group tab, you can view the name, status, risk level, description of each compliance package that you enable. You can also edit, delete, or view the required compliance package.


