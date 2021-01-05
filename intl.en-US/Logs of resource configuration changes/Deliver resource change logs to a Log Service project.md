# Deliver resource change logs to a Log Service project

If you want to deliver resource change logs to a specified Logstore in Log Service, you must specify a project and Logstore. After the resource change logs are delivered to the specified Logstore, you can query and analyze the logs.

Log Service is activated. If you have not activated Log Service, you must log on to the [Log Service console](https://sls.console.aliyun.com) and activate the service as prompted.

-   For more information about Log Service, see [What is Log Service?](/intl.en-US/Product Introduction/What is Log Service?.md).
-   For information about the code samples that are used to deliver logs, see [Sample code used to deliver resource change logs to Log Service]().

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to SLS**.

3.  On the **Deliver Logs to SLS** page, turn on the **SLS Settings** switch.

4.  Set the required parameters to specify a project and a Logstore to store logs.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Project Region**|The region where the project resides.|
    |**Project Name**|The name of the project. The project name must be unique within an Alibaba Cloud account in a region.    -   If you select **Create a project**, you must specify a project name.
    -   If you select **Select an existing project of your account**, you must select an existing project from the Project Name drop-down list. |
    |**Logstore Name**|The name of the Logstore. The name must be unique within an Alibaba Cloud account in a region.    -   If you select **Create a project**, you must specify a Logstore name.
    -   If you select **Select an existing project of your account**, you must select an existing Logstore from the Logstore Name drop-down list. |

5.  Click **OK**.


After the resource change logs are delivered to the specified Logstore, you can query and analyze the resource change logs in the Logstore within a specified period. For more information, see [Query logs](/intl.en-US/Index and query/Query logs.md).

