# GetSupportedResourceTypes

调用GetSupportedResourceTypes接口查询配置审计支持的资源类型列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=GetSupportedResourceTypes&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetSupportedResourceTypes|要执行的操作，取值：**GetSupportedResourceTypes**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ResourceTypes|Array of String|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|资源类型列表。 |
|RequestId|String|6CE4ABA1-9A57-41A9-8EA9-E8B17D4671CD|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetSupportedResourceTypes
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetSupportedResourceTypesResponse>
		<ResourceTypes>ACS::ECS::Instance</ResourceTypes>
		<ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
		<RequestId>3A0D65E8-D5C0-4664-B257-950F7A5E33C3</RequestId>
</GetSupportedResourceTypesResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "ResourceTypes" : [ "ACS::ECS::Instance", "ACS::ECS::NetworkInterface" ],
  "RequestId" : "3A0D65E8-D5C0-4664-B257-950F7A5E33C3"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

