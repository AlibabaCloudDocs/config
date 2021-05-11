# 投递资源日志到日志服务SLS的代码示例

如果您设置了资源日志投递功能，当资源的配置变更时，配置审计自动将资源日志以指定格式投递到日志服务SLS。通过本文您可以了解资源日志的代码示例和主要参数说明。

**说明：** 配置审计投递到日志服务SLS的资源日志的日志主题为`__topic__:staging`。日志和日志主题的概念，请参见[日志](/cn.zh-CN/产品简介/基本概念/日志.md)和[日志主题](/cn.zh-CN/产品简介/基本概念/日志主题.md)。

## 普通账号

资源日志的主要参数说明如下表所示。

|参数|说明|
|--|--|
|accountId|资源所属阿里云账号ID。|
|arn|资源ARN。关于各云服务资源类型对应的ARN格式，请参见[ARN格式]()。|
|captureTime|配置审计发现资源变更事件并生成日志的时间戳。关于时间戳的转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|configuration|资源的详细配置。|
|configurationDiff|资源配置变更的具体变更项及变更前后信息。|
|regionId|资源所在地域ID。|
|resourceCreateTime|新建资源的时间戳。关于时间戳的转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|resourceEventType|资源变更事件的类型。取值：-   DISCOVERED：新建资源事件。
-   MODIFY：修改资源事件。
-   REMOVE：删除资源事件。 |
|resourceId|资源ID。|
|resourceName|资源名称。|
|resourceType|资源类型。关于配置审计支持的资源类型，请参见[支持配置审计的云服务](/cn.zh-CN/产品简介/支持配置审计的云服务.md)。|
|tags|资源标签。|

新建、修改和删除资源的代码示例如下：

-   新建资源

    阿里云账号在对象存储OSS的上海地域新建存储空间（Bucket） new-bucket，在configurationDiff中显示变更前信息（null）和变更后信息。

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

-   修改资源

    阿里云账号在对象存储OSS的上海地域修改存储空间new-bucket的读写权限，在configurationDiff中显示变更前信息public-read-write（公共读写）和变更后信息private（私有）。

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

-   删除资源

    阿里云账号在对象存储OSS的上海地域删除存储空间new-bucket，在configurationDiff中显示变更前信息和变更后信息（null）。

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


## 企业管理账号

资源日志的主要参数说明如下表所示。

|参数|说明|
|--|--|
|accountId|资源所属企业管理账号ID。|
|arn|资源ARN。关于各云服务资源类型对应的ARN格式，请参见[ARN格式]()。|
|captureTime|配置审计发现资源变更事件并生成日志的时间戳。关于时间戳的转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|configuration|资源的详细配置。|
|configurationDiff|资源配置变更的具体变更项及变更前后信息。|
|regionId|资源所在地域ID。|
|resourceCreateTime|新建资源的时间戳。关于时间戳的转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|resourceDirectoryId|资源目录ID，例如：rd-EV\*\*\*\*。|
|resourceEventType|资源变更事件的类型。取值：-   DISCOVERED：新建资源事件。
-   MODIFY：修改资源事件。
-   REMOVE：删除资源事件。 |
|resourceId|资源ID。|
|resourceName|资源名称。|
|resourceType|资源类型。关于配置审计支持的资源类型，请参见[支持配置审计的云服务](/cn.zh-CN/产品简介/支持配置审计的云服务.md)。|
|tags|资源标签。|

新建、修改和删除资源的代码示例如下：

-   新建资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域新建存储空间（Bucket） new-bucket，在configurationDiff中显示变更前信息（null）和变更后信息。

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

-   修改资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域修改存储空间new-bucket的读写权限，在configurationDiff中显示变更前信息public-read-write（公共读写）和变更后信息private（私有）。

    ```
    accountId:12088631786*****
    arn:acs:oss:cn-shanghai:12088631786*****:new-bucket
    captureTime:1605513034150
    configuration:{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-05T10:42:44.000Z","Owner":{"DisplayName":"12088631786*****","ID":"12088631786*****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.*****.com","https://www.*****.com"]},"AllowEmptyReferer":"false","Name":"new-bucket","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"},{"Value":"vv","Key":"kk"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}
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

-   删除资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域删除存储空间new-bucket，在configurationDiff中显示变更前信息和变更后信息（null）。代码示例如下：

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


