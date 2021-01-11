# Resource change events

When Cloud Config detects a resource change, Cloud Config immediately sends a notification to you by using Message Service \(MNS\). This topic describes the parameters and sample code of resource change events.

The following table describes the parameters of resource change events.

|Parameter|Description|
|---------|-----------|
|accountId|The ID of the Alibaba Cloud account that owns the resource.|
|resourceName|The name of the resource.|
|AvailabilityZone|The zone where the resource resides.|
|resourceType|The type of the resource. For more information about supported resource types, see [Alibaba Cloud services that support Cloud Config](/intl.en-US/Product Introduction/Alibaba Cloud services that support Cloud Config.md).|
|resourceEventType|The type of the resource change event. Valid values:-   DISCOVERED: A resource is created.
-   MODIFY: A resource is modified.
-   REMOVE: A resource is deleted. |
|resourceCreateTime|The timestamp when the resource is created.|
|RelationshipDiff|The change item of the associated resource.|
|captureTime|The timestamp when Cloud Config detects a resource change event and generates a log.|
|configurationDiff|The change item of the resource event.|
|resourceId|The ID of the resource.|
|Relationship|The associated resource.|
|region|The region where the resource resides.|
|tags|The tags of the resource.|

## Create a resource

In this example, an Object Storage Service \(OSS\) bucket named new-bucket is created in the Singapore \(Singapore\) region by using an Alibaba Cloud account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations before the changes are "null". The following sample code is used:

```
{
          "AccountId":120886317861****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"ap-southeast-1a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"DISCOVERED",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605759241690,
          "ConfigurationDiff":"{\"AccessControlList\":[null,{\"Grant\":\"private\"}],\"ServerSideEncryptionRule\":[null,{\"SSEAlgorithm\":\"None\"}],\"CreationDate\":[null,\"2020-11-19T04:07:44.000Z\"],\"Owner\":[null,{\"DisplayName\":\"120886317861****\",\"ID\":\"120886317861****\"}],\"StorageClass\":[null,\"Standard\"],\"DataRedundancyType\":[null,\"LRS\"],\"AllowEmptyReferer\":[null,\"true\"],\"Name\":[null,\"new-bucket\"],\"Versioning\":[null,\"Enabled\"],\"BucketPolicy\":[null,{\"LogPrefix\":\"\",\"LogBucket\":\"\"}],\"ExtranetEndpoint\":[null,\"oss-ap-southeast-1.aliyuncs.com\"],\"IntranetEndpoint\":[null,\"oss-ap-southeast-1-internal.aliyuncs.com\"],\"Location\":[null,\"oss-ap-southeast-1\"]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"ap-southeast-1",
          "Tags":"{}"
        }
```

## Update a resource

In this example, the encryption method of an OSS bucket named new-bucket in the Singapore \(Singapore\) region is modified by using an Alibaba Cloud account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations are changed from "None" to "AES256". The following sample code is used:

```
{
          "AccountId":120886317861****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"ap-southeast-1a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"MODIFY",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605779129000,
          "ConfigurationDiff":"{\"ServerSideEncryptionRule\":[{\"SSEAlgorithm\":\"None\"},{\"SSEAlgorithm\":\"AES256\"}]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"ap-southeast-1",
          "Tags":"{}"
        }
```

## Delete a resource

In this example, an OSS bucket named new-bucket in the Singapore \(Singapore\) region is deleted by using an Alibaba Cloud account. The resource configurations before and after changes are displayed in the configurationDiff parameter. The resource configurations after the changes are "null". The following sample code is used:

```
{
          "AccountId":12088631786****,
          "ResourceName":"new-bucket",
          "AvailabilityZone":"ap-southeast-1a",
          "ResourceType":"ACS::OSS::Bucket",
          "ResourceEventType":"REMOVE",
          "ResourceCreateTime":"",
          "RelationshipDiff":"",
          "CaptureTime":1605860519000,
          "ConfigurationDiff":"{\"AccessControlList\":[{\"Grant\":\"private\"},null],\"ServerSideEncryptionRule\":[{\"SSEAlgorithm\":\"AES256\"},null],\"CreationDate\":[\"2020-05-15T09:39:59.000Z\",null],\"Owner\":[{\"DisplayName\":\"120886317861****\",\"ID\":\"120886317861****\"},null],\"StorageClass\":[\"Standard\",null],\"DataRedundancyType\":[\"LRS\",null],\"RefererList\":[{\"Referer\":[\"https://www.tmall.com\"]},null],\"AllowEmptyReferer\":[\"false\",null],\"Name\":[\"ddddss\",null],\"BucketPolicy\":[{\"LogPrefix\":\"\",\"LogBucket\":\"\"},null],\"TagSet\":[]},null],\"ExtranetEndpoint\":[\"oss-ap-southeast-1.aliyuncs.com\",null],\"Region\":[\"ap-southeast-1\",null],\"IntranetEndpoint\":[\"oss-ap-southeast-1-internal.aliyuncs.com\",null],\"Location\":[\"oss-ap-southeast-1\",null]}",
          "ResourceId":"new-bucket",
          "Relationship":"",
          "Region":"ap-southeast-1",
          "Tags":"{}"
        }
```

