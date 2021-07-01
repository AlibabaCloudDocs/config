# Overview

You can specify a remediation template for a rule when you create or edit the rule. A remediation template is a workflow in Logic Composer. If the configuration of a resource is non-compliant, the template can be automatically or manually triggered to modify the configuration.

You must grant Logic Composer and Operation Orchestration Service \(OOS\) the required permissions to modify the configurations of your resources based on the remediation template. For more information about Logic Composer, see [What is Logic Composer?](). For more information about OOS, see [Introduction to OOS](https://www.alibabacloud.com/help/doc-detail/120556.htm).

When you create or edit a rule, you can configure or skip the remediation settings. Automatic and manual execution of remediation templates have the following differences:

-   Automatic execution: If the resources to which the rule is applied are evaluated as non-compliant, the configurations of the resources are automatically remediated.
-   Manual execution: If the resources to which the rule is applied are evaluated as non-compliant, the configurations of the resources are not automatically remediated. You can manually run the template to remediate the resource configurations on the Correction Details tab of the rule.

## Limits

-   You can specify remediation templates only for specific managed rules. Cloud Config is planning to support remediation settings for more managed rules.
-   You can specify only one remediation template for a rule. Default templates are applicable only to managed rules.

## Related features

The following table describes the features that are related to remediation settings.

|Feature|Description|
|-------|-----------|
|[Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md)|When you create a rule, you can specify a remediation template for the rule and configure automatic execution for the template. If the configuration of a resource is non-compliant, the template automatically runs to correct the configuration.|
|[Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md)|When you create a rule, you can specify a remediation template for the rule and configure manual execution for the template. If the configuration of a resource is non-compliant, you can manually run the template to remediate the configuration.|
|[Delete remediation settings](/intl.en-US/Resource Compliance Audit/Remediation settings/Delete remediation settings.md)|Cloud Config allows you to delete remediation settings and revoke permissions.|

