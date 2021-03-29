# Basic concepts

This topic introduces the basic concepts of Cloud Config.

## Resource type

Cloud Config is a specialized service that is used to evaluate resources. A resource type is a category of resources. For example, the resource type of Elastic Compute Service \(ECS\) instances is Instance. The resource type code is ACS::ECS::Instance. Resources can be divided into the following types:

-   Instances, such as compute instances and storage instances
-   Management elements of application products, such as workspaces and workflows
-   Management resources related to permissions, such as roles and policies

## Resource configuration

Cloud Config retrieves the configuration of all your resources through the API of the corresponding cloud services. In the resource list, you can click a resource ID to view the configuration of the resource. You can also click Manage in the Actions column to manage the resource in the corresponding cloud service console.

## Monitoring scope

You can configure the monitoring scope of Cloud Config by specifying the resource types to be monitored.

-   If a resource type is added to the monitoring scope, Cloud Config tracks your resources of this type and records their configuration changes every 10 minutes.
-   If a resource type is removed from the monitoring scope, Cloud Config does not record the configuration changes to the resources of this type.

## Configuration timeline

Cloud Config provides a configuration timeline for each resource that is monitored.

-   If a resource is created before you activate Cloud Config, the configuration timeline starts from the time when you activate Cloud Config.
-   If a resource is created after you activate Cloud Config, the configuration timeline starts from the time when the resource is created. Cloud Config detects the configuration changes every 10 minutes. If resource configuration changes at a point in time, a node is generated on the configuration timeline. You can then view the basic information, configuration changes, and related operations of the resource.

## Rule

A rule is a function that is used to determine whether a resource configuration is compliant. Cloud Config uses functions of Function Compute to run rule code. Assume that a rule is applied to a resource type in Cloud Config. If the configurations of a resource of this type changes, Cloud Config re-evaluates the resource based on the rule and checks whether the configurations are compliant. Cloud Config can also trigger rules at a specified frequency to periodically evaluate the compliance of all resources. The rules in Cloud Config are divided into the following categories:

-   Managed rules

    Cloud Config provides managed rules. For more information, see [Managed rules](/intl.en-US/Resource Compliance Audit/Preset rules/Managed rules.md).

-   Custom rules

    You can use Function Compute to create a rule. Before you can create a rule, you must create a function in the Function Compute console. Then you can select the function ARN in the Cloud Config console. For more information, see [Create a custom rule by using Function Compute](/intl.en-US/Resource Compliance Audit/Develop custom rules/Create a custom rule by using Function Compute.md). You can use custom rules to evaluate the compliance of resources in different scenarios.


## Compliance timeline

Cloud Config evaluates resources based on rules. A compliance record is generated when a rule is triggered. Cloud Config displays the compliance records over time in the compliance timeline. The compliance records that are displayed in the compliance timeline depend on the trigger type.

-   If the trigger type is Periodic, the compliance timeline displays the records of periodical compliance evaluations.
-   If the trigger type is Configuration Changes, the compliance timeline displays the records of compliance evaluations of every configuration change.
-   If both trigger types are selected, the compliance timeline displays the compliance records of both types.

