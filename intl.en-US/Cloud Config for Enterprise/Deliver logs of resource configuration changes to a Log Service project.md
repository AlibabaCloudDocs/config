# Deliver logs of resource configuration changes to a Log Service project

You can use a master account to specify a Log Service project to store logs of resource configuration changes of the master account and the member accounts in the resource directory. You cannot use a member account to specify a project. The logs of the resource configuration changes of a member account are delivered to the project that is specified by the master account.

-   The master account is used to log on to the Cloud Config for Enterprise console.
-   Log Service is activated.

    If you have not activated Log Service, log on to the [Log Service console](https://sls.console.aliyun.com) and activate the service as required.


For more information about Log Service, see [What is Log Service?](/intl.en-US/Product Introduction/What is Log Service?.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to SLS**.

3.  On the **Deliver Logs to SLS** page, turn on **SLS Settings**.

4.  Specify a Log Service project to store logs of resource configuration changes.

    You can create a project or select an existing project to store the logs of resource configuration changes in the master account and member accounts. You can specify a project that belongs to the master account or a member account.

    -   To specify a project that belongs to the master account, select **Create a project** or **Select an existing project of your account**, and set the parameters as described in the following table.

        |Parameter|Description|
        |---------|-----------|
        |**Project Region**|The region where the Log Service project resides.|
        |**Project Name**|The name of the project. The name must be unique to an Alibaba Cloud account in a region.        -   If you select **Create a project**, you must specify a project name.
        -   If you select **Select an existing project of your account**, you must select an existing project from the Project Name drop-down list.

For more information about how to create a project in Log Service, see [Quick start](/intl.en-US/Quick Start/Quick start.md). |
        |**Logstore Name**|The name of the Logstore. The name must be unique to an Alibaba Cloud account in a region.        -   If you select **Create a project**, you must specify a Logstore name.
        -   If you select **Select an existing project of your account**, you must select an existing Logstore from the Logstore Name drop-down list.

For more information about how to create a Logstore in Log Service, see [Quick start](/intl.en-US/Quick Start/Quick start.md). |

    -   To specify a project that belongs to a member account, select **Select an existing project of another account \(enterprise account only\)** and set the parameters as described in the following table. Make sure that the member account has an available Log Service project.

        |Parameter|Description|
        |---------|-----------|
        |**Logstore ARN**|The Alibaba Cloud Resource Name \(ARN\) of the specified project in the member account.The ARN must be in the format of `acs:log:{regionId}:{Aliuid}:project/{projectName}/logstore/{logstoreName} format`. The following content describes the fields in the format:

        -   `{regionId}`: the region where the Log Service project resides, such as cn-shanghai.
        -   `{Aliuid}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `{projectName}`: the name of the project, such as project1.
        -   `{logstoreName}`: the name of the Logstore, such as logstore1.
An example of a project ARN is acs:log:cn-shanghai:178589740730\*\*\*\*:project/project1/logstore/logstore1. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account.The ARN of the role must be in the format of `acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`. The following content describes the fields in the format:

        -   `{Aliuid}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service linked role of Cloud Config that authorizes Cloud Config to deliver logs of resource configuration changes to the specified project.
An example of a role ARN is acs:ram::178589740730\*\*\*\*:role/aliyunserviceroleforconfig. |

5.  Click **OK**.


