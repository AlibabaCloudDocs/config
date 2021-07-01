# Manage the service-linked role for Cloud Config

The service-linked role for Cloud Config is named AliyunServiceRoleForConfig. It is a RAM role that authorizes Cloud Config to access other Alibaba Cloud services in specific scenarios.

**Note:** For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Scenarios

-   Cloud Config can retrieve resource configurations of other Alibaba Cloud services by assuming the AliyunServiceRoleForConfig role to call the API operations of these Alibaba Cloud services. The AliyunServiceRoleForConfig role allows Cloud Config to read the resource configurations.
-   You can specify an Object Storage Service \(OSS\) bucket to receive resource snapshots. The AliyunServiceRoleForConfig role allows Cloud Config to write snapshot files to the specified bucket.
-   You can specify a Log Service Logstore to receive resource change logs. The AliyunServiceRoleForConfig role allows Cloud Config to write log files to the specified Logstore.
-   You can specify a Message Service \(MNS\) topic to receive notifications of resource events. The AliyunServiceRoleForConfig role allows Cloud Config to send notifications of resource events to the specified topic.

## Role description

The following list describes the details of the service-linked role for Cloud Config:

-   Role name: AliyunServiceRoleForConfig.
-   Name of the policy that is attached to the role: AliyunServiceRolePolicyForConfig.
-   Policy description: This policy grants Cloud Config the permissions to read resource configurations of other Alibaba Cloud services, write resource snapshots to OSS buckets, write resource change logs to Log Service Logstores, and send notifications of resource events to MNS topics.

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
                    "rds:DescribeParameters",
                    "rds:DescribeSQLCollector*",
                    "rds:DescribeActionEventPolicy",
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
                    "kms:DescribeKeyVersion",
                    "kms:ListKeyVersions",
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
                    "resourcemanager:ListHandshakesForResourceDirectory",
                    "resourcemanager:GetHandshake",
                    "resourcemanager:ListResourceGroups",
                    "resourcemanager:GetResourceGroup",
                    "composer:GetFlow",
                    "composer:DescribeFlow",
                    "nas:Describe*",
                    "hbase:Describe*",
                    "hbase:Get*",
                    "hbase:List*",
                    "hbase:Query*",
                    "cs:Get*",
                    "cs:List*",
                    "dms:List*",
                    "dms:Get*",
                    "mq:OnsInstanceInServiceList",
                    "mq:OnsInstanceBaseInfo",
                    "mq:OnsTopicList",
                    "mq:OnsGroupList",
                    "mq:QueryInstanceBaseInfo",
                    "mq:PUB",
                    "mq:SUB",
                    "mq:ListTagResources",
                    "alidns:Describe*",
                    "alidns:List*",
                    "mse:Query*",
                    "mse:List*",
                    "ros:Describe*",
                    "ros:Get*",
                    "ros:List*",
                    "elasticsearch:List*",
                    "elasticsearch:Describe*",
                    "dcdn:Describe*",
                    "hcs-sgw:Describe*",
                    "eci:Describe*",
                    "kms:ListSecrets",
                    "kms:DescribeSecret",
                    "privatelink:List*",
                    "privatelink:Get*",
                    "brain-industrial:List*",
                    "brain-industrial:Get*",
                    "imagesearch:List*",
                    "imagesearch:Describe*",
                    "hitsdb:Describe*",
                    "apigateway:Describe*",
                    "sas:DescribeGroupedVul",
                    "sas:DescribeFieldStatistics",
                    "cmn:List*",
                    "cmn:Get*",
                    "ledgerdb:Describe*",
                    "pvtz:Describe*",
                    "oos:Search*",
                    "oos:List*",
                    "adb:Describe*",
                    "edas:Read*",
                    "drds:Describe*",
                    "gpdb:Describe*"
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
                    "composer:CreateFlow",
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


## Create the AliyunServiceRoleForConfig role

You can create the service-linked role AliyunServiceRoleForConfig in the Cloud Config console.

-   Use an ordinary account

    If you use an ordinary account, you must create the service-linked role AliyunServiceRoleForConfig before you can use Cloud Config. For more information, see [Authorize Cloud Config to access your resources]().

-   Use a management account

    You can use a management account to add all or some member accounts in your resource directory to an account group. This way, Cloud Config automatically creates the service-linked role AliyunServiceRoleForConfig for all member accounts in the account group. For more information about account groups, see [Overview](/intl.en-US/Account groups/Overview.md).


## Delete the AliyunServiceRoleForConfig role

Cloud Config does not automatically delete the service-linked role AliyunServiceRoleForConfig. To delete the role, you must log on to the [RAM console](https://ram.console.aliyun.com/). For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

