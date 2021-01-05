# Rule list

This topic describes the rule list on the Rules page in the Cloud Config console. You can view the status of each rule and the compliance evaluation results returned for each rule on the Rules page.

The first time you open the **Rules** page, no rules are displayed on the page. After you create a rule, you can view the rule on the page. You can also view the basic information of the rule on the page. We recommend that you take note of the information in the **Status** and **Compliance** columns.

## Status column

The Status column indicates the status of each rule in the rule list. The following table describes the statuses.

|Status|Description|
|------|-----------|
|Active|Cloud Config is monitoring the related resources based on the rule. The rule is triggered when the resource configuration changes.|
|Evaluating|The rule is triggered and the compliance of the related resources is being evaluated.|
|Deleting Results|Cloud Config is deleting the compliance evaluation results that are returned based on the rule. This allows you to clear test data before you start to evaluate the configuration compliance of your resources.|
|Inactive|The rule is disabled. Cloud Config retains the configurations of the rule. However, the rule cannot be triggered.|
|Deleting|Cloud Config is deleting the rule.|

## Compliance column

The Compliance column indicates the compliance status of each rule. This column displays the statistics of the compliance evaluation results that are returned based on the rule. The following table describes the compliance statuses.

|Compliance status|Description|
|-----------------|-----------|
|Compliant \(N\)|N resources are evaluated to be compliant based on the rule. N indicates the number of compliant resources.|
|Non-compliant \(N\)|N resources are evaluated to be non-compliant based on the rule. N indicates the number of non-compliant resources. To view a non-compliant resource, find the rule in the rule list, and then click **Details** in the **Actions** column.|
|Insufficient Data|No resources are evaluated based on the rule.|

