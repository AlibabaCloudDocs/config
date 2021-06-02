# View the resource list

After you authorize Cloud Config to access your resources, you can view the resources that reside in different regions within your account in the Cloud Config console. You can also search for a resource and view the details of the resource.

Cloud Config supports only some Alibaba Cloud services. Therefore, the resource list displays only part of your resources. Cloud Config will support more Alibaba Cloud services and display more resources in the resource list soon. For more information about the services and resource types that Cloud Config supports, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, view all resources that Cloud Config supports within your account.

    |Column|Description|
    |------|-----------|
    |**Resource ID / Resource Name**|The unique ID and name of the resource.|
    | |The tags that you bind to the resource for management. If you do not bind a tag to the resource, no tag is displayed in this column.|
    | |The type of the resource. A resource type is a category of resources, such as Elastic Compute Service \(ECS\) instance or Object Storage Service \(OSS\) bucket.|
    | |The region where the resource resides, such as China \(Hangzhou\).|
    | |The time when the resource was created.|
    | |The status of the resource. Valid values:    -   **Active**

If the resource is available, **Active** is displayed in the Resource Status column. By default, the resource list displays the resources that are in the **Active** state.

    -   **Deleted**

If the resource is deleted, **Deleted** is displayed in the Resource Status column. You can set filter conditions to filter the resources that are in the **Deleted** state. |
    | |The operations that you can perform on the resource in the Cloud Config console. For more information, see [Manage resources](/intl.en-US/Resources/Manage resources.md).|


## Use a management account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Resources**.

3.  On the **Resources** page, click the required account group tab.

4.  On the account group tab, view the resources of all member accounts in the account group.

    |Column|Description|
    |------|-----------|
    |**Resource ID / Resource Name**|The unique ID and name of the resource.|
    |**Owner**|The ID of the account to which the resource belongs.|
    | |The tags that you bind to the resource for management. If you do not bind a tag to the resource, no tag is displayed in this column.|
    | |The type of the resource. A resource type is a category of resources, such as ECS instance or OSS bucket.|
    | |The region where the resource resides, such as China \(Hangzhou\).|
    | |The time when the resource was created.|
    | |The status of the resource. Valid values:    -   **Active**

If the resource is available, **Active** is displayed in the Resource Status column. By default, the resource list displays the resources that are in the **Active** state.

    -   **Deleted**

If the resource is deleted, **Deleted** is displayed in the Resource Status column. You can set filter conditions to filter the resources that are in the **Deleted** state. |
    | |The operations that you can perform on the resource in the Cloud Config console. For more information, see [Manage resources](/intl.en-US/Resources/Manage resources.md).|


