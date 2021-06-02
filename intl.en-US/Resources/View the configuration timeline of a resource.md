# View the configuration timeline of a resource

Cloud Config records each detailed configuration change of the resources that it monitors, and displays the configuration changes over time in a configuration timeline. After you activate Cloud Config, Cloud Config starts recording your resource configuration changes and keeps the data for 10 years by default.

The configuration timeline of a resource indicates the configuration change history of the resource. The following table describes the elements included in the configuration timeline.

|Element|Description|
|-------|-----------|
|Points on a configuration timeline|-   Start point: If a resource is created before you activate Cloud Config, the start point of the configuration timeline is the time when you activate Cloud Config. If a resource is created after you activate Cloud Config, the start point of the configuration timeline is the time when the resource is created.
-   Node: Cloud Config takes a configuration snapshot of a resource every 10 minutes. If the new snapshot is different from the one that was taken 10 minutes ago, Cloud Config generates a configuration change record. This record is displayed as a node on the configuration timeline.
-   Breakpoint: If you remove a resource type from the monitoring scope of Cloud Config, Cloud Config stops monitoring this type of resources and does not update the configuration timeline of each resource of this type. |
|Content on a configuration timeline|-   A configuration timeline displays nodes by time in descending order. The first node displays the latest configuration change snapshot of the current resource. The nodes below the first node display earlier configuration change snapshots of the resource.
-   Each node displays the basic information about the resource, the details of the current configuration change, and the ActionTrail events that correspond to the current configuration change. |

**Note:** Cloud Config detects configuration changes at regular intervals of 10 minutes. If you change the configuration of a resource and then restore the resource to the previous configuration within the same 10-minute interval, Cloud Config cannot identify the change or display the change on the configuration timeline.

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, set filter conditions or enter a resource ID to search for the resource whose configuration timeline you want to view.

4.  Click the resource ID in the **Resource ID / Resource Name** column.

5.  Click the tab to view the configuration timeline of the resource.

    -   In the section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Configuration Changes** section, you can view the relevant resource configurations before and after the current configuration change in JSON format.
    -   In the **ActionTrail** section, you can view the ActionTrail events that correspond to the current configuration change.

## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, click the required account group tab.

4.  On the account group tab, set filter conditions or enter a resource ID to search for the resource whose configuration timeline you want to view.

5.  Find the resource for which you want to view the details and click the resource ID in the **Resource ID / Resource Name** column. On the Details tab, view the resource details.

6.  Click the tab to view the configuration timeline of the resource.

    -   In the section, you can view the ID, name, type, and tags of the resource, the time when the resource was created, and the region and zone where the resource resides.
    -   In the **Configuration Changes** section, you can view the relevant resource configurations before and after the current configuration change in JSON format.
    -   In the **ActionTrail** section, you can view the ActionTrail events that correspond to the current configuration change.

