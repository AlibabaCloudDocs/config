# Overview

Cloud Config for Enterprise is an integration between Cloud Config and Resource Management. You can use Cloud Config for Enterprise to evaluate configuration compliance of resources that belong to different master accounts.

**Note:** For more information about Resource Management, see [What is Resource Management?]().

## Features

Cloud Config for Enterprise provides the following features:

-   After you use the master account to upgrade Cloud Config to Cloud Config for Enterprise, Cloud Config for Enterprise is activated for all member accounts, including newly created member accounts.
-   After you use the master account to configure rules to evaluate resource compliance, you can apply the rules to all member accounts.
-   The master account can be used to view the list, configuration history, and configuration compliance of resources that belong to all member accounts.
-   The master account can be used to specify an Object Storage Service \(OSS\) bucket to store resource change snapshots.
-   The master account can be used to specify a Log Service project to store resource change logs.
-   The master account can be used to specify a Message Service \(MNS\) topic to subscribe to resource events.
-   To facilitate compliance control in a centralized manner, a member account cannot be used to create, modify, or delete rules in Cloud Config for Enterprise.

## Architecture

The following figure shows how Cloud Config for Enterprise works with resource directories. You can use resource directories to manage multiple master accounts of your enterprise and construct a directory tree that represents the logical relationships among the accounts. You can use Cloud Config for Enterprise to evaluate whether resource configurations are compliant based on specified rules. You can use the master account to view the list, configuration history, and configuration compliance of resources that belong to all member accounts.

![Architecture of Cloud Config for Enterprise](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7365346951/p95013.png)

## Terms

|Term|Description|
|----|-----------|
|master account|A master account is the account that is used to enable a resource directory and is the super administrator of the resource directory. The master account has all administrative permissions on the resource directory and the member accounts in the resource directory. Only an Alibaba Cloud account that has passed enterprise real-name verification can be used as a master account. Each resource directory has only one master account. |
|member account|A member account serves as a container for resources and is also an organizational unit in a resource directory. A member account indicates a project or application. The resources of different member accounts are isolated.

A member account is an account that a master account adds to a resource directory or creates in a resource directory. |
|rule|A rule is created by the master account and is used to evaluate configuration compliance. The rule is applied to all member accounts of the master account.|
|Cloud Config for individuals|If you do not need to manage resource compliance across master accounts, you can use Cloud Config for individuals.|
|Cloud Config for Enterprise|If you have multiple master accounts, you can upgrade Cloud Config to Cloud Config for Enterprise to achieve centralized compliance management. Cloud Config for Enterprise is an integration between Cloud Config and Resource Management. This allows you to manage resource compliance across all member accounts by using only one master account. **Note:** Some features such as classified protection precheck become unavailable after you upgrade Cloud Config for individuals to Cloud Config for Enterprise. These features will be integrated into Cloud Config for Enterprise in future updates. |

## Upgrade to Cloud Config for Enterprise

Before you upgrade Cloud Config to Cloud Config for Enterprise, you must create a resource directory in the Resource Management console. Otherwise, you cannot be redirected to the upgrade page in the Cloud Config console. To upgrade Cloud Config, perform the following steps:

Log on to the Cloud Config console by using the master account. On the Overview page, click **Upgrade**. The upgrade takes a few minutes. The time you wait varies based on the number of member accounts. Before an upgrade, make sure that you understand the following feature and action changes related to service upgrades or changes:

-   An upgrade to Cloud Config for Enterprise changes the features that are available to the master account and member accounts in the console. For more information about the differences between Cloud Config for individuals and Cloud Config for Enterprise, see [Differences between Cloud Config for individuals and Cloud Config for Enterprise](/intl.en-US/.md).
-   The following table describes the actions that Cloud Config for Enterprise performs when member accounts are changed in a resource directory.

    |Change|Action performed by Cloud Config for Enterprise|
    |------|-----------------------------------------------|
    |A member account is added|After a member account is added to the resource directory, Cloud Config for Enterprise is automatically activated for the member account. The member account inherits the rules that the master account assigns to all member accounts. The resource change snapshots of the member account are delivered to the OSS bucket that is specified by using the master account.|
    |A member account is removed|After a member account is removed, the rules that are assigned by using the master account are removed from the member account. The snapshots, logs, and resource events are no longer delivered to the destination that is specified by using the master account. You can use Cloud Config for individuals with the member account.|
    |A member account is transferred|The directory trees on the **Rules** page and the **Resources** page of the master account are changed. The evaluation results based on rules are not affected. The resource change snapshots are still delivered to the OSS bucket that is specified by using the master account.|


## Limits

The following list describes the limits when you use Cloud Config for Enterprise.

-   Cloud Config for Enterprise is in invitational preview. You must [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.18.dbd44bd3e4f845#/ticket/createIndex) or ask your service manager to add you to the whitelist for the invitational preview.
-   Before you use Cloud Config for Enterprise, you must log on to the Resource Management console to create a resource directory on the **Resource Directory** page.
-   To create or apply rules, you must log on to the Cloud Config for Enterprise console. You can log on to the console by using the master account, or as a RAM user who is granted the administrator permissions. The rules are applied to all member accounts.
-   To specify or modify the delivery destination of snapshots, logs, and resource events, you must log on to the Cloud Config for Enterprise console. You can log on to the console by using the master account, or as a RAM user who is granted the administrator permissions.
-   You cannot use a member account to perform write operations in the Cloud Config for Enterprise console.
-   You can create a maximum of 200 rules for each master account.
-   After you upgrade Cloud Config for individuals to Cloud Config for Enterprise, the original configurations of the master account and member accounts are deleted. All member accounts are managed by the master account.
-   You cannot downgrade Cloud Config for Enterprise to Cloud Config for individuals.

    **Note:** Both Cloud Config for individuals and Cloud Config for Enterprise are provided free of charge.


