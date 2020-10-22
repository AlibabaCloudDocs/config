# View the compliance timeline of a resource

In Cloud Config, each resource has its own compliance timeline. A compliance evaluation record is generated for a resource each time when the resource is evaluated by a rule. Multiple compliance evaluation records form a compliance timeline of the resource.

The compliance timeline of a resource includes the following elements:

-   Points on a compliance timeline
    -   Start point: the time when a resource is evaluated by a rule for the first time. You can configure Cloud Config to run a rule to periodically evaluate a resource at the specified time or each time when you change the resource configuration. You can also manually run a rule to evaluate a resource.
    -   Node: A node is generated on the compliance timeline of a resource each time the resource is evaluated. One or more rules may be used to evaluate a resource at a time.
    -   Breakpoint: Unlike a configuration timeline, a compliance timeline does not have any breakpoints because a resource is evaluated by a rule based on real-time configuration changes and this evaluation is discontinuous.
-   Content on a compliance timeline

    A compliance timeline is a collection of historical compliance evaluation records of a specific resource.

    -   Time: the time when a compliance evaluation is performed.
    -   Trigger type: the reason that triggers the compliance evaluation on a resource. A compliance evaluation can be manually or periodically triggered, and can also be triggered based on real-time configuration changes.
    -   Compliance evaluation results: On the left side of the Compliance Timeline tab, the evaluation result for each node can be marked as **Compliant** or **Non-compliant**. This helps you find the node that you focus on.
    -   Evaluation details of each node: include the basic information of the resource and the current evaluation result. If the evaluation is triggered by real-time configuration changes, the change details are also displayed for you to find the non-compliant configuration item.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the Resources page, set filters or enter a resource ID to search for the specified resource.

4.  Click the resource ID in the **Resource ID / Resource Name** column.

5.  On the page that appears, click the **Compliance Timeline** tab and view the compliance timeline details of the resource.


