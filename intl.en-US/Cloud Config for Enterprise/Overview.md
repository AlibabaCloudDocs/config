# Overview

Cloud Config for Enterprise is an integration of Cloud Config and Resource Management. You can use Cloud Config for Enterprise to audit configuration compliance for resources that belong to different master accounts.

**Note:** For more information about Resource Management, see [What is Resource Management?]().

## Features

Cloud Config for Enterprise supports the following features and has specific limits:

-   After you use the master account to upgrade Cloud Config to Cloud Config for Enterprise, Cloud Config for Enterprise is activated for all member accounts, including new member accounts.
-   After you use the master account to configure rules that are used to audit configuration compliance for resources, you can apply the rules to all member accounts.
-   You can use the master account to view the list, configuration history, and configuration compliance status of resources that belong to member accounts.
-   After you use the master account to enable the snapshot feature, you can deliver the snapshots of resource configuration changes to a specified Object Storage Service \(OSS\) bucket.
-   After you use the master account to enable the log delivery feature, you can deliver the logs of resource configuration changes to a specified Log Service project.
-   After you use the master account to enable the event notification feature, you can send the event notifications of the resources to a specified topic in Message Service \(MNS\).
-   You cannot create, modify, or delete rules if you log on to Cloud Config for Enterprise with a member account. This facilitates centralized compliance control.

## Architecture

The following figure shows how Cloud Config for Enterprise works with resource directories. You can use resource directories to manage multiple master accounts of your enterprise and construct a directory tree that represents the logical relationships among the accounts. You can use Cloud Config for Enterprise to evaluate whether resource configurations are compliant with specific rules. You can use the master account to view the list, configuration history, and configuration compliance status of resources that belong to each member account.

![Architecture of Cloud Config for Enterprise](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7365346951/p95013.png)

## Terms

|Term|Description|
|----|-----------|
|master account|A master account is the account that is used to enable a resource directory and is the super administrator of the resource directory. The master account has all administrative permissions on the resource directory and the member accounts in the resource directory. Only an Alibaba Cloud account that has passed the enterprise real-name verification can be used as a master account. Each resource directory has only one master account.|
|member account|A member account is an Alibaba Cloud account. It serves as a container for resources and is also an organizational unit in a resource directory. A member account indicates a project or application. The resources under different member accounts are isolated.

A member account is an account that a master account invites to join a resource directory or creates in a resource directory. |
|rule|A rule is created by the master account and is used to audit configuration compliance. The rule is applied to all member accounts of the master account.|
|Cloud Config for individuals|If you do not need to manage resource configuration compliance across master accounts, you can use Cloud Config for individuals.|
|Cloud Config for Enterprise|If your enterprise has multiple master accounts, you can upgrade Cloud Config to Cloud Config for Enterprise to achieve centralized management. Cloud Config for Enterprise is an integration of Cloud Config and Resource Management. This allows you to manage resource configuration compliance across all member accounts by using only one master account. **Note:** Specific features such as protection screening will be unavailable after you upgrade Cloud Config to Cloud Config for Enterprise. These features will be integrated into Cloud Config for Enterprise in the future updates. |

## Upgrade to Cloud Config for Enterprise

Before you upgrade Cloud Config to Cloud Config for Enterprise, you must create a resource directory in the Resource Management console. Otherwise, the entry to upgrade the service is unavailable in the Cloud Config console. To upgrade Cloud Config, perform the following steps:

Log on to the Cloud Config console by using the master account. On the Overview page, click **Upgrade**. The upgrade takes a few minutes to complete. The required time varies based on the number of member accounts. Before an upgrade, make sure that you understand the following feature and action changes related to service upgrades or changes:

-   An upgrade will change the features that are available in the console to the master account and member accounts. For more information, see [Differences between Cloud Config for individuals and Cloud Config for Enterprise](/intl.en-US/.md).
-   The following table describes the actions that Cloud Config for Enterprise performs when member accounts in a resource directory change.

    |Change|Action that Cloud Config for Enterprise performs|
    |------|------------------------------------------------|
    |A member account is added.|After a member account is added to the resource directory, Cloud Config for Enterprise is automatically activated for the member account. The member account inherits the rules that the master account assigns to all member accounts. The snapshots of resource configuration changes of the member account are delivered to the OSS bucket that is specified by the master account.|
    |A member account is removed.|After a member account is removed, the rules that are assigned by the master account are removed from the member account. The snapshots, logs, and resource events are no longer delivered to the destination that is specified by the master account. You can use Cloud Config for individuals with the member account.|
    |A member account is transferred.|The directory trees on the **Rules** page and the **Resources** page of the master account are changed. The snapshots of rule evaluation and resource configurations are still delivered to the OSS bucket that is specified by the master account.|


## Limits

The following list describes the limits when you are using Cloud Config for Enterprise.

-   Cloud Config for Enterprise is in invitational preview. Therefore, you must [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.18.dbd44bd3e4f845#/ticket/createIndex) or contact the service manager for the permission to use Cloud Config for Enterprise.
-   Before you use Cloud Config for Enterprise, you must log on to the Resource Management console to create a resource directory on the **Resource Directory** page.
-   To create or apply rules, you must log on to the Cloud Config for Enterprise console by using the master account or as a RAM user with the administrator permissions. The rules are applied to all member accounts.
-   To specify or modify the delivery destination of snapshots, logs, and event notifications, you must log on to the Cloud Config for Enterprise console by using the master account or as a RAM user with the administrator permissions.
-   You cannot use a member account to perform write operations in the Cloud Config for Enterprise console.
-   You can create up to 200 rules by using a master account.
-   After you upgrade Cloud Config to Cloud Config for Enterprise, the original configurations of the master account and member accounts are deleted. All member accounts are managed by the master account.
-   You cannot downgrade Cloud Config for Enterprise to Cloud Config for individuals.

    **Note:** Both Cloud Config for individuals and Cloud Config for Enterprise are free.


