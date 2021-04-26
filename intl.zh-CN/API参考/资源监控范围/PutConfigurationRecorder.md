# PutConfigurationRecorder

调用PutConfigurationRecorder接口修改阿里云账号的资源监控范围。

该接口仅对当前请求的阿里云账号有效。关于配置审计支持的资源类型，请参见[支持配置审计的云服务](~~127411~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=PutConfigurationRecorder&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|PutConfigurationRecorder|要执行的操作，取值：PutConfigurationRecorder。 |
|ResourceTypes|String|是|ACS::ECS::Instance,ACS::ECS::Disk|资源类型。多个资源类型之间用半角逗号（,）分隔。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|7C189ED2-30C1-492E-82B6-0D828B556ED9|请求ID。 |
|ConfigurationRecorder|Object| |资源监控信息。 |
|ConfigurationRecorderStatus|String|REGISTERED|资源监控状态。取值：

 -   REGISTRABLE：未注册。
-   BUILDING：构建中。
-   REGISTERED：已注册。
-   REBUILDING：重新构建中。 |
|AccountId|Long|123456789|当前阿里云账号ID。 |
|ResourceTypes|Array of String|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|资源类型列表。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=PutConfigurationRecorder
&ResourceTypes=ACS::ECS::Instance,ACS::ECS::Disk
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<PutConfigurationRecorderResponse>
		<RequestId>7C189ED2-30C1-492E-82B6-0D828B556ED9</RequestId>
		<ConfigurationRecorder>
			<ConfigurationRecorderStatus>REBUILDING</ConfigurationRecorderStatus>
			<ResourceTypes>ACS::ECS::Instance</ResourceTypes>
			<ResourceTypes>ACS::ECS::Disk</ResourceTypes>
			<AccountId>123456789</AccountId>
		</ConfigurationRecorder>
</PutConfigurationRecorderResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "7C189ED2-30C1-492E-82B6-0D828B556ED9",
  "ConfigurationRecorder" : {
    "ConfigurationRecorderStatus" : "REBUILDING",
    "ResourceTypes" : [ "ACS::ECS::Instance", "ACS::ECS::Disk" ],
    "AccountId" : "123456789"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|Invalid.ResourceTypes.Value|The specified resourceTypes is invalid.|输入的资源类型为非法值。|
|400|ProcessIsRunning|The process is running.|进程还在执行中。|
|400|RDMemberNoPermission|You are not authorized to perform the operation. The reasons include: 1. You have not enabled the resource directory service. 2. You are not using the administrator account of resource directory.|您无权进行此操作，原因可能是： 1、您未启用资源目录服务。 2、您使用的不是资源目录的企业管理账号。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

