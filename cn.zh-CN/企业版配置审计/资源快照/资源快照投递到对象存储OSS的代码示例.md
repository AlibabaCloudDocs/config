# 资源快照投递到对象存储OSS的代码示例

如果您设置了资源快照投递功能，企业版配置审计将企业管理账号和所有成员账号的资源变更历史快照或资源定时配置快照以指定格式投递到对象存储OSS。通过本文您可以了解资源变更历史快照和资源定时配置快照的代码示例和主要参数说明。

## 资源变更历史快照

资源变更历史快照的主要参数说明如下表所示。

|参数|说明|
|--|--|
|accountId|资源所属企业管理账号ID。|
|arn|资源ARN。各云服务资源类型对应的ARN格式，请参见[ARN格式]()。|
|regionId|资源所在地域ID。|
|configuration|资源的详细配置。|
|configurationDiff|资源配置变更的具体变更项及变更前后信息。|
|captureTime|企业版配置审计发现资源变更事件并生成日志的时间戳。时间戳转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|resourceCreateTime|创建资源的时间戳。时间戳转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|resourceId|资源ID。|
|resourceName|资源名称。|
|resourceType|资源类型。支持的资源类型请参见[支持配置审计的云服务](/cn.zh-CN/产品简介/支持配置审计的云服务.md)。|
|tags|资源标签。|
|resourceEventType|资源变更事件的类型。取值：-   DISCOVERED：新建资源事件。
-   MODIFY：修改资源事件。
-   REMOVE：删除资源事件。 |
|resourceDirectoryId|资源目录ID，例如：rd-EV\*\*\*\*。|

新建、更新和删除资源的代码示例如下：

-   新建资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域新建存储桶（Bucket） test123，在configurationDiff中显示变更前信息（null）和变更后信息。

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

-   更新资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域更新存储桶test666的Referer白名单，在configurationDiff中显示变更前信息（允许开启空Referer）和变更后信息（不允许开启空Referer）。

    ```
    {
        "configurationItems":[
            {
                "accountId":120886317861****,
                "arn":"acs:oss:cn-shanghai:120886317861****:test666",
                "regionId":"cn-shanghai",
                "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"AES256"},"Comment":"","CreationDate":"2020-03-16T08:34:49.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","RefererList":{"Referer":["https://www.*****.com"]},"AllowEmptyReferer":"false","Name":"testoss111","BucketPolicy":{"LogPrefix":"","LogBucket":""},"TagSet":{"Tag":[{"Value":"1","Key":"1"},{"Value":"2","Key":"2"},{"Value":"001","Key":"526"},{"Value":"612","Key":"612"},{"Value":"prod2","Key":"env"},{"Value":"v0","Key":"k0"}]},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","Region":"cn-shanghai","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                "configurationDiff":"{"AllowEmptyReferer":["true","false"]}",
                "captureTime":1605508188495,
                "resourceCreateTime":1584347689000,
                "resourceId":"test666",
                "resourceName":"test666",
                "resourceType":"ACS::OSS::Bucket",
                "tags":"",
                "resourceEventType":"MODIFY",
                "resourceDirectoryId":"rd-EV****"
            }
        ],
        "fileVersion":"1.0"
    }
    ```

-   删除资源

    资源目录rd-EV\*\*\*\*中的企业管理账号在对象存储OSS的上海地域删除存储桶test666，在configurationDiff中显示变更前信息和变更后信息（null）。

    ```
    {
        "configurationItems":[
            {
                "accountId":120886317861****,
                "arn":"acs:oss:cn-shanghai:120886317861****:"test666",
                "regionId":"cn-shanghai",
                "configuration":"{"AccessControlList":{"Grant":"private"},"ServerSideEncryptionRule":{"SSEAlgorithm":"None"},"Comment":"","CreationDate":"2020-11-16T06:50:36.000Z","Owner":{"DisplayName":"120886317861****","ID":"120886317861****"},"StorageClass":"Standard","DataRedundancyType":"LRS","AllowEmptyReferer":"true","Name":"test666","BucketPolicy":{"LogPrefix":"","LogBucket":""},"ExtranetEndpoint":"oss-cn-shanghai.aliyuncs.com","IntranetEndpoint":"oss-cn-shanghai-internal.aliyuncs.com","Location":"oss-cn-shanghai"}",
                "configurationDiff":"{"AccessControlList":[{"Grant":"private"},null],"ServerSideEncryptionRule":[{       "SSEAlgorithm":"None"},null],"CreationDate":["2020-11-16T06:50:36.000Z",null],"Owner":[
    {"DisplayName":"120886317861****","ID":"120886317861****"},null],"BucketPolicy":[{       "LogPrefix":"","LogBucket":""},null],"StorageClass":["Standard",null], "ExtranetEndpoint":["oss-cn-shanghai.aliyuncs.com",null],"DataRedundancyType":["LRS",null],"AllowEmptyReferer":[
    "true",null],"IntranetEndpoint":["oss-cn-shanghai-internal.aliyuncs.com",null],"Name":[      "test666",null],"Location":["oss-cn-shanghai",null]}",
                "captureTime":1605509680560,
                "resourceCreateTime":1605509436000,
                "resourceId":"test666",
                "resourceName":"test666",
                "resourceType":"ACS::OSS::Bucket",
                "tags":"{}",
                "resourceEventType":"REMOVE",
                "resourceDirectoryId":"rd-EV****"
            }
        ],
        "fileVersion":"1.0"
    }
    ```


## 资源定时配置快照

资源定时配置快照的主要参数说明如下表所示。

|参数|说明|
|--|--|
|accountId|资源所属企业管理账号ID。|
|availabilityZone|资源可用区。|
|regionId|资源所在地域ID。|
|configuration|资源的详细配置。|
|resourceCreateTime|创建资源的时间戳。时间戳转换方法，请参见[Unix时间戳](https://oktools.net/timestamp)。|
|resourceId|资源ID。|
|resourceName|资源名称。|
|resourceType|资源类型。支持的资源类型请参见[支持配置审计的云服务](/cn.zh-CN/产品简介/支持配置审计的云服务.md)。|
|tags|资源标签。|

企业管理账号将对象存储OSS上海地域的存储桶test123的定时配置快照投递到您指定的存储桶中。代码示例如下：

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

