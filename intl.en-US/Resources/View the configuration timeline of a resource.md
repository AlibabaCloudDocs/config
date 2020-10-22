# View the configuration timeline of a resource

Cloud Config records each detailed configuration change of the resources that it monitors, and displays the configuration changes over time in a configuration timeline.

The configuration timeline of a resource includes the following elements:

-   Points on a configuration timeline
    -   Start point: If a resource is created before you activate Cloud Config, the start point of the configuration timeline is the time when you activate Cloud Config. If a resource is created after you activate Cloud Config, the start point of the configuration timeline is the time when the resource is created.
    -   Node: Cloud Config takes a configuration snapshot of a resource every 10 minutes. If the new snapshot is different from the one that was taken 10 minutes ago, Cloud Config generates a configuration change record. This record is displayed as a node on the configuration timeline.
    -   Breakpoint: If you remove a resource type from the monitoring scope of Cloud Config, Cloud Config stops monitoring this type of resources and does not update the configuration timeline of each resource of this type. Cloud Config monitors this type of resources again only after you add the resource type to the monitoring scope. Cloud Config does not record the changes of the resources before you add the resource type to the monitoring scope.
-   Content on a configuration timeline

    A configuration timeline is a set of configuration change records of a specific resource.

    -   A configuration timeline displays nodes by time in descending order. The first node displays the latest configuration change snapshot of a resource. The nodes below the first node display earlier configuration change snapshots of the resource.
    -   Each node displays the details of the current configuration change. The details include the comparison between the current and previous configurations and the events that trigger the current configuration change.
    **Note:** Cloud Config detects configuration changes at regular intervals of 10 minutes. If you change the configuration of a resource and then restore to the previous configuration within the same 10-minute interval, Cloud Config cannot identify the change or display the change on the configuration timeline.


1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the Resources page, set filters or enter a resource ID to search for the specified resource.

4.  Click the resource ID in the **Resource ID / Resource Name** column.

5.  On the page that appears, click the **Configuration Timeline** tab. Then, view the configuration timeline of the resource.


