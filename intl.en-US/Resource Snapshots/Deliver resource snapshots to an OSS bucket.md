# Deliver resource snapshots to an OSS bucket

If you want to deliver resource change snapshots and scheduled resource snapshots to Object Storage Service \(OSS\), you must specify a bucket. After the resource snapshots are delivered to the specified bucket, you can view or download JSON files.

OSS is activated. For more information, see [Activate OSS](/intl.en-US/Console User Guide/Sign up for OSS.md).

-   For more information about OSS, see [What is OSS?](/intl.en-US/Product Introduction/What is OSS?.md).
-   For information about the code samples that are used to deliver an object in the JSON format, see [Sample code used to deliver resource snapshots to OSS]().

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, choose **Delivery Services** \> **Deliver Logs to OSS**.

3.  On the **Deliver Logs to OSS** page, turn on the **OSS Settings** switch.

4.  Set the required parameters to specify an OSS bucket to store resource snapshots.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Region**|The region where the OSS bucket resides.|
    |**Bucket**|The name of the OSS bucket. The bucket name must be unique.    -   If you select **Create a bucket**, you must specify a bucket name.
    -   If you select **Select an existing bucket of your account**, you must select an existing bucket from the Bucket drop-down list. |
    |**Server-side Encryption**|Specifies whether to encrypt the objects in the bucket. This parameter must be specified if you select **Create a bucket**.The following encryption methods are supported:

    -   **AES256**
    -   **KMS** |

5.  Click **OK**.


After the resource snapshots are delivered to the specified bucket, you can view or download JSON files on the Files page of the destination bucket in the OSS console. The path of each snapshot is in the format of /ACSLogs/AccountId/Config/RegionId/yyyy/mm/dd/.

