# StartConfigurationRecorder

Enables Cloud Config to monitor the resources of your Alibaba Cloud account.

Ordinary accounts and management accounts have the following differences when you use them to call the StartConfigurationRecorder operation:

-   If you are using an ordinary account, you can call the StartConfigurationRecorder operation to activate Cloud Config for the current account. You can also view the resources of the current account and manage the compliance rules of the current account.
-   If you are using the management account of a resource directory and set the `EnterpriseEdition` parameter to `true`, you can activate Cloud Config for all member accounts. In addition, a global account group that includes all member accounts is created by default. You can view the resources of all member accounts in the account group and manage the compliance rules of all member accounts.

In this topic, an ordinary account is used as an example to show how to activate Cloud Config and monitor the resources of the current account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=StartConfigurationRecorder&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StartConfigurationRecorder|The operation that you want to perform. Set the value to StartConfigurationRecorder. |
|EnterpriseEdition|Boolean|No|false|Specifies whether to upgrade Cloud Config for Enterprise. Default value: false. Valid values:

-   true
-   false

**Note:** Cloud Config for Enterprise is upgraded to the account group feature. For more information, see [Announcement: Enterprise Edition Cloud Config Upgrade to Account Group](~~213433~~). |

For more information about common request parameters, see [Common parameters](~~169575~~).

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A3601178-A6A2-4636-BE56-1116F73C0B0C|The ID of the request. |
|ConfigurationRecorder|Object| |The details of the configuration recorder that monitors resources. |
|OrganizationEnableStatus|String|REGISTRABLE|The upgrade status of Cloud Config for Enterprise. Valid values:

-   REGISTRABLE: Cloud Config for Enterprise is not upgraded.
-   BUILDING: Cloud Config for Enterprise is being upgraded.
-   REGISTERED: Cloud Config for Enterprise is upgraded. |
|ConfigurationRecorderStatus|String|REGISTRABLE|The status of the configuration recorder. Valid values:

-   REGISTRABLE: The configuration recorder has not been registered.
-   BUILDING: The configuration recorder is being deployed.
-   REGISTERED: The configuration recorder has been registered.
-   REBUILDING: The configuration recorder is being redeployed. |
|OrganizationMasterId|Long|987654321|The ID of the management account.

**Note:** This parameter is returned only when the operation was called by a management account. |
|AccountId|Long|123456789|The ID of your Alibaba Cloud account.

**Note:** This parameter is returned only when the operation was called by an ordinary account. |
|ResourceTypes|Array of String|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|The types of resources that are monitored by Cloud Config.

**Note:** By default, Cloud Config returns all resource types. In the following sample responses, `ACS::ECS::Instance` and `ACS::ECS::NetworkInterface` are returned. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=StartConfigurationRecorder
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|400|ProcessIsRunning|The process is running.|The error message returned because the service initialization is in progress.|
|400|RDMemberNoPermission|You are not authorized to perform the operation. The reasons include: 1. You have not enabled the resource directory service. 2. You are not using the administrator account of resource directory.|The error message returned because you are not authorized to perform the specified operation potentially for one of the following reasons:1. You have not enabled a resource directory. 2. You are not using the master account of the specified resource directory.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|500|CreateSLRFail|Failed to create SLR.|The error message returned because the service-linked role of Cloud Config failed to be created.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

