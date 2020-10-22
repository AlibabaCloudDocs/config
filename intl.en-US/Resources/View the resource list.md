# View the resource list

After you authorize Cloud Config to access your resources, you can view the resources that reside in different regions under your account in the Cloud Config console. You can also search for the specified resource and view the detailed configuration of the resource.

Cloud Config supports only specific Alibaba Cloud services. Therefore, the resource list may display only a part of your resources. Cloud Config will support more Alibaba Cloud services and display more resources in the resource list soon. For more information about the resource types that Cloud Config supports, see [Resource types supported by Cloud Config](/intl.en-US/Resource monitoring scope/Resource types supported by Cloud Config.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, view all resources that Cloud Config supports under your account.

    |Column|Description|
    |------|-----------|
    |**Resource ID / Resource Name**|The ID and name of the resource.|
    |**Tags**|The tags that you add to the resource for management. If you do not add any tags to the resource, the tag icon is not displayed in this column.|
    |**Resource Type**|The type of the resource. A resource type is a category of resources, such as Elastic Compute Service \(ECS\) instance or Object Storage Service \(OSS\) bucket.|
    |**Region**|The region where the resource resides, such as China \(Hangzhou\).|
    |**Created At**|The time when the resource was created.|
    |**Resource Status**|The status of the resource. Valid values:    -   **Retained**

The Retained state indicates that the resource is normally managed. By default, the resource list displays the resources that are in the **Retained** state.

    -   **Deleted**

The Deleted state indicates that the resource has been deleted. You can view the resources in the **Deleted** state by setting the related filter. |
    |**Actions**|The operations that you can perform on the resource in the Cloud Config console. For more information, see [Manage resources](/intl.en-US/Resources/Manage resources.md).|


