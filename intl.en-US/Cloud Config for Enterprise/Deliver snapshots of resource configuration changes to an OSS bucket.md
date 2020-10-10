# Deliver snapshots of resource configuration changes to an OSS bucket

You can use a master account to specify an Object Storage Service \(OSS\) bucket to store the snapshots of resource configuration changes of the master account and the member accounts in the resource directory. The specified OSS bucket must belong to the master account or a member account. You cannot use a member account to specify an OSS bucket. The snapshots of resource configuration changes of a member account are delivered to the OSS bucket that is specified by the master account.

-   The master account is used to log on to the Cloud Config for Enterprise console.
-   OSS is activated. For more information, see [Activate OSS](/intl.en-US/Quick Start/Sign up for OSS.md).

For more information about OSS, see [What is OSS?](/intl.en-US/Product Introduction/What is OSS?.md).

1.  Log on to the [Cloud Config for Enterprise console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Specify an OSS bucket to store snapshots of resource configuration changes.

    You can create an OSS bucket or select an existing bucket to store snapshots of resource configuration changes in the master account and member accounts. You can specify an OSS bucket that belongs to the master account or a member account.

    -   To specify an OSS bucket that belongs to the master account, select **Create a bucket** or **Select an existing bucket of your account** and set the parameters as described in the following table.

        |Parameter|Description|
        |---------|-----------|
        |**Region**|The region where the OSS bucket resides.|
        |**Bucket**|The name of the bucket. The name must be unique to an Alibaba Cloud account in a region.        -   If you select **Create a bucket**, you must specify a bucket name.
        -   If you select **Select an existing bucket of your account**, you must select an existing bucket from the drop-down list.

For more information about how to create a bucket in OSS, see [Create buckets](/intl.en-US/Console User Guide/Manage buckets/Create buckets.md). |
        |**Server-side Encryption**|Specifies whether to encrypt objects in the bucket. This parameter is available only when you select **Create a bucket**.The following encryption methods are supported:

        -   **AES256**
        -   **KMS** |

    -   To specify an OSS bucket that belongs to a member account, select **Select an existing bucket of another account \(enterprise account only\)** and set the parameters as described in the following table. Make sure that the member account has an available OSS bucket.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the bucket that belongs to the destination account**|The Alibaba Cloud Resource Name \(ARN\) of the specified OSS bucket in the member account.The ARN must be in the format of

`acs:oss:{regionId}:{Aliuid}:{bucketName}`. The following content describes the fields in the format:

        -   `{regionId}`: the region where the OSS bucket resides, for example, cn-shanghai.
        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `{bucketName}`: the name of the bucket, for example, test123.
An example of a bucket ARN is acs:oss:cn-shanghai:178589740730\*\*\*\*:test123. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account.The ARN of the role must be in the format of

`acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`. The following content describes the fields in the format:

        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service linked role that authorizes Cloud Config for Enterprise to deliver the snapshots of resource configuration changes to the specified OSS bucket.
An example of a role ARN is acs:ram::178589740730\*\*\*\*:role/aliyunserviceroleforconfig. |

5.  Click **OK**.


After the snapshots of resource configuration changes are delivered to the OSS bucket, you can view them in the OSS console.

1.  Log on to the [OSS console](https://oss.console.aliyun.com/).
2.  In the left-side navigation pane, click **Buckets**.
3.  On the **Buckets** page, find the bucket that you want to view by searching or filtering.
4.  Click the name of the bucket.
5.  In the left-side navigation pane, choose **Files** \> **Files**.

    On the **Files** page, you can view the snapshots of resource configuration changes. The path of each snapshot is in the format of /ACSLogs/AccountId/Config/RegionId/yyyy/mm/dd/.


