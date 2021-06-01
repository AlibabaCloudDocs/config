# Announcement: Cloud Config provides the account group feature to replace Cloud Config for Enterprise

Cloud Config provides the account group feature to replace Cloud Config for Enterprise. You can specify multiple member accounts in an account group to manage the compliance data of the resources within these accounts in a unified manner. In addition, you can divide member accounts into multiple account groups to realize differentiated compliance management for your enterprise. The account group feature achieves the same effect as Cloud Config for Enterprise, except that you cannot divide member accounts when you use Cloud Config for Enterprise. The release of the account group feature has no negative impact on your business.

## Changes to the console

The Cloud Config console allows you to manage the compliance data for both the management account and member accounts in your resource directory based on account groups. After the account group feature is used, pay attention to the following changes:

-   Cloud Config for Enterprise: If you use a management account to manage the compliance data, you must manage the compliance data for all member accounts in your resource directory as a whole.
-   Account group: If you use a management account to manage the compliance data, you can manage the compliance data for all or some member accounts in your resource directory based on account groups. You can create a maximum of five account groups for each management account and specify different accounts for each account group. This helps you manage the compliance data of the resources within multiple accounts.

If you are using Cloud Config for Enterprise, a global account group is automatically generated among other account groups. The existing rules and compliance packages still apply to the account group.

## Changes to the API

The `MultiAccount` and `MemberId` parameters of the following operations are scheduled to be offline before 00:00:00 on June 30, 2021. The account group-related operations are scheduled to be online before 00:00:00 on May 30, 2021.

-   [GetDiscoveredResourceCounts](/intl.en-US/API Reference/Resources/GetDiscoveredResourceCounts.md)
-   [ListDiscoveredResources](/intl.en-US/API Reference/Resources/ListDiscoveredResources.md)
-   [DescribeDiscoveredResource](/intl.en-US/API Reference/Resources/DescribeDiscoveredResource.md)
-   [GetDiscoveredResourceSummary](/intl.en-US/API Reference/Resources/GetDiscoveredResourceSummary.md)
-   [GetResourceComplianceTimeline](/intl.en-US/API Reference/Resources/GetResourceComplianceTimeline.md)
-   [GetResourceConfigurationTimeline](/intl.en-US/API Reference/Resources/GetResourceConfigurationTimeline.md)
-   [DescribeConfigRule](/intl.en-US/API Reference/Rules/DescribeConfigRule.md)
-   [ListConfigRules](/intl.en-US/API Reference/Rules/ListConfigRules.md)
-   [PutConfigRule](/intl.en-US/API Reference/Rules/PutConfigRule.md)
-   [DescribeEvaluationResults](/intl.en-US/API Reference/Rules/DescribeEvaluationResults.md)
-   [DescribeCompliance](/intl.en-US/API Reference/Rules/DescribeCompliance.md)
-   [DescribeComplianceSummary](/intl.en-US/API Reference/Rules/DescribeComplianceSummary.md)

If you are using the `MultiAccount` and `MemberId` parameters, we recommend that you use the account group-related operations after 00:00:00 on May 30, 2021. If you want to use these two parameters, we recommend that you wait until the account group-related operations are available. For more information about account groups, see [Overview](/intl.en-US/Account groups/Overview.md).

