# Manage the service linked role associated with Cloud Config

The service linked role associated with Cloud Config is named AliyunServiceRoleForConfig. The role is a Resource Access Management \(RAM\) role that authorizes Cloud Config to access other Alibaba Cloud services in specific scenarios.

**Note:** For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Scenarios

The AliyunServiceRoleForConfig role is applicable to the following scenarios:

-   Cloud Config can call the API operations of other Alibaba Cloud services to retrieve the configurations of the resources that belong to your Alibaba Cloud account. The AliyunServiceRoleForConfig role allows Cloud Config to read the configurations of the resources.
-   You can specify an OSS bucket to receive resource configuration snapshots. The AliyunServiceRoleForConfig role allows Cloud Config to write snapshot files to the specified OSS bucket.

## Create a service linked role

You can create the AliyunServiceRoleForConfig role in the Cloud Config console.

-   Cloud Config for individuals

    To use Cloud Config with an Alibaba Cloud account, you must create a role that is associated with the service. For more information, see [Authorize Cloud Config to access your resources](/intl.en-US/Quick Start/Authorize Cloud Config to access your resources.md).

-   Cloud Config for Enterprise

    To use the Cloud Config for Enterprise, you must log on to the Cloud Config console with the enterprise account and click **Upgrade** on the Overview page. After Cloud Config is upgraded to the enterprise edition, Cloud Config creates the AliyunServiceRoleForConfig role for all member accounts.

    For more information, see [Overview](/intl.en-US/Cloud Config for Enterprise/Overview.md).


## Delete the AliyunServiceRoleForConfig role

If you no longer need a service linked role, you can log on to the [RAM console](https://ram.console.aliyun.com/) to delete the role. For more information, see [Delete a service-linked role](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Role description

The following list describes the detailed information of the role that is associate with Cloud Config:

-   Role name: AliyunServiceRoleForConfig.
-   Name of the permission policy that is attached to the role: AliyunServiceRolePolicyForConfig.
-   Description of the permission policy: The policy authorizes Cloud Config to read the resource configurations of the account and write configuration snapshots to an OSS bucket.

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Action": [
                    "ecs:Describe*",
                    "ess:Describe*",
                    "vpc:Describe*",
                    "rds:DescribeDBInstance*",
                    "rds:DescribeRegions",
                    "rds:DescribeBackup*",
                    "slb:Describe*",
                    "*:DescribeTags",
                    "oss:GetService",
                    "oss:GetBucket*",
                    "oss:ListBuckets",
                    "oss:ListObjects",
                    "ram:List*",
                    "ram:Get*",
                    "actiontrail:LookupEvents",
                    "actiontrail:Describe*",
                    "actiontrail:Get*",
                    "ots:BatchGet*",
                    "ots:Describe*",
                    "ots:Get*",
                    "ots:List*",
                    "ocs:Describe*",
                    "cms:Get*",
                    "cms:List*",
                    "cms:Query*",
                    "cms:BatchQuery*",
                    "cms:Describe*",
                    "kvstore:Describe*",
                    "fc:Get*",
                    "fc:List*",
                    "kms:DescribeKey",
                    "kms:DescribeRegions",
                    "kms:ListAliases",
                    "kms:ListAliasesByKeyId",
                    "kms:ListKeys",
                    "cdn:Describe*",
                    "yundun*:Get*",
                    "yundun*:Describe*",
                    "yundun*:Query*",
                    "yundun*:List*",
                    "polardb:Describe*",
                    "dds:Describe*",
                    "cen:Describe*",
                    "mns:ListTopic",
                    "mns:GetTopicAttributes",
                    "resourcemanager:GetAccount",
                    "resourcemanager:ListAccountsForParent",
                    "resourcemanager:ListAccounts",
                    "resourcemanager:GetFolder",
                    "resourcemanager:ListFoldersForParent",
                    "resourcemanager:ListAncestors",
                    "resourcemanager:GetResourceDirectory",
                    "composer:GetFlow",
                    "composer:DescribeFlow",
                    "nas:Describe*",
                    "hbase:Describe*",
                    "hbase:Get*",
                    "hbase:List*",
                    "hbase:Query*",
                    "cs:Get*"
                ],
                "Resource": "*",
                "Effect": "Allow"
            },
            {
                "Action": [
                    "oss:PutObject",
                    "fc:InvokeFunction",
                    "mns:PublishMessage",
                    "composer:GroupInvokeFlow",
                    "log:PostLogStoreLogs"
                ],
                "Resource": "*",
                "Effect": "Allow"
            },
            {
                "Action": [
                    "config:*"
                ],
                "Resource": "*",
                "Effect": "Allow"
            },
            {
                "Action": "ram:DeleteServiceLinkedRole",
                "Resource": "*",
                "Effect": "Allow",
                "Condition": {
                    "StringEquals": {
                        "ram:ServiceName": "config.aliyuncs.com"
                    }
                }
            }
        ]
    }
    ```


