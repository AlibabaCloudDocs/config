# Overview

This topic describes the definition, scenarios, and limits of account groups, and the impacts of member account changes on Cloud Config. The member account can belong to a resource directory or an account group.

## Definition

An account group is a collection of member accounts. In a resource directory, the management account can add all or some member accounts to an account group for centralized compliance management. An account group is also a resource pool formed by gathering resources from multiple member accounts.

The management account can view the resource lists, resource details, resource configuration timelines, resource compliance timelines, and associated resources of all member accounts in the account group. It can also create rules and compliance packages in the account group. These rules and compliance packages take effect on resources of all member accounts in the account group for continuous compliance evaluation.

## Scenarios

A management account can add all or some member accounts in a resource directory to an account group. An account group can be used to manage resource compliance across Alibaba Cloud accounts. It allows enterprises to manage compliance and collect data for multiple services and Alibaba Cloud accounts in a comprehensive manner.

Account groups can be used in the following scenarios:

-   You can view the global resources of all member accounts in an account group. A management account can view the resources of all member accounts in an account group, or filter or search for resources in a resource list. A management account can also view the details and configuration timeline of resources.
-   You can set a compliance baseline for all member accounts in an account group. A management account can create rules and compliance packages in an account group. These rules and compliance packages take effect on the resources of all member accounts in the account group. Member accounts cannot modify or delete the rules and compliance packages. This way, a management account can forcibly set a unified compliance baseline for multiple member accounts.
-   You can view the compliance check results of all member accounts. A management account can view the compliance check results of a rule on the resources of each member account. A management account can also view the compliance check results of a rule on all the resources of multiple member accounts. This facilitates centralized compliance management for multiple services and accounts.
-   You can collect the resource data of all member accounts. After an account group is created, the management account takes over some Cloud Config permissions of member accounts. The management account can configure a unified data delivery method for all the member accounts in the account group. Then, the resource configuration history of all member accounts is delivered to the management account or a member account that is used to store enterprise configuration data.
-   You can send the resource events of all accounts. A management account can send the resource change events and resource non-compliance events of all member accounts to a Message Service \(MNS\) topic.

**Note:** If you are using Cloud Config for Enterprise, a new account group that contains all the member accounts of a resource directory is created by default in an account group. Existing rules are still valid.

## Limits

Account groups have the following limits:

-   Only a management account in a resource directory can create an account group. The management account can add all or some member accounts of a resource directory to the account group.
-   Each management account can create a maximum of five account groups. Each account group can contain a maximum of 200 member accounts.

## Impacts of member account changes in a resource directory on Cloud Config

The following table lists the impacts of member account changes in a resource directory on Cloud Config.

|Item|Impact|
|----|------|
|Add a member account to a resource directory|-   The global account group of Cloud Config is affected. The member account added to the resource directory is automatically added to the global account group.
-   The custom account groups of Cloud Config are not affected. The member account added to the resource directory is not automatically added to custom account groups. You need to manually add the member account by using the management account. |
|Change the resource directory to which a member account belongs|Cloud Config is not affected. Cloud Config does not perform operations.|
|Remove a member account from a resource directory|Cloud Config is affected. If you remove a member account from a resource directory, the management account loses the management permissions on the member account. Then, the member account is automatically removed from all account groups.|

## Impacts of member account changes in an account group on Cloud Config

The following table lists the impacts of member account changes in an account group on Cloud Config.

|Item|Impact|
|----|------|
|Add a member account to no account group|The member account uses Cloud Config as an independent Alibaba Cloud account.|
|Add a member account to an account group|-   If a service-linked role for Cloud Config has not been created for the member account, the role is automatically created.
-   The existing rules and compliance packages of the member account are retained.
-   The delivery methods of resource data and notification methods of resource events configured for the member account are automatically cleared. The configuration permissions for the member account are removed. The member account must follow the configurations of the management account.
-   On the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages, the member account can view the **Current Account** tab and the tab of the account group. The member account can view its own resources, and rules and compliance packages created by the management account in the account group. The member account cannot modify rules and compliance packages. When the member account views the details of rules and compliance packages, only its own resources are displayed.
-   The existing rules and compliance packages in the account group automatically take effect on the member account. |
|Remove a member account from an account group|-   On the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages, the member account can no longer view the **Current Account** tab and the tab of the account group.
-   The existing rules and compliance packages of the account group no longer take effect on the member account.
-   The service-linked role for Cloud Config of the member account is retained.
-   The rules and compliance packages created by the member account are retained.
-   The delivery methods of resource data and notification methods of resource events configured for the member account are automatically cleared. The member account regains the permissions to re-configure the delivery methods of resource data and notification methods of resource events.
-   The member account uses Cloud Config as an independent Alibaba Cloud account and is no longer managed by the management account. |

