# Deliver resource change logs to a Log Service project

You can use a master account to deliver resource change logs of the master account and its member accounts in your resource directory to a Logstore. The Logstore must belong to the master account or a member account. Only master accounts are authorized to deliver resource change logs. No member accounts have the relevant permissions.

-   A master account is used to log on to the Cloud Config console.
-   Log Service is activated.

    If you have not activated Log Service, log on to the [Log Service console](https://sls.console.aliyun.com) and activate the service as prompted.


-   For more information about Log Service, see [What is Log Service?](/intl.en-US/Product Introduction/What is Log Service?.md).
-   For information about the code samples that are used to deliver logs, see [Sample code used to deliver resource change logs to Log Service]().

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to SLS**.

3.  On the **Deliver Logs to SLS** page, turn on the **SLS Settings** switch.

4.  Specify a project and a Logstore to store logs.

    You can create a project within the current master account, or select an existing project that belongs to the master account or a member account. The specified project stores the resource change logs of the master account and its member accounts.

    -   To deliver resource change logs to a project that belongs to the master account, select **Create a project** or **Select an existing project of your account**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Project Region**|The region where the project resides.|
        |**Project Name**|The name of the project. The project name must be unique within an Alibaba Cloud account in a region.        -   If you select **Create a project**, you must specify a project name.
        -   If you select **Select an existing project of your account**, you must select an existing project from the Project Name drop-down list. |
        |**Logstore Name**|The name of the Logstore. The Logstore name must be unique within an Alibaba Cloud account in a region.        -   If you select **Create a project**, you must specify a Logstore name.
        -   If you select **Select an existing project of your account**, you must select an existing Logstore from the Logstore Name drop-down list. |

    -   To deliver resource change logs to a project that belongs to a member account, select **Select an existing project of another account \(enterprise account only\)**, and then set the required parameters. Before you set the parameters, make sure that the member account has available projects. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Logstore ARN**|The Alibaba Cloud Resource Name \(ARN\) of the specified project in the member account, for example, `acs:log:ap-southeast-1:178589740730****:project/project1/logstore/logstore1`.Before you set this parameter, make sure that you have obtained the ID of the member account, the region where the project resides, the name of the project, and the name of the Logstore.

The ARN must be in the format of `acs:log:{regionId}:{Aliuid}:project/{projectName}/logstore/{logstoreName}`, where:

        -   `{regionId}`: the ID of the region where the project resides, for example, ap-southeast-1.
        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `{projectName}`: the name of the project, for example, project1.
        -   `{logstoreName}`: the name of the Logstore, for example, logstore1. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, for example, `acs:ram::178589740730****:role/aliyunserviceroleforconfig`.Before you set this parameter, make sure that you have obtained the ID of the member account. Then, set the parameter based on the ARN format.

The ARN must be in the format of `acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`, where:

        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service-linked role of Cloud Config that authorizes Cloud Config to deliver resource change logs to the specified project. |

5.  Click **OK**.


After the resource change logs are delivered to the specified Logstore, you can query and analyze the resource change logs in the Logstore within a specified period. For more information, see [Query logs](/intl.en-US/Index and query/Query logs.md).

