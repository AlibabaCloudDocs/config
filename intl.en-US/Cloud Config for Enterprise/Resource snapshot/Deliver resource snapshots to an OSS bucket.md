# Deliver resource snapshots to an OSS bucket

You can use a master account to deliver resource snapshots of the master account and its member accounts in your resource directory to an Object Storage Service \(OSS\) bucket. The bucket must belong to the master account or a member account. Only master accounts are authorized to deliver resource snapshots. No member accounts have the relevant permissions. The resource snapshots include resource change snapshots and scheduled resource snapshots.

-   A master account is used to log on to the Cloud Config console.
-   OSS is activated. For more information, see [Activate OSS](/intl.en-US/Console User Guide/Sign up for OSS.md).

-   For more information about OSS, see [What is OSS?](/intl.en-US/Product Introduction/What is OSS?.md).
-   For information about the code samples that are used to deliver an object in the JSON format, see [Sample code used to deliver resource snapshots to OSS]().

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on the **OSS Settings** switch.

4.  Specify an OSS bucket to store resource snapshots.

    You can create an OSS bucket within the current master account, or select an existing bucket that belongs to the master account or a member account. The OSS bucket stores the resource snapshots within the master account and its member accounts.

    -   To deliver resource snapshots to an OSS bucket that belongs to the master account, select **Create a bucket** or **Select an existing bucket of your account**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Region**|The region where the OSS bucket resides.|
        |**Bucket**|The name of the OSS bucket. The bucket name must be unique.        -   If you select **Create a bucket**, you must specify a bucket name.
        -   If you select **Select an existing bucket of your account**, you must select an existing bucket from the Bucket drop-down list. |
        |**Server-side Encryption**|Specifies whether to encrypt the objects in the bucket. This parameter must be specified if you select **Create a bucket**.The following encryption methods are supported:

        -   **AES256**
        -   **KMS** |

    -   To deliver resource snapshots to an OSS bucket that belongs to a member account, select **Select an existing bucket of another account \(enterprise account only\)**, and then set the required parameters. Before you set the parameters, make sure that the member account has available buckets. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the bucket that belongs to the destination account**|The Alibaba Cloud Resource Name \(ARN\) of the specified OSS bucket in the member account, for example, `acs:oss:ap-southeast-1:178589740730****:test123`.Before you set this parameter, make sure that you have obtained the ID of the member account, the region where the bucket resides, and the name of the bucket.

The ARN must be in the format of `acs:oss:{regionId}:{Aliuid}:{bucketName}`, where:

        -   `{regionId}`: the ID of the region where the bucket resides, for example, ap-southeast-1.
        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `{bucketName}`: the name of the bucket, for example, test123. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, for example, `acs:ram::178589740730****:role/aliyunserviceroleforconfig`.Before you set this parameter, make sure that you have obtained the ID of the member account. Then, set the parameter based on the ARN format.

The ARN must be in the format of `acs:ram::{Aliuid}:role/aliyunserviceroleforconfig`, where:

        -   `{Aliuid}`: the ID of the member account, for example, 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the service-linked role that authorizes Cloud Config to deliver resource snapshots to the specified OSS bucket. |

5.  Click **OK**.


After the resource snapshots are delivered to the specified bucket, you can view or download JSON files on the Files page of the destination bucket in the OSS console. The path of each snapshot is in the format of /ACSLogs/AccountId/Config/RegionId/yyyy/mm/dd/.

