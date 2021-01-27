# ActionTrail event log reference

This topic describes the key fields of an event log with examples.

## Key fields of an event log

|Field|Type|Required|Example|Description|
|-----|----|--------|-------|-----------|
|acsRegion|String|Yes|cn-hangzhou|The ID of the region where the event log was recorded.|
|apiVersion|String|No|2014-05-26|The version of the API operation that was called. If eventType is set to ApiCall, the event log records an API operation.|
|eventId|String|Yes|F23A3DD5-7842-4EF9-9DA1-3776396A\*\*\*\*|The ID of the event log. ActionTrail generates a globally unique identifier \(GUID\) for each event log.|
|eventName|String|Yes|CreateNetworkInterface|The name of the event log. -   If eventType is set to ApiCall, this field is set to the name of the API operation that was called.
-   If eventType is not set to ApiCall, this field is set to a string that indicates the action recorded in the event log. |
|eventSource|String|Yes|ecs.aliyuncs.com|The source of the event log.|
|eventTime|String|Yes|2020-01-09T12:12:14Z|The time when the event log was recorded, in UTC.|
|eventType|String|Yes|ApiCall|The type of the action that was recorded in the event log. Valid values: -   ApiCall: indicates that an API operation was called. Most consoles of Alibaba Cloud services are developed based on the OpenAPI specification. If an action was performed in these consoles, ActionTrail records the action as ApiCall.
-   ConsoleOperation \(ConsoleCall\): indicates that an action was performed in specific consoles or on buy pages of some Alibaba Cloud services. These consoles or buy pages are not developed based on the OpenAPI specification. If an action was performed in this type of console or on a buy page, ActionTrail records this action as ConsoleOperation or ConsoleCall. For this type of action, the value of eventName can be the name of the API operation that was called or a string that indicates the action.
-   AliyunServiceEvent: indicates that Alibaba Cloud performed an action on your resources. For example, Alibaba Cloud released a subscription instance upon expiration.
-   PasswordReset: indicates that your password was reset.
-   ConsoleSignin: indicates a logon to a console.
-   ConsoleSignout: indicates a logoff from a console. |
|eventVersion|String|Yes|1|The version of the event log format. The current version is 1.|
|errorCode|String|No|NoPermission|The error code returned if an error occurred during the processing of an API request. ·|
|errorMessage|String|No|You are not authorized.|The error message returned if an error occurred during the processing of the API request.|
|requestId|String|Yes|F23A3DD5-7842-4EF9-9DA1-3776396AD58D|The ID of the API request.|
|requestParameters|Dictionary|No|N/A|The parameters specified in the API request.|
|responseElements|Dictionary|No|N/A|The response returned for the API request.|
|referencedResources|Dictionary|No|N/A|The list of resources that the action recorded in the event log involves.|
|serviceName|String|Yes|Ecs|The name of the Alibaba Cloud service to which the event log belongs.|
|sourceIpAddress|String|Yes|11.168.XX.XX|The IP address from which the event log was recorded.|
|userAgent|String|Yes|Apache-HttpClient/4.5.7 \(Java/1.8.0\_152\)|The agent by which the API request was sent. Valid values: -   AlibabaCloud \(Linux 3.10.0-693.2.2.el7.x86\_64;x86\_64\) Python/2.7.5 Core/2.13.16 python-requests/2.18.3
-   Apache-HttpClient/4.5.7 \(Java/1.8.0\_152\) |
|userIdentity|Dictionary|Yes|N/A|The identity information about the requester.|

The following table describes the fields that userIdentity contains.

|Field|Type|Required|Example|Description|
|-----|----|--------|-------|-----------|
|type|String|Yes|ram-user|The type of the identity. Valid values: -   root-account: indicates an Alibaba Cloud account.
-   ram-user: indicates a RAM user.
-   assumed-role: indicates a RAM role.
-   system: indicates an Alibaba Cloud service. |
|principalId|String|Yes|28815334868278\*\*\*\*|The ID of the requester. -   If type is set to root-account, this field is set to the ID of the Alibaba Cloud account.
-   If type is set to ram-user, this field is set to the ID of the RAM user.
-   If type is set to assumed-role, this field is set to a string in the RoleID:RoleSessionName format. |
|accountId|String|Yes|112233445566\*\*\*\*|The ID of the Alibaba Cloud account.|
|accessKeyId|String|No|55nCtAwmPLkk\*\*\*\*|-   The AccessKey ID that is used by the requester. If the requester made the API request by using an SDK, this field is recorded.
-   If the requester logged on to the Alibaba Cloud Management Console, this field is not recorded. |
|userName|String|No|B\*\*|-   The name of the requester. If type is set to ram-user, this field is set to the name of the RAM user.
-   If type is set to assumed-role, this field is set to a string in the RoleName:RoleSessionName format. |
|sessionContext|String|No|\{"attributes": \{"mfaAuthenticated": "true", "creationDate": "2015-12-31T06:33:14Z" \}|The session context recorded when the requester called an API operation by using a Security Token Service \(STS\) token or logged on to the Alibaba Cloud Management Console. The session context contains the following attributes: -   `creationDate`: indicates the time when the STS token was created.
-   `mfaAuthenticated`: indicates whether multi-factor authentication was used for logging on to the Alibaba Cloud Management Console. |

## Example

```
{
  "eventId": "F23A3DD5-7842-4EF9-9DA1-3776396A****",
  "responseElements": {
    "RequestId": "F23A3DD5-7842-4EF9-9DA1-3776396AD58D",
    "NetworkInterfaceId": "eni-bp12f9rjbjqauktz****"
  },
  "eventVersion": "1",
  "requestParameters": {
    "Tag.1.Key": "CreatedBy",
    "RequestId": "F23A3DD5-7842-4EF9-9DA1-3776396AD58D",
    "SecurityGroupId": "sg-bp10mvd8143rlfks****",
    "Tag.1.Value": "StreamCompute",
    "VSwitchId": "vsw-bp1iqqmaj41noh2c8****",
    "RegionId": "cn-hangzhou",
    "SignatureType": "",
    "stsTokenPlayerUid": 165266556947****
  },
  "eventSource": "ecs.aliyuncs.com",
  "sourceIpAddress": "11.168.XX.XX",
  "userIdentity": {
    "sessionContext": {
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "2020-01-09T12:12:14Z"
      }
    },
    "accessKeyId": "STS.NUnj6nuqKaEoMZGsT****",
    "accountId": "116214825062****",
    "principalId": "31645666448606****:116214825062****",
    "userName": "aliyunstreamdefaultrole:116214825062****",
    "type": "assumed-role"
  },
  "eventType": "ApiCall",
  "referencedResources": {
    "VSwitch": [
      "vsw-bp1iqqma1noh402c8****"
    ],
    "SecurityGroup": [
      "sg-bp10mvd143r6lfks****"
    ]
  },
  "serviceName": "Ecs",
  "additionalEventData": {
    "Scheme": "http"
  },
  "apiVersion": "2014-05-26",
  "requestId": "F23A3DD5-7842-4EF9-9DA1-3776396AD58D",
  "eventTime": "2020-01-09T12:12:14Z",
  "acsRegion": "cn-hangzhou",
  "eventName": "CreateNetworkInterface",
  "__expanded": true
}
```

