# Terms

This topic introduces the basic terms involved in Cloud Config.

|Term|Description|
|----|-----------|
|resource type|A resource type is a category of resources. For example, the resource type of Elastic Compute Service \(ECS\) instances is Instance. Resources can be divided into the following types:-   Instances, such as compute instances and storage instances
-   Management elements of application services, such as workspaces and workflows
-   Management resources related to permissions, such as roles and policies |
|resource configurations|Cloud Config retrieves all your resources by using the APIs of Alibaba Cloud services. In a resource list, you can click a resource ID to view the configurations of the resource. You can also manage the resource in the Alibaba Cloud Management Console.|
|monitoring scope|You can configure the monitoring scope of Cloud Config by specifying the types of resources to be monitored. -   If a resource type is added to the monitoring scope, Cloud Config tracks your resources of this type and records the configuration changes every 10 minutes.
-   If a resource type is removed from the monitoring scope, Cloud Config does not record the configuration changes to the resources of this type. |
|rule|A rule is a function that is used to determine whether a resource configuration is compliant. Cloud Config runs rule code by using functions of Function Compute. Assume that a rule is applied to a resource type in Cloud Config. If the configurations of a resource of this type change, Cloud Config re-evaluates the resource based on the rule and checks whether the configuration is compliant. Cloud Config can also trigger rules at a specified time to periodically evaluate the compliance of all resources. The rules in Cloud Config are divided into the following categories:-   Managed rules

For more information, see [Managed rules](/intl.en-US/Preset rules/Managed rules.md).

-   Custom rules

You can use Function Compute to create a rule. Before you can create a rule, you must create a function in the Function Compute console. Then, you can select the function ARN in the Cloud Config console. For more information, see [Create a custom rule by using Function Compute](). |
|configuration timeline|Cloud Config provides a configuration timeline for each resource that is monitored. -   If a resource was created before you activate Cloud Config, the configuration timeline starts from the time when you activated Cloud Config.
-   If a resource is created after you activate Cloud Config, the configuration timeline starts from the time when the resource is created. Cloud Config detects configuration changes every 10 minutes. If resource configuration changes at a point in time, a node is generated on the configuration timeline. You can then view the basic information, configuration changes, and related operations of the resource. |
|compliance timeline|Cloud Config evaluates resources based on rules. A compliance record is generated when a rule is triggered. Cloud Config displays the compliance records over time in the compliance timeline. The compliance records that are displayed in the compliance timeline depend on the trigger type. -   If the trigger type is Periodic, the compliance timeline displays the records of periodical compliance evaluations.
-   If the trigger type is Configuration Changes, the compliance timeline displays the records of compliance evaluations of every configuration change.
-   If both trigger types are selected, the compliance timeline displays the compliance records of both types. |
|classified protection precheck|The classified protection precheck feature of Cloud Config monitors and evaluates your Alibaba Cloud resources in a continuous manner. You can view the compliance evaluation result in real time and remediate non-compliant resources. This simplifies the procedure of an official assessment. For more information, see [Baseline for Classified Protection of Cybersecurity 2.0](/intl.en-US/Resource compliance packages/Baseline for Classified Protection of Cybersecurity 2.0.md).|
|CIS|The [Center for Internet Security \(CIS\)](https://www.cisecurity.org/) is a community of organizations and individuals that want actionable security resources. The CIS Controls are a set of 20 controls designed to help organizations safeguard their systems and data.|
|resource directory|Resource Directory allows you to manage the relationships among multiple levels of enterprise resources \(accounts\). |
|management account|A management account is an account that is used to enable a resource directory and is the super administrator of the resource directory. The management account has all administrative permissions on the resource directory and the member accounts in the resource directory. Only an Alibaba Cloud account that has passed enterprise real-name verification can be used as a management account. Each resource directory has only one management account.

**Note:** A management account does not belong to a resource directory and is not limited by the control policies of a resource directory. |
|member account|A member account serves as a container for resources and is also an organizational unit in a resource directory. A member account indicates a project or application. The resources of different member accounts are isolated. You can use a management account to authorize RAM users, user groups, or roles to access the resources of member accounts.

You can use a management account to invite a member account to join a resource directory or create a member account in a resource directory. |
|account group|An account group is a collection of member accounts. In a resource directory, the management account can add all or some member accounts to an account group for centralized compliance management. An account group is also a resource pool formed by gathering resources from multiple member accounts.

The management account can view the resource lists, resource details, resource configuration timelines, resource compliance timelines, and associated resources of all member accounts in the account group. It can also create rules and compliance packages in the account group. These rules and compliance packages take effect on resources of all member accounts in the account group for continuous compliance evaluation. |

