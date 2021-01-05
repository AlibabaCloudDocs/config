# Sample code used to deliver resource change logs to Log Service

You can enable the delivery feature for resource change logs. Then, Cloud Config for Enterprise delivers the logs of the master account and its member accounts in a specified format to Log Service if the resource configurations are changed. This topic describes the sample code that is used to deliver resource change logs. This topic also describes the related parameters.

**Note:** The log topic of resource change logs that are delivered by Cloud Config for Enterprise to Log Service is in the `__topic__:staging` format. For more information about logs and log topics, see [Logs](/intl.en-US/Product Introduction/Basic concepts/Logs.md) and [Log topics](/intl.en-US/Product Introduction/Basic concepts/Log topics.md).

The following table describes the parameters of resource change logs.

|Parameter|Description|
|---------|-----------|
|accountId|The ID of the master account that owns the resource.|
|arn|The Alibaba Cloud Resource Name \(ARN\) of the resource. For more information about the ARN formats of cloud services, see [ARN formats]().|
|captureTime|The timestamp when the Cloud Config for Enterprise detects a resource change event and generates a log. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|
|configuration|The configurations of the resource.|
|configurationDiff|The resource configuration details before and after changes.|
|regionId|The ID of the region where the resource resides.|
|resourceCreateTime|The timestamp when the resource is created. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|
|resourceDirectoryId|The ID of the resource directory, for example, rd-EV\*\*\*\*.|
|resourceEventType|The type of the resource change event. Valid values:-   DISCOVERED: A resource is created.
-   MODIFY: A resource is modified.
-   REMOVE: A resource is deleted. |
|resourceId|The ID of the resource.|
|resourceName|The name of the resource.|
|resourceType|The type of the resource. For more information about supported resource types, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
|tags|The tags of the resource.|

## Create a resource

In this example, an Object Storage Service \(OSS\) bucket named new-bucket is created in the China \(Shanghai\) region by using a master account. The master account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations before the changes are "null". The following sample code is used:

```
accountId:1208863178****
arn:acs:oss:cn-shanghai:1208863178****:new-bucket
captureTime:1605509680560
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"new-bucket","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-****.aliyuncs.com","IntranetEndpoint":"oss-cn-****-internal.aliyuncs.com","Location":"oss-cn-****"}
configurationDiff:{"AccessControlList":[null,{"Grant":"private"}],"ServerSideEncryptionRule":[null,{"SSEAlgorithm":"None"}],"CreationDate":[null,"2020-11-16T06:50:36.000Z"],"Owner":[null,{"DisplayName":"1208863178****","ID":"1208863178****"}],"BucketPolicy":[null,{"LogPrefix":"","LogBucket":""}],"StorageClass":[null,"Standard"],"ExtranetEndpoint":[null,"oss-cn-****.aliyuncs.com"],"DataRedundancyType":[null,"LRS"],"AllowEmptyReferer":[null,"true"],"IntranetEndpoint":[null,"oss-cn-****-internal.aliyuncs.com"],"Name":[null,"new-bucket"],"Location":[null,"oss-cn-****"]}
regionId:cn-shanghai
resourceCreateTime:1605509436000
resourceDirectoryId:rd-EV****
resourceEventType:DISCOVERED
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

## Update a resource

In this example, the read and write permissions of an OSS bucket named new-bucket in the China \(Shanghai\) region are modified by using a master account. The master account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations are changed from "public-read-write" to "private". The following sample code is used:

```
accountId:12088631786*****
arn:acs:oss:cn-shanghai:12088631786*****:new-bucket
captureTime:1605513034150
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-05T10:42:44.000Z","Owner":{"DisplayName":"12088631786*****","ID":"12088631786*****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www. *****.com","https://www. *****.com"]},"AllowEmptyReferer":"false","Name":"new-bucket","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"},{"Value":"vv","Key":"kk"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}
configurationDiff:{"AccessControlList":[{"Grant":"public-read-write"},{"Grant":"private"}]}
regionId:cn-shanghai
resourceCreateTime:1583404964000
resourceDirectoryId:rd-EV****
resourceEventType:MODIFY
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

## Delete a resource

In this example, an OSS bucket named new-bucket in the China \(Shanghai\) region is deleted by using a master account. The master account is in a resource directory named rd-EV\*\*\*\*. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations after the changes are "null". The following sample code is used:

```
accountId:1208863178****
arn:acs:oss:cn-shanghai:1208863178****:new-bucket
captureTime:1605509680560
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"cn-shanghai","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}
configurationDiff:{"AccessControlList":[{"Grant":"private"},null],"ServerSideEncryptionRule":[{"SSEAlgorithm":"None"},null],"CreationDate":["2020-11-16T06:50:36.000Z",null],"Owner":[{"DisplayName":"1208863178****","ID":"1208863178****"},null],"BucketPolicy":[{"LogPrefix":"","LogBucket":""},null],"StorageClass":["Standard",null],"ExtranetEndpoint":["oss-cn-shanghai.aliyuncs.com",null],"DataRedundancyType":["LRS",null],"AllowEmptyReferer":["true",null],"IntranetEndpoint":["oss-cn-shanghai-internal.aliyuncs.com",null],"Name":["new-bucket",null],"Location":["oss-cn-shanghai",null]}
regionId:cn-shanghai
resourceCreateTime:1605509436000
resourceDirectoryId:rd-EV****
resourceEventType:REMOVE
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

