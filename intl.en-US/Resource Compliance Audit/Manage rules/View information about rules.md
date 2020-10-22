# View information about rules

This topic describes the information about rules on the Rules page in the Cloud Config console. You can view the status of each rule and the statistics on the compliance evaluation results that are returned by each rule on the page.

When you open the **Rules** page for the first time, no rule is displayed on the page. After you create a rule, you can view the rule on the page. You can also view the basic information about the rule. We recommend that you pay close attention to the information in the **Compliance** and **Status** columns.

## Compliance column

The Compliance column indicates the compliance status of a specified rule, that is, the statistics on the compliance evaluation results that are returned by the rule. The following table describes the compliance statuses.

|Compliance status|Description|
|-----------------|-----------|
|Compliant \(N\)|All resources that are evaluated based on the rule are considered compliant in historical evaluations. N indicates the number of compliant resources.|
|Non-compliant \(N\)|Specific resources that are evaluated based on the rule are considered non-compliant in historical evaluations. N indicates the number of non-compliant resources. You can view the non-compliant resources on the Rule Details tab of the details page of the rule.|
|Insufficient Data|No resources are evaluated based on the rule.|

## Status column

The Status column indicates the status of a specific rule. The following table describes the statuses.

|Status|Description|
|------|-----------|
|Active|Cloud Config is monitoring the related resources based on the rule. The rule will be triggered once the resource configuration changes.|
|Evaluating|The rule is triggered and is evaluating whether configurations of the related resources are compliant.|
|Deleting Results|Cloud Config is deleting the compliance evaluation results that are returned by the rule. You can use Cloud Config to delete the compliance evaluation results that are returned by a specified rule. This allows you to clear test data before you start to evaluate the configuration compliance of resources.|
|Inactive|The rule is disabled. Cloud Config retains the configuration of the rule. However, the rule cannot be triggered.|
|Deleting|Cloud Config is deleting the rule.|

