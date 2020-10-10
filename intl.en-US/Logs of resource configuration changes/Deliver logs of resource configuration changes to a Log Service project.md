# Deliver logs of resource configuration changes to a Log Service project

To deliver resource configuration changes as logs to Log Service, you must specify a Log Service project.

Log Service is activated. If you have not activated Log Service, you must log on to the [Log Service console](https://sls.console.aliyun.com) and activate the service.

For more information about Log Service, see [What is Log Service?](/intl.en-US/Product Introduction/What is Log Service?.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to SLS**.

3.  On the **Deliver Logs to SLS** page, turn on **SLS Settings**.

4.  Specify a Log Service project to store logs of resource configuration changes.

    The following table describes the parameters for specifying a Log Service project.

    |Parameter|Description|
    |---------|-----------|
    |**Project Region**|The region where the Log Service project resides.|
    |**Project Name**|The name of the project. The name must be unique to an Alibaba Cloud account in a region.    -   If you select **Create a project**, you must specify a project name.
    -   If you select **Select an existing project of your account**, you must select an existing project from the drop-down list.

For more information about how to create a project in Log Service, see [Quick start](/intl.en-US/Quick Start/Quick start.md). |
    |**Logstore Name**|The name of the Logstore. The name must be unique to an Alibaba Cloud account in a region.    -   If you select **Create a project**, you must specify a Logstore name.
    -   If you select **Select an existing project of your account**, you must select an existing Logstore from the drop-down list.

For more information about how to create a Logstore in Log Service, see [Quick start](/intl.en-US/Quick Start/Quick start.md). |

5.  Click **OK**.


