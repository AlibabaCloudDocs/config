# Release notes

This topic describes the release dates, supported regions, and related topics for the main features of Cloud Config.

## April 2021

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Compliance packages|The following new compliance packages are provided:-   BestPracticesForDataBase
-   BestPracticesForECS
-   RMiTComplianceCheck

|2021-04-20|All regions|[Overview]()|

## March 2021

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Compliance packages|The following new compliance packages are provided:-   CISComplianceCheck
-   BestPracticesForNetwork
-   BestPracticesForAccountGovernance

|2021-03-31|All regions|[Overview]()|
|Compliance packages|A compliance package is a set of rules that are managed by Cloud Config based on a specific compliance scenario. The compliance package dynamically and continuously monitors the compliance of your cloud resources. The following compliance packages are provided:-   ClassifiedProtectionPreCheck
-   BestPracticesForOSS

|2021-03-15|All regions|[Overview]()|
|Account groups|Cloud Config provides the account group feature to replace Cloud Config for Enterprise. You can specify multiple member accounts in an account group to manage the compliance data of the resources within these accounts in a unified manner. In addition, you can divide member accounts into multiple account groups to realize differentiated compliance management for your enterprise.|2021-03-10|All regions|[Overview](/intl.en-US/Account groups/Overview.md)|

## December 2020

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Integration with ActionTrail events|You can view the details of operations performed by using the current Alibaba Cloud account and its RAM users in the last 90 days in the Cloud Config console. These operations include access to the Cloud Config console and OpenAPI Explorer. They are recorded by ActionTrail as events.|2020-12-16|All regions|[View ActionTrail event details](/intl.en-US/event log/View ActionTrail event details.md)|

## August 2020

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Delivery of resource change logs to Log Service|You can deliver resource change logs to a specified Log Service Logstore.|2020-08-18|All regions|[Deliver resource change logs to a Log Service project](/intl.en-US/Logs of resource configuration changes/Deliver resource change logs to a Log Service project.md)|

## March 2020

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Remediation settings|You can specify a remediation template for a rule. If Cloud Config detects that specific resource configurations violate this rule, you can use the remediation template to automatically or manually correct the non-compliant configurations, realizing the continuous compliance of the cloud resources.|2020-03-20|All regions|-   [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md)
-   [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md) |

## February 2020

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Delivery of event notifications to Message Service \(MNS\)|You can deliver notifications of resource change events, resource non-compliance events, and resource snapshot delivery events to a specified MNS topic.|2020-02-26|All regions|[Send notifications of resource events to an MNS topic](/intl.en-US/Events/Send notifications of resource events to an MNS topic.md)|
|Classified protection precheck|You can enable the classified protection precheck feature with a few clicks to continuously monitor your resources based on Multi-Level Protection Scheme \(MLPS\) 2.0 for free.|2020-02-01|All regions|[MLPS 2.0](/intl.en-US/Resource compliance packages/MLPS 2.0.md)|

## January 2020

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Risk levels for rules|You can define risk levels for rules to determine which rules you want to focus on when different rules have non-compliance evaluation results.|2020-01-15|All regions|[Create a rule based on a managed rule](/intl.en-US/Resource Compliance Audit/Manage rules/Create a rule based on a managed rule.md)|
|Display of associated resources|The details page of a resource displays the resources that are associated with the current resource.|2020-01-15|All regions|[View the details of a resource](/intl.en-US/Resources/View the details of a resource.md)|
|Simplified display of non-compliance information|The non-compliance information is structured and displayed in a list, so that you can identify the non-compliant configurations with ease.|2020-01-15|All regions|[View the compliance evaluation results](/intl.en-US/Resource Compliance Audit/View compliance evaluation results/View the compliance evaluation results.md)|

## December 2019

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Delivery of resource snapshots to Object Storage Service \(OSS\)|You can deliver resource snapshots, including resource change snapshots and scheduled resource snapshots to a specified OSS bucket.|2019-12-30|All regions|[Deliver resource snapshots to an OSS bucket](/intl.en-US/Resource Snapshots/Deliver resource snapshots to an OSS bucket.md)|
|More supported Alibaba Cloud services|Cloud Config continues to integrate with more Alibaba Cloud services.|2019-12-30|All regions|[Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md)|
|Release on the International site \(alibabacloud.com\)|Cloud Config is released for public preview on the International site \(alibabacloud.com\) and supports all regions outside mainland China.|2019-12-20|All regions|[Cloud Config on the International site \(alibabacloud.com\)](https://www.alibabacloud.com/products/cloud-config)|

## November 2019

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Custom rules|In addition to the managed rules provided by Cloud Config, you can create custom rules by using Function Compute.|2019-11-10|Regions supported by the China site \(aliyun.com\)|[Create a custom rule by using Function Compute]()|

## October 2019

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|More managed rules|Cloud Config provides you with more managed rules that you can directly use.|2019-10-30|Regions supported by the China site \(aliyun.com\)|[Managed rules](/intl.en-US/Preset rules/Managed rules.md)|
|More supported Alibaba Cloud services|Cloud Config continues to integrate with more Alibaba Cloud services.|2019-10-15|Regions supported by the China site \(aliyun.com\)|[Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md)|

## September 2019

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Optimization in searches of resources|You can filter resources by type, region, and compliance status, and search for resources by resource ID.|2019-09-30|Regions supported by the China site \(aliyun.com\)|[Search for resources](/intl.en-US/Resources/Search for resources.md)|
|Overview page|It shows a statistical view of resource distribution, compliance status, and recent changes.|2019-09-20|Regions supported by the China site \(aliyun.com\)|[Overview page in the Cloud Config console](https://config.console.aliyun.com/overview?accounttraceid=c2a7a0aedff64a6fb9f56b5d9a1ba206tnvi)|
|More managed rules|Cloud Config provides you with more managed rules that you can directly use.|2019-09-20|Regions supported by the China site \(aliyun.com\)|[Managed rules](/intl.en-US/Preset rules/Managed rules.md)|
|Continuous compliance evaluation|-   You can create rules based on compliance requirements to continuously and automatically monitor the compliance of resource configurations.
-   A compliance timeline can be formed for each monitored resource.
-   Each node in the compliance timeline indicates a compliance evaluation and displays the specific evaluation result.

|2019-09-15|Regions supported by the China site \(aliyun.com\)|[Rule definition and implementation]()|

## August 2019

|Feature|Description|Release date|Supported region|Related topic|
|-------|:----------|:-----------|----------------|:------------|
|Public preview of Cloud Config|-   You can view your resources in all regions in a unified manner and search for resources with efficiency.
-   Cloud Config tracks resource configuration changes and records the change details to form a configuration timeline for each monitored resource.
-   Each node in the configuration timeline indicates a resource configuration change and displays the details of the change.

|2019-08-31|Regions supported by the China site \(aliyun.com\)|[Overview](/intl.en-US/Resources/Overview.md)|

