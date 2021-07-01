# Deliver resource snapshots to an OSS bucket

If you want to deliver resource change snapshots and scheduled resource snapshots to Object Storage Service \(OSS\), you must specify a bucket. After the resource snapshots are delivered to the specified bucket, you can view or download JSON files.

OSS is activated. For more information, see [Activate OSS](/intl.en-US/Console User Guide/Sign up for OSS.md).

To achieve a balance between storage costs and scenario-specific requirements, we recommend that you select **Standard** for the **Storage Class** parameter when you create an OSS bucket. If you need only to store data that is infrequently accessed \(once or twice each month\) for a long period of time, we recommend that you select **IA** for the **Storage Class** parameter when you create an OSS bucket. For more information, see [Create buckets](/intl.en-US/Console User Guide/Manage buckets/Create buckets.md).

## Use an ordinary account

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Set the required parameters to specify an OSS bucket to store resource snapshots.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Region**|The region where the OSS bucket resides.|
    |**Bucket**|The name of the OSS bucket. The bucket name must be unique.     -   If you select **Create Bucket**, you must specify a bucket name.
    -   If you select **Select Buckets**, you must select an existing bucket from the Bucket drop-down list. |
    |**Server-side Encryption**|Specifies whether to encrypt objects in the OSS bucket. This parameter must be specified if you select **Create Bucket**. Valid values:

    -   **No**
    -   **AES256**
    -   **KMS** |

5.  Click **OK**.


## Use a management account

You can use a management account to specify an OSS bucket to receive the resource snapshots of the management account and its member accounts. The bucket must belong to the management account or a member account. Only management accounts are authorized to configure the delivery settings of resource snapshots. No member accounts have the relevant permissions.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Set the required parameters to specify an OSS bucket to store resource snapshots.

    You can create an OSS bucket within the management account, or select an existing OSS bucket that belongs to the management account or a member account. The OSS bucket stores the resource snapshots within the management account and its member accounts.

    -   To deliver resource snapshots to an OSS bucket that belongs to the management account, select **Create Bucket** or **Select Buckets**, and then set the required parameters. The following table describes the parameters.

        |Parameter|Description|
        |---------|-----------|
        |**Region**|The region where the OSS bucket resides.|
        |**Bucket**|The name of the OSS bucket. The bucket name must be unique.         -   If you select **Create Bucket**, you must specify a bucket name.
        -   If you select **Select Buckets**, you must select an existing bucket from the Bucket drop-down list. |
        |**Server-side Encryption**|Specifies whether to encrypt objects in the OSS bucket. This parameter must be specified if you select **Create Bucket**. Valid values:

        -   **No**
        -   **AES256**
        -   **KMS** |

    -   To deliver resource snapshots to an OSS bucket that belongs to a member account, select **Select Buckets from Other Enterprise Management Accounts**, and then set the required parameters. Before you set the parameters, make sure that the member account has available buckets. The following table describes the parameters that are used to specify the Alibaba Cloud Resource Name \(ARN\) of the bucket within the member account and the ARN of the role to be assumed by the member account.

        |Parameter|Description|
        |---------|-----------|
        |**The ARN of the bucket that belongs to the destination account**|The ARN of the bucket in the member account, such as `acs:oss:ap-southeast-1:178589740730****:test123`. The ARN must be in the format of `acs:oss:{regionId}:{AccountID}:{bucketName}`. The following list describes the fields:

        -   `{regionId}`: the ID of the region where the bucket resides, such as ap-southeast-1.
        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `{bucketName}`: the name of the bucket, such as test123. |
        |**The role ARN that belongs to the destination account**|The ARN of the role to be assumed by the member account, such as `acs:ram::178589740730****:role/aliyunserviceroleforconfig`. Before you set this parameter, make sure that you have obtained the ID of the member account. Then, set the parameter based on the required format.

The ARN must be in the format of `acs:ram::{AccountID}:role/aliyunserviceroleforconfig`. The following list describes the fields:

        -   `{AccountID}`: the ID of the member account, such as 178589740730\*\*\*\*.
        -   `aliyunserviceroleforconfig`: the role that authorizes Cloud Config to access other Alibaba Cloud services. |

5.  Click **OK**.


After the resource snapshots are delivered to the specified bucket, you can view or download JSON files on the Files page of the bucket in the OSS console. For information about the sample code that is used to deliver snapshots in the JSON format, see [Sample code used to deliver resource snapshots to OSS](/intl.en-US/Resource Snapshots/Sample code used to deliver resource snapshots to OSS.md).

The path of each snapshot file is in the format of /ACSLogs/AccountId/Config/RegionId/yyyy/mm/dd/.

