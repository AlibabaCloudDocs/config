# Deliver resource change logs to a Log Service project

If you want to deliver resource change logs to a specified Logstore in Log Service, you must specify a project and Logstore. After the resource change logs are delivered to the specified Logstore, you can query and analyze the logs.

Log Service is activated. If you have not activated Log Service, you must log on to the [Log Service console](https://sls.console.aliyun.com) and activate the service as prompted. For more information, see [What is Log Service?](/intl.en-US/Product Introduction/What is Log Service?.md).

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to Log Service**.

3.  On the **Deliver Logs to Log Service** page, turn on **SLS Settings**.

4.  Set the required parameters to specify a project and a Logstore to store logs.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Project Region**|The region where the project resides.|
    |**Project Name**|The name of the project. The project name must be unique within an Alibaba Cloud account in a region.     -   If you select **Create a project in the account**, you must specify a project name.
    -   If you select **Select an existing project from the account**, you must select an existing project from the Project Name drop-down list. |
    |**Logstore Name**|The name of the Logstore. The Logstore name must be unique within an Alibaba Cloud account in a region.     -   If you select **Create a project in the account**, you must specify a Logstore name.
    -   If you select **Select an existing project from the account**, you must select an existing Logstore from the Logstore Name drop-down list. |

5.  Click **OK**.


## Use a management account

You can use a management account to specify a Logstore to store the resource change logs of the management account and the member accounts in the resource directory. The delivery destination can be a Logstore that belongs to the management account or a member account. Only management accounts are authorized to deliver resource change logs. No member accounts have the relevant permissions.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to Log Service**.

3.  On the **Deliver Logs to Log Service** page, turn on **SLS Settings**.

4.  Set the required parameters to specify a project and a Logstore to store logs.

    You can create a project within the current management account, or select an existing project that belongs to the management account or a member account. The specified project stores the resource change logs of the management account and its member accounts.

    -   To deliver resource change logs to a project that belongs to the management account, select **Create a project in the account** or **Select an existing project from the account**, and set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Project Region**|The region where the project resides.|
        |**Project Name**|The name of the project. The project name must be unique within an Alibaba Cloud account in a region.         -   If you select **Create a project in the account**, you must specify a project name.
        -   If you select **Select an existing project from the account**, you must select an existing project from the Project Name drop-down list. |
        |**Logstore Name**|The name of the Logstore. The Logstore name must be unique within an Alibaba Cloud account in a region.         -   If you select **Create a project in the account**, you must specify a Logstore name.
        -   If you select **Select an existing project from the account**, you must select an existing Logstore from the Logstore Name drop-down list. |

    -   To deliver resource change logs to a project that belongs to a member account, select **Select an existing project from other enterprise management accounts**, and set the required parameters. Before you set the parameters, make sure that the member account has an available project. The following table describes the parameters that are used to specify the Alibaba Cloud Resource Name \(ARN\) of the project within the member account and the ARN of the role to be assumed by the member account.

        |Parameter|Description|
        |---------|-----------|
        |**Logstore ARN**|The ARN of the project within the member account, such as `acs:log:ap-southeast-1:178589740730****:project/project1/logstore/logstore1`. The ARN must be in the format of `acs:log:{regionId}:{AccountID}:project/{projectName}/logstore/{logstoreName}`. The following list describes the fields:

        -   `{regionId}`: the ID of the region where the project resides, such as ap-southeast-1.
        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `{projectName}`: the name of the project, such as project1.
        -   `{logstoreName}`: the name of the Logstore, such as logstore1. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, such as `acs:ram::178589740730****:role/aliyunserviceroleforconfig`. The ARN must be in the format of `acs:ram::{AccountID}:role/aliyunserviceroleforconfig`. The following list describes the fields:

        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service-linked role of Cloud Config that authorizes Cloud Config to deliver resource change logs to the specified project. |

5.  Click **OK**.


After the resource change logs are delivered to the specified Logstore, you can query and analyze the resource change logs in the Logstore within a specified period. For more information, see [Query logs](/intl.en-US/Index and query/Query logs.md).

For information about the sample code that is used to deliver logs in the JSON format, see [Sample code used to deliver resource change logs to Log Service](/intl.en-US/Logs of resource configuration changes/Sample code used to deliver resource change logs to Log Service.md).

