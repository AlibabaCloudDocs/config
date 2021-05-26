# StartConfigurationRecorder

调用StartConfigurationRecorder接口开启配置审计服务并设置资源监控范围。

使用普通账号或企业管理账号调用该接口的差异如下：

-   如果您是普通账号，可以调用该接口为当前账号开启配置审计服务。您可以查看当前账号的资源，并对资源的合规性进行管理。
-   如果您是资源目录的企业管理账号，当`EnterpriseEdition`设置为`true`时，可以调用该接口为所有成员账号开启配置审计服务，且默认创建一个包含所有成员账号的全局账号组。您可以在账号组中查看所有成员账号的资源，并对资源的合规性进行统一管理。

本文将提供一个示例，使用普通账号开启配置审计服务并监控当前账号的资源。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=StartConfigurationRecorder&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartConfigurationRecorder|要执行的操作，取值：StartConfigurationRecorder。 |
|EnterpriseEdition|Boolean|否|false|是否升级企业版配置审计。取值：

 -   true
-   false（默认值）

 **说明：** 企业版配置审计升级为账号组。更多信息，请参见[公告：企业版配置审计升级为账号组](213433)。 |

关于公共请求参数的详情，请参见[公共参数](~~169575~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A3601178-A6A2-4636-BE56-1116F73C0B0C|请求ID。 |
|ConfigurationRecorder|Object| |资源监控信息。 |
|OrganizationEnableStatus|String|REGISTRABLE|企业版配置审计升级状态。取值：

 -   REGISTRABLE：未升级。
-   BUILDING：升级中。
-   REGISTERED：已升级。 |
|ConfigurationRecorderStatus|String|REGISTRABLE|资源监控状态。取值：

 -   REGISTRABLE：未注册。
-   BUILDING：构建中。
-   REGISTERED：已注册。
-   REBUILDING：重新构建中。 |
|OrganizationMasterId|Long|987654321|企业管理账号ID。

 **说明：** 仅当企业管理账号调用该接口时，返回该参数。 |
|AccountId|Long|123456789|阿里云账号ID。

 **说明：** 仅当普通账号调用该接口时，返回该参数。 |
|ResourceTypes|Array of String|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|资源类型列表。

 **说明：** 配置审计默认返回全部资源类型，返回示例仅以资源类型`ACS::ECS::Instance`和`ACS::ECS::NetworkInterface`为例进行展示。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=StartConfigurationRecorder
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<StartConfigurationRecorderResponse>
		<RequestId>A3601178-A6A2-4636-BE56-1116F73C0B0C</RequestId>
		<ConfigurationRecorder>
			<ResourceTypes>ACS::ECS::Instance</ResourceTypes>
			<ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
			<AccountId>123456789</AccountId>
			<ConfigurationRecorderStatus>REGISTRABLE</ConfigurationRecorderStatus>
		</ConfigurationRecorder>
</StartConfigurationRecorderResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "A3601178-A6A2-4636-BE56-1116F73C0B0C",
  "ConfigurationRecorder" : {
    "ResourceTypes" : [ "ACS::ECS::Instance", "ACS::ECS::NetworkInterface" ],
    "AccountId" : "123456789",
    "ConfigurationRecorderStatus" : "REGISTRABLE"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|400|ProcessIsRunning|The process is running.|进程还在执行中。|
|400|RDMemberNoPermission|You are not authorized to perform the operation. The reasons include: 1. You have not enabled the resource directory service. 2. You are not using the administrator account of resource directory.|您无权进行此操作，原因可能是： 1、您未启用资源目录服务。 2、您使用的不是资源目录的企业管理账号。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|500|CreateSLRFail|Failed to create SLR.|创建角色失败。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

