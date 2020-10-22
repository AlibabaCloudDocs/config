# Deliver snapshots of resource configuration changes to an OSS bucket

This topic describes how to deliver snapshots of resource configuration changes as objects to Object Storage Service \(OSS\). This topic also describes how to view delivered snapshots in the OSS console. You must specify an OSS bucket to deliver the snapshots of resource configuration changes.

OSS is activated. For more information, see [Activate OSS](/intl.en-US/Quick Start/Sign up for OSS.md).

For more information about OSS, see [What is OSS?](/intl.en-US/Product Introduction/What is OSS?.md).

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on **OSS Settings**.

4.  Specify an OSS bucket to store snapshots of resource configuration changes.

    The following table describes the parameters for specifying an OSS bucket.

    |Parameter|Description|
    |---------|-----------|
    |**Region**|The region where the OSS bucket resides.|
    |**Bucket**|The name of the bucket. The name must be unique to an Alibaba Cloud account in a region.    -   If you select **Create a bucket**, you must specify a bucket name.
    -   If you select **Select an existing bucket of your account**, you must select an existing bucket from the Bucket drop-down list.

For more information about how to create a bucket in OSS, see [Create buckets](/intl.en-US/Console User Guide/Manage buckets/Create buckets.md). |
    |**Server-side Encryption**|Specifies whether to encrypt objects in the bucket. This parameter is displayed when you select **Create a bucket**.The following encryption methods are supported:

    -   **AES256**
    -   **KMS** |

5.  Click **OK**.


After the snapshots of resource configuration changes are delivered to the OSS bucket, you can view them in the OSS console.

1.  Log on to the [OSS console](https://oss.console.aliyun.com/).
2.  In the left-side navigation pane, click **Buckets**.
3.  On the **Buckets** page, find the bucket where you want to view snapshots by searching or filtering.
4.  Click the name of the bucket.
5.  In the left-side navigation pane, choose **Files** \> **Files**.

    On the **Files** page, view the snapshots of resource configuration changes. The path of each snapshot is in the format of /ACSLogs/AccountId/Config/RegionId/yyyy/mm/dd/.


