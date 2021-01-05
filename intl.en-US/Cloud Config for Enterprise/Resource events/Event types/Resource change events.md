# Resource change events

When Cloud Config for Enterprise detects a resource change, Cloud Config for Enterprise immediately sends a notification to you by using Message Service \(MNS\). This topic describes the sample code of resource change events. This topic also describes the related parameters.

The following table describes the parameters of resource change events.

|Parameter|Description|
|---------|-----------|
|accountId|The ID of the master account that owns the resource.|
|resourceName|The name of the resource.|
|AvailabilityZone|The zone where the resource resides.|
|resourceType|The type of the resource. For more information about supported resource types, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
|resourceEventType|The type of the resource change event. Valid values:-   DISCOVERED: A resource is created.
-   MODIFY: A resource is modified.
-   REMOVE: A resource is deleted. |
|resourceCreateTime|The timestamp when the resource is created. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|
|RelationshipDiff|The change item of the associated resource.|
|captureTime|The timestamp when Cloud Config for Enterprise detects a resource change event and generates a log. For information about how to convert timestamps, see [UNIX timestamp](https://oktools.net/timestamp).|
|configurationDiff|The change item of the resource event.|
|resourceId|The ID of the resource.|
|Relationship|The associated resource.|
|region|The region where the resource resides.|
|tags|The tags of the resource.|

## Create a resource

In this example, an Object Storage Service \(OSS\) bucket named new-bucket is created in the China \(Shanghai\) region by using a master account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations before the changes are "null". The following sample code is used:

```
{
          "AccountId":120886317861****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"cn-shanghai-a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"DISCOVERED",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605759241690,
          "ConfigurationDiff":"{\"AccessControlList\":[null,{\"Grant\":\"private\"}],\"ServerSideEncryptionRule\":[null,{\"SSEAlgorithm\":\"None\"}],\"CreationDate\":[null,\"2020-11-19T04:07:44.000Z\"],\"Owner\":[null,{\"DisplayName\":\"120886317861****\",\"ID\":\"120886317861****\"}],\"StorageClass\":[null,\"Standard\"],\"DataRedundancyType\":[null,\"LRS\"],\"AllowEmptyReferer\":[null,\"true\"],\"Name\":[null,\"new-bucket\"],\"Versioning\":[null,\"Enabled\"],\"BucketPolicy\":[null,{\"LogPrefix\":\"\",\"LogBucket\":\"\"}],\"ExtranetEndpoint\":[null,\"oss-cn-shanghai.aliyuncs.com\"],\"IntranetEndpoint\":[null,\"oss-cn-shanghai-internal.aliyuncs.com\"],\"Location\":[null,\"oss-cn-shanghai\"]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"cn-shanghai",
          "Tags":"{}"
        }
```

## Update a resource

In this example, the encryption method of an OSS bucket named new-bucket in the China \(Shanghai\) region is modified by using a master account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations are changed from "None" to "AES256". The following sample code is used:

```
{
          "AccountId":120886317861****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"cn-shanghai-a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"MODIFY",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605779129000,
          "ConfigurationDiff":"{\"ServerSideEncryptionRule\":[{\"SSEAlgorithm\":\"None\"},{\"SSEAlgorithm\":\"AES256\"}]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"cn-shanghai",
          "Tags":"{}"
        }
```

## Delete a resource

In this example, an OSS bucket named new-bucket in the China \(Shanghai\) region is deleted by using a master account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations after the changes are "null". The following sample code is used:

```
{
          "AccountId":12088631786****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"cn-shanghai-a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"REMOVE",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605860519000,
          "ConfigurationDiff":"{\"AccessControlList\":[{\"Grant\":\"private\"},null],\"ServerSideEncryptionRule\":[{\"SSEAlgorithm\":\"AES256\"},null],\"CreationDate\":[\"2020-05-15T09:39:59.000Z\",null],\"Owner\":[{\"DisplayName\":\"120886317861****\",\"ID\":\"120886317861****\"},null],\"StorageClass\":[\"Standard\",null],\"DataRedundancyType\":[\"LRS\",null],\"RefererList\":[{\"Referer\":[\"https://www.tmall.com\"]},null],\"AllowEmptyReferer\":[\"false\",null],\"Name\":[\"ddddss\",null],\"BucketPolicy\":[{\"LogPrefix\":\"\",\"LogBucket\":\"\"},null],\"TagSet\":[]},null],\"ExtranetEndpoint\":[\"oss-cn-shanghai.aliyuncs.com\",null],\"Region\":[\"cn-shanghai\",null],\"IntranetEndpoint\":[\"oss-cn-shanghai-internal.aliyuncs.com\",null],\"Location\":[\"oss-cn-shanghai\",null]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"cn-shanghai",
          "Tags":"{}"
        }
```

