# DescribeConfigurationRecorder

调用DescribeConfigurationRecorder接口查询资源监控范围。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeConfigurationRecorder&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeConfigurationRecorder|要执行的操作，取值：DescribeConfigurationRecorder。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConfigurationRecorder|Struct| |资源监控信息。 |
|AccountId|Long|123456789|当前阿里云账号ID。 |
|ConfigurationRecorderStatus|String|REGISTERED|资源监控状态。取值：

 -   REGISTRABLE：未注册。
-   BUILDING：构建中。
-   REGISTERED：已注册。
-   REBUILDING：重新构建中。 |
|ResourceTypes|List|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|资源类型列表。 |
|RequestId|String|A3601178-A6A2-4636-BE56-1116F73C0B0C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeConfigurationRecorder
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeConfigurationRecorderResponse>
		  <RequestId>A3601178-A6A2-4636-BE56-1116F73C0B0C</RequestId>
		  <ConfigurationRecorder>
			    <ResourceTypes>ACS::ECS::Instance</ResourceTypes>
			    <ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
			    <AccountId>123456789</AccountId>
			    <ConfigurationRecorderStatus>REGISTERED</ConfigurationRecorderStatus>
		  </ConfigurationRecorder>
</DescribeConfigurationRecorderResponse>
```

`JSON`格式

```
{
  "RequestId": "A3601178-A6A2-4636-BE56-1116F73C0B0C",  
  "ConfigurationRecorder": {
    "ResourceTypes": [
      "ACS::ECS::Instance",
      "ACS::ECS::NetworkInterface"
    ],
    "AccountId": "123456789",
    "ConfigurationRecorderStatus": "REGISTERED"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Config)查看更多错误码。

