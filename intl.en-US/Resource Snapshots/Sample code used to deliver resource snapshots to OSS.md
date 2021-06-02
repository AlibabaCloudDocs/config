# Sample code used to deliver resource snapshots to OSS

You can enable the delivery feature for resource snapshots. Then, Cloud Config delivers the resource change snapshots or scheduled resource snapshots in a specified format to Object Storage Service \(OSS\). This topic describes the sample code that is used to deliver resource change snapshots and scheduled resource snapshots. This topic also describes the related parameters.

## Use an ordinary account

-   Resource change snapshots

    The following table describes the parameters of resource change snapshots.

    |Parameter|Description|
    |---------|-----------|
    |accountId|The ID of the Alibaba Cloud account that owns the resource.|
    |arn|The Alibaba Cloud Resource Name \(ARN\) of the resource. For more information about the ARN formats of cloud services, see [ARN formats]().|
    |regionId|The ID of the region where the resource resides.|
    |configuration|The configurations of the resource.|
    |configurationDiff|The resource configuration details before and after the change.|
    |captureTime|The timestamp when Cloud Config detects a resource change event and generates a log.|
    |resourceCreateTime|The timestamp when the resource is created.|
    |resourceId|The ID of the resource.|
    |resourceName|The name of the resource.|
    |resourceType|The type of the resource. For more information about the resource types supported by Cloud Config, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
    |tags|The tags of the resource.|
    |resourceEventType|The type of the resource change event. Valid values:    -   DISCOVERED: A resource is created.
    -   MODIFY: A resource is modified.
    -   REMOVE: A resource is deleted. |

    The following three pieces of code are used to create, modify, and delete a resource:

    -   Create a resource

        In this example, an OSS bucket named test123 is created in the China \(Shanghai\) region by using an Alibaba Cloud account. The resource configurations before and after the change are displayed in the configurationDiff parameter. The resource configurations before the change are "null".

        ```
        {
            "configurationItems":[
                {
                    "accountId":1208863178****,
                    "arn":"acs:oss:cn-shanghai:120886317****:test123",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"test123","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AccessControlList":[null,{"Grant":"private"}],"ServerSideEncryptionRule":[null,{"SSEAlgorithm":"None"}],"CreationDate":[null,"2020-11-16T06:50:36.000Z"],"Owner":[null,{"DisplayName":"1208863178****","ID":"1208863178****"}],"BucketPolicy":[null,{"LogPrefix":"","LogBucket":""}],"StorageClass":[null,"Standard"],"ExtranetEndpoint":[null,"oss-cn-shanghai.aliyuncs.com"],"DataRedundancyType":[null,"LRS"],"AllowEmptyReferer":[null,"true"],"IntranetEndpoint":[null,"oss-cn-shanghai-internal.aliyuncs.com"],"Name":[null,"test123"],"Location":[null,"oss-cn-shanghai"]}",
                    "captureTime":1605509680560,
                    "resourceCreateTime":1605509436000,
                    "resourceId":"test123",
                    "resourceName":"test123",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"{}",
                    "resourceEventType":"DISCOVERED"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

    -   Modify a resource

        In this example, a referer whitelist of an OSS bucket named test456 in the China \(Shanghai\) region is modified by using an Alibaba Cloud account. The resource configurations before and after the change are displayed in the configurationDiff parameter. The value of the AllowEmptyReferer parameter is changed from "true" to "false".

        ```
        {
            "configurationItems":[
                {
                    "accountId":1208863178****,
                    "arn":"acs:oss:cn-shanghai:1208863178****:test456",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-16T08:34:49.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.*****.com"]},"AllowEmptyReferer":"false","Name":"testoss111","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"001","Key":"526"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AllowEmptyReferer":["true","false"]}",
                    "captureTime":1605508188495,
                    "resourceCreateTime":1584347689000,
                    "resourceId":"test456",
                    "resourceName":"test456",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"",
                    "resourceEventType":"MODIFY"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

    -   Delete a resource

        In this example, an OSS bucket named test456 in the China \(Shanghai\) region is deleted by using an Alibaba Cloud account. The resource configurations before and after the change are displayed in the configurationDiff parameter. The resource configurations after the change are "null".

        ```
        {
            "configurationItems":[
                {
                    "accountId":1208863178****,
                    "arn":"acs:oss:cn-shanghai:120886317****:"test456",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"test456","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AccessControlList":[{"Grant":"private"},null],"ServerSideEncryptionRule":[{"SSEAlgorithm":"None"},null],"CreationDate":["2020-11-16T06:50:36.000Z",null],"Owner":[{"DisplayName":"1208863178****","ID":"1208863178****"},null],"BucketPolicy":[{"LogPrefix":"","LogBucket":""},null],"StorageClass":["Standard",null], "ExtranetEndpoint":["oss-cn-shanghai.aliyuncs.com",null],"DataRedundancyType":["LRS",null],"AllowEmptyReferer":["true",null],"IntranetEndpoint":["oss-cn-shanghai-internal.aliyuncs.com",null],"Name":["test456",null],"Location":["oss-cn-shanghai",null]}",
                    "captureTime":1605509680560,
                    "resourceCreateTime":1605509436000,
                    "resourceId":"test456",
                    "resourceName":"test456",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"{}",
                    "resourceEventType":"REMOVE"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

-   Scheduled resource snapshots

    The following table describes the parameters of scheduled resource snapshots.

    |Parameter|Description|
    |---------|-----------|
    |accountId|The ID of the Alibaba Cloud account that owns the resource.|
    |availabilityZone|The zone where the resource resides.|
    |regionId|The ID of the region where the resource resides.|
    |configuration|The configurations of the resource.|
    |resourceCreateTime|The timestamp when the resource is created.|
    |resourceId|The ID of the resource.|
    |resourceName|The name of the resource.|
    |resourceType|The type of the resource. For more information about the resource types supported by Cloud Config, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
    |tags|The tags of the resource.|

    In this example, the scheduled resource snapshots of an OSS bucket named test123 in the China \(Shanghai\) region are delivered to a specified bucket by using an Alibaba Cloud account. The following sample code is used:

    ```
    {
        "configurationItems":[
            {
                "accountId":12088631786*****,
                "availabilityZone":"",
                "regionId":"cn-shanghai",
                "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2019-08-29T06:02:59.000Z","Owner":{"DisplayName":"12088631786*****","ID":"12088631786*****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.******.com"]},"AllowEmptyReferer":"false","Name":"test123","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"001","Key":"526"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"}]},"Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                "resourceCreateTime":1567058579000,
                "resourceId":"test123",
                "resourceName":"test123",
                "resourceType":"ACS::OSS::Bucket",
                "tags":""
            }
        ],
        "fileVersion":"1.0"
    }
    ```


## Use a management account

-   Resource change snapshots

    The following table describes the parameters of resource change snapshots.

    |Parameter|Description|
    |---------|-----------|
    |accountId|The ID of the management account that owns the resource.|
    |arn|The ARN of the resource. For more information about the ARN formats of cloud services, see [ARN formats]().|
    |regionId|The ID of the region where the resource resides.|
    |configuration|The configurations of the resource.|
    |configurationDiff|The resource configuration details before and after the change.|
    |captureTime|The timestamp when Cloud Config detects a resource change event and generates a log.|
    |resourceCreateTime|The timestamp when the resource is created.|
    |resourceId|The ID of the resource.|
    |resourceName|The name of the resource.|
    |resourceType|The type of the resource. For more information about the resource types supported by Cloud Config, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
    |tags|The tags of the resource.|
    |resourceEventType|The type of the resource change event. Valid values:    -   DISCOVERED: A resource is created.
    -   MODIFY: A resource is modified.
    -   REMOVE: A resource is deleted. |
    |resourceDirectoryId|The ID of the resource directory, such as rd-EV\*\*\*\*.|

    The following three pieces of code are used to create, modify, and delete a resource:

    -   Create a resource

        In this example, an OSS bucket named test123 is created in the China \(Shanghai\) region by using a management account. The management account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after the change are displayed in the configurationDiff parameter. The resource configurations before the change are "null".

        ```
        {
            "configurationItems":[
                {
                    "accountId":120886317861****,
                    "arn":"acs:oss:cn-shanghai:120886317861****:test123",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"test123","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AccessControlList":[null,{"Grant":"private"}],"ServerSideEncryptionRule":[null,{"SSEAlgorithm":"None"}],"CreationDate":[null,"2020-11-16T06:50:36.000Z"],"Owner":[null,{"DisplayName":"120886317861****","ID":"120886317861****"}],"BucketPolicy":[null,{"LogPrefix":"","LogBucket":""}],"StorageClass":[null,"Standard"],"ExtranetEndpoint":[null,"oss-cn-shanghai.aliyuncs.com"],"DataRedundancyType":[null,"LRS"],"AllowEmptyReferer":[null,"true"],"IntranetEndpoint":[null,"oss-cn-shanghai-internal.aliyuncs.com"],"Name":[null,"test123"],"Location":[null,"oss-cn-shanghai"]}",
                    "captureTime":1605509680560,
                    "resourceCreateTime":1605509436000,
                    "resourceId":"new-bucket****",
                    "resourceName":"new-bucket****",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"{}",
                    "resourceEventType":"DISCOVERED",
                    "resourceDirectoryId":"rd-EV****"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

    -   Modify a resource

        In this example, a referer whitelist of an OSS bucket named test456 in the China \(Shanghai\) region is modified by using a management account. The management account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after the change are displayed in the configurationDiff parameter. The value of the AllowEmptyReferer parameter is changed from "true" to "false".

        ```
        {
            "configurationItems":[
                {
                    "accountId":120886317861****,
                    "arn":"acs:oss:cn-shanghai:120886317861****:test456",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-16T08:34:49.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.*****.com"]},"AllowEmptyReferer":"false","Name":"testoss111","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"001","Key":"526"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AllowEmptyReferer":["true","false"]}",
                    "captureTime":1605508188495,
                    "resourceCreateTime":1584347689000,
                    "resourceId":"test456",
                    "resourceName":"test456",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"",
                    "resourceEventType":"MODIFY",
                    "resourceDirectoryId":"rd-EV****"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

    -   Delete a resource

        In this example, an OSS bucket named test456 in the China \(Shanghai\) region is deleted by using a management account. The management account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after the change are displayed in the configurationDiff parameter. The resource configurations after the change are "null".

        ```
        {
            "configurationItems":[
                {
                    "accountId":120886317861****,
                    "arn":"acs:oss:cn-shanghai:120886317861****:"test456",
                    "regionId":"cn-shanghai",
                    "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"test456","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                    "configurationDiff":"{"AccessControlList":[{"Grant":"private"},null],"ServerSideEncryptionRule":[{"SSEAlgorithm":"None"},null],"CreationDate":["2020-11-16T06:50:36.000Z",null],"Owner":[{"DisplayName":"120886317861****","ID":"120886317861****"},null],"BucketPolicy":[{"LogPrefix":"","LogBucket":""},null],"StorageClass":["Standard",null], "ExtranetEndpoint":["oss-cn-shanghai.aliyuncs.com",null],"DataRedundancyType":["LRS",null],"AllowEmptyReferer":["true",null],"IntranetEndpoint":["oss-cn-shanghai-internal.aliyuncs.com",null],"Name":["test456",null],"Location":["oss-cn-shanghai",null]}",
                    "captureTime":1605509680560,
                    "resourceCreateTime":1605509436000,
                    "resourceId":"test456",
                    "resourceName":"test456",
                    "resourceType":"ACS::OSS::Bucket",
                    "tags":"{}",
                    "resourceEventType":"REMOVE",
                    "resourceDirectoryId":"rd-EV****"
                }
            ],
            "fileVersion":"1.0"
        }
        ```

-   Scheduled resource snapshots

    The following table describes the parameters of scheduled resource snapshots.

    |Parameter|Description|
    |---------|-----------|
    |accountId|The ID of the management account that owns the resource.|
    |availabilityZone|The zone where the resource resides.|
    |regionId|The ID of the region where the resource resides.|
    |configuration|The configurations of the resource.|
    |resourceCreateTime|The timestamp when the resource is created.|
    |resourceId|The ID of the resource.|
    |resourceName|The name of the resource.|
    |resourceType|The type of the resource. For more information about the resource types supported by Cloud Config, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
    |tags|The tags of the resource.|

    In this example, the scheduled resource snapshots of an OSS bucket named test123 in the China \(Shanghai\) region are delivered to a specified bucket by using a management account. The following sample code is used:

    ```
    {
        "configurationItems":[
            {
                "accountId":120886317861****,
                "availabilityZone":"",
                "regionId":"cn-shanghai",
                "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2019-08-29T06:02:59.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.******.com"]},"AllowEmptyReferer":"false","Name":"test123","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"001","Key":"526"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"}]},"Region":"cn-*****","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                "resourceCreateTime":1567058579000,
                "resourceId":"test123",
                "resourceName":"test123",
                "resourceType":"ACS::OSS::Bucket",
                "tags":""
            }
        ],
        "fileVersion":"1.0"
    }
    ```


