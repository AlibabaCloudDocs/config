# View the compliance timeline of a resource

In Cloud Config, each resource has its own compliance timeline. Cloud Config generates a compliance evaluation record for a resource each time the resource is evaluated by a rule, and displays the compliance evaluation records over time in a compliance timeline.

The compliance timeline of a resource indicates the compliance evaluation history of the resource. The following table describes the elements included in the compliance timeline.

|Element|Description|
|-------|-----------|
|Points on a compliance timeline|-   Start point: the time when a resource is evaluated by a rule for the first time. You can configure Cloud Config to run a rule to periodically evaluate a resource at the specified time or each time you change the resource configuration. You can also manually run a rule to evaluate a resource.
-   Node: A node is generated on the compliance timeline of a resource each time the resource is evaluated. One or more rules may be used to evaluate a resource at a time.
-   Breakpoint: Unlike a configuration timeline, a compliance timeline does not have breakpoints. You can configure Cloud Config to run a rule to periodically evaluate a resource at the specified time or each time you change the resource configuration. You can also manually run a rule to evaluate a resource. If you remove a resource type from the monitoring scope of Cloud Config, Cloud Config stops monitoring this type of resources and does not update the compliance timeline of each resource of this type. Cloud Config monitors this type of resources again only after you add the resource type to the monitoring scope. Cloud Config does not record the changes of the resources before you add the resource type to the monitoring scope. |
|Content on a compliance timeline|-   Time: the time when a compliance evaluation is performed.
-   Trigger type: the reason that triggers the compliance evaluation on a resource. A compliance evaluation can be manually or periodically triggered, and can also be triggered based on real-time configuration changes.
-   Compliance evaluation results: On the left side of the **Compliance Timeline** tab, the evaluation result for each node can be marked as Compliant or Non-compliant. This helps you find non-compliant resources.
-   Evaluation details of each node: You can view the basic information about the resource and the current evaluation result. If the evaluation is periodically triggered, or triggered based on real-time configuration changes, the change details are also displayed for you to find non-compliant configuration items. |

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, set filter conditions or enter a resource ID to search for the resource for which you want to view the compliance timeline.

4.  Click the resource ID in the **Resource ID / Resource Name** column.

5.  Click the tab to view the compliance timeline of the resource.

    -   In the section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Evaluation Result** section, you can view the latest compliance evaluation result of the resource.
    -   In the **Configuration Changes** section, you can view the relevant resource configurations before and after the current configuration change in the JSON format.

## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, click the required account group tab.

4.  On the account group tab, set filter conditions or enter a resource ID to search for the resource for which you want to view the compliance timeline.

5.  Click the resource ID in the **Resource ID / Resource Name** column.

6.  Click the tab to view the compliance timeline of the resource.

    -   In the section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Evaluation Result** section, you can view the latest compliance evaluation result of the resource.
    -   In the **Configuration Changes** section, you can view the relevant resource configurations before and after the current configuration change in the JSON format.

