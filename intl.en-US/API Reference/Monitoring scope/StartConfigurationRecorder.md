# StartConfigurationRecorder

Starts recording configurations of the resources you have selected to record in your Alibaba Cloud account.

You can call this operation only by using a master account for Cloud Config for Enterprise or using Cloud Config for individuals. If you use a member account for Cloud Config for Enterprise, the `RDMemberNoPermission` error code will be returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Config&api=StartConfigurationRecorder&type=RPC&version=2019-01-08)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StartConfigurationRecorder|The operation that you want to perform. Set the value to StartConfigurationRecorder. |
|EnterpriseEdition|Boolean|No|false|Specifies whether to use Cloud Config for Enterprise. Valid values:

-   true
-   false: This is the default value. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConfigurationRecorder|Struct| |The details of the configuration recorder. |
|AccountId|Long|123456789|The ID of your Alibaba Cloud account. |
|ConfigurationRecorderStatus|String|REGISTRABLE|The status of the configuration recorder. Valid values:

-   REGISTRABLE: The configuration recorder has not been registered.
-   BUILDING: The configuration recorder is in deployment.
-   REGISTERED: The configuration recorder has been registered.
-   REBUILDING: The configuration recorder is being redeployed. |
|OrganizationEnableStatus|String|REGISTRABLE|Indicates whether Cloud Config for Enterprise is enabled for your enterprise. Valid values:

-   REGISTRABLE: Cloud Config for Enterprise has not been enabled for your enterprise.
-   BUILDING: Cloud Config for Enterprise is in deployment for your enterprise.
-   REGISTERED: Cloud Config for Enterprise is enabled for your enterprise. |
|OrganizationMasterId|Long|123456789|The ID of the master account. After Cloud Config for Enterprise is enabled for your enterprise, if you call the StartConfigurationRecorder operation by using the master account, the system returns the ID of the master account. |
|ResourceTypes|List|\["ACS::ECS::Instance","ACS::ECS::NetworkInterface"\]|The types of resources that are monitored. |
|RequestId|String|A3601178-A6A2-4636-BE56-1116F73C0B0C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=StartConfigurationRecorder
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StartConfigurationRecorderResponse>
          <RequestId>A3601178-A6A2-4636-BE56-1116F73C0B0C</RequestId>
          <ConfigurationRecorder>
                <ResourceTypes>ACS::ECS::Instance</ResourceTypes>
                <ResourceTypes>ACS::ECS::NetworkInterface</ResourceTypes>
                <AccountId>100931896542****</AccountId>
                <ConfigurationRecorderStatus>REGISTRABLE</ConfigurationRecorderStatus>
                <OrganizationEnableStatus>REGISTRABLE</OrganizationEnableStatus>
                <OrganizationMasterId></OrganizationMasterId>
          </ConfigurationRecorder>
</StartConfigurationRecorderResponse>
```

`JSON` format

```
{
  "RequestId": "A3601178-A6A2-4636-BE56-1116F73C0B0C",  
  "ConfigurationRecorder": {
    "ResourceTypes": [
      "ACS::ECS::Instance",
      "ACS::ECS::NetworkInterface"
    ],
    "AccountId": "100931896542****",
    "ConfigurationRecorderStatus": "REGISTRABLE",
    "OrganizationEnableStatus": "REGISTRABLE",
    "OrganizationMasterId": ""
  }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|NoPermission|You are not authorized to perform this operation.|The error message returned because you are not authorized to perform the specified operation.|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|The error message returned because the service is unavailable.|
|404|AccountNotExisted|Your account does not exist.|The error message returned because your account does not exist.|
|500|CreateSLRFail|Failed to create SLR.|The error message returned because the service linked role for Cloud Config failed to be created.|
|400|EnterpriseEditonAlreadyUpgraded|The Enterprise Edition is already upgraded.|The error message returned because Cloud Config for Enterprise has been enabled.|
|400|ProcessIsRunning|The process is running.|The error message returned because the service initialization is in progress.|
|400|RDEnableConfigAccessFail|Failed to enable Config access Resource Directory.|The error message returned because the system failed to access the resource directory when you enable Cloud Config for Enterprise.|
|400|EnterpriseEditionAllResourceTypesDefault|The Enterprise Edition monitor all resource types by default.|The error message returned because Cloud Config for Enterprise monitors all supported types of resources by default and you cannot use a member account to modify the monitoring scope.|
|400|RDMemberNoPermission|You are not authorized to perform the operation. The reasons include: 1. You have not enabled the resource directory service. 2. You are not using the administrator account of resource directory.|The error message returned because you are not authorized to perform the specified operation potentially for one of the following reasons:1. You have not enabled a resource directory.2. You are not using the master account of the specified resource directory.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Config).

