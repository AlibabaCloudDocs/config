# 资源日志投递到日志服务SLS的代码示例

如果您设置了资源日志投递功能，当资源的配置变更时，配置审计自动将资源日志以指定格式投递到日志服务SLS。通过本文您可以了解资源变更日志的代码示例和主要参数说明。

**说明：** 配置审计投递到日志服务SLS的资源变更日志的日志主题为`__topic__:staging`。日志和日志主题的概念，请参见[日志](/cn.zh-CN/产品简介/基本概念/日志.md)和[日志主题](/cn.zh-CN/产品简介/基本概念/日志主题.md)。

资源变更日志的主要参数说明如下表所示。

|参数|说明|
|--|--|
|accountId|资源所属阿里云账号ID。|
|arn|资源ARN，例如：对象存储OSS的存储桶，ARN格式为`arn:acs:oss:{regionId}:{Aliuid}:{bucketName}`，各参数含义如下：-   `{regionId}`：存储桶所在地域ID。
-   `{Aliuid}`：阿里云账号ID。
-   `{bucketName}`：存储桶名称。 |
|captureTime|配置审计发现资源变更事件的时间戳。|
|configuration|资源的详细配置。|
|configurationDiff|资源事件的变更项。|
|regionId|资源所在地域ID。|
|resourceCreateTime|创建资源的时间戳。|
|resourceEventType|资源变更事件的类型。取值：-   DISCOVERED：新建资源事件。
-   MODIFY：修改资源事件。
-   REMOVE：删除资源事件。 |
|resourceId|资源ID。|
|resourceName|资源名称。|
|resourceType|资源类型，例如：ACS::OSS::Bucket。|
|tags|资源的标签。|

## 新建资源

新建资源的代码示例如下：

```
accountId:1208863178****
arn:acs:oss:cn-shanghai:1208863178****:new-bucket
captureTime:1605509680560
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"new-bucket","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-****.aliyuncs.com","IntranetEndpoint":"oss-cn-****-internal.aliyuncs.com","Location":"oss-cn-****"}
configurationDiff:{"AccessControlList":[null,{"Grant":"private"}],"ServerSideEncryptionRule":[null,{"SSEAlgorithm":"None"}],"CreationDate":[null,"2020-11-16T06:50:36.000Z"],"Owner":[null,{"DisplayName":"1208863178****","ID":"1208863178****"}],"BucketPolicy":[null,{"LogPrefix":"","LogBucket":""}],"StorageClass":[null,"Standard"],"ExtranetEndpoint":[null,"oss-cn-****.aliyuncs.com"],"DataRedundancyType":[null,"LRS"],"AllowEmptyReferer":[null,"true"],"IntranetEndpoint":[null,"oss-cn-****-internal.aliyuncs.com"],"Name":[null,"new-bucket"],"Location":[null,"oss-cn-****"]}
regionId:cn-shanghai
resourceCreateTime:1605509436000
resourceEventType:DISCOVERED
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

## 更新资源

更新资源的代码示例如下：

```
accountId:12088631786*****
arn:acs:oss:cn-shanghai:12088631786*****:new-bucket
captureTime:1605513034150
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-05T10:42:44.000Z","Owner":{"DisplayName":"12088631786*****","ID":"12088631786*****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.*****.com","https://www.*****.com"]},"AllowEmptyReferer":"false","Name":"new-bucket","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"},{"Value":"vv","Key":"kk"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}
configurationDiff:{"AccessControlList":[{"Grant":"public-read-write"},{"Grant":"private"}]}
regionId:cn-shanghai
resourceCreateTime:1583404964000
resourceEventType:MODIFY
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

## 删除资源

删除资源的代码示例如下：

```
accountId:1208863178****
arn:acs:oss:cn-shanghai:1208863178****:new-bucket
captureTime:1605509680560
configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"1208863178****","ID":"1208863178****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"cn-shanghai","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}
configurationDiff:{"AccessControlList":[{"Grant":"private"},null],"ServerSideEncryptionRule":[{"SSEAlgorithm":"None"},null],"CreationDate":["2020-11-16T06:50:36.000Z",null],"Owner":[{"DisplayName":"1208863178****","ID":"1208863178****"},null],"BucketPolicy":[{"LogPrefix":"","LogBucket":""},null],"StorageClass":["Standard",null],"ExtranetEndpoint":["oss-cn-shanghai.aliyuncs.com",null],"DataRedundancyType":["LRS",null],"AllowEmptyReferer":["true",null],"IntranetEndpoint":["oss-cn-shanghai-internal.aliyuncs.com",null],"Name":["new-bucket",null],"Location":["oss-cn-shanghai",null]}
regionId:cn-shanghai
resourceCreateTime:1605509436000
resourceEventType:REMOVE
resourceId:new-bucket
resourceName:new-bucket
resourceType:ACS::OSS::Bucket
tags:{}
```

