# What is the data structure of functions that can be used to create custom rules?

This topic describes the data structure of functions that can be used to create custom rules. To enable Cloud Config to execute a function of a custom rule, you must create a function with the following data structure in Function Compute:

```
{
  "invokingEvent": {
    "messageType": "ScheduledNotification",
    "notificationCreationTimestamp": 1600610821106,
    "accountId": {The ID of the Alibaba Cloud account that owns the resource},
    "configurationItem": {
      "accountId": {The ID of the Alibaba Cloud account that owns the resource},
      "availabilityZone": "",
      "regionId": "ap-southeast-1",
      "configuration": "{\"UpdateDate\":\"2019-10-21T08:02:58Z\",\"UserName\":\"test123\",\"AccessKeys\":\"AccessKey\":[]},\"UserId\":\"{The ID of the RAM user}\",\"Comments\":\"\",\"DisplayName\":\"test123\",\"CreateDate\":\"2019-10-21T07:57:55Z\",\"LoginProfile\":{\"PasswordResetRequired\":false,\"UserName\":\"test123\",\"MFABindRequired\":false,\"CreateDate\":\"2019-10-21T07:57:55Z\"}}",
      "captureTime": 1600610821106,
      "resourceCreateTime": 1571644675000,
      "resourceId": "20082888873117****",
      "resourceName": "test123",
      "resourceType": "ACS::RAM::User",
      "tags": ""
    }
  },
  "ruleParameters": {
    "dangerousActions": "ecs:*,oss:*,log:*"
  },
  "resultToken": "HLQr3BZx/C+DLjwudFcYdUsiYzW485CJlYIMAAUjibdHcJhG2uvgKZ9tXaFh2yvVUxO2+tFf3whxOmGigYQErk1ymtmLWLzFV4JForVWYIKdbwwhbDBOgVwF7Ov9c3uVCNz/KpxNElwhTzMkZB95U1vmLs4vUYXuB/Txw4jiCYAZuoGWYC/HJwYdSFOHkjAajIswBuzIbX5qFXfwpaqviNDW3I5q8O+Kx7eSYkqqGTYz1ncQdx3sXNSII/TW****"
```

The following table describes the main parameters in the data structure of functions that can be used to create custom rules.

|Parameter|Description|Example|
|---------|-----------|-------|
|accountId|The ID of the Alibaba Cloud account that owns the resource.|169827232854\*\*\*\*|
|regionId|The ID of the region to which the resource belongs.|ap-southeast-1|
|resourceId|The ID of the resource.|20082888873117\*\*\*\*|
|resourceName|The name of the resource.|test123|
|resourceType|The type of the resource.|ACS::RAM::User|
|ruleParameters|The parameters of the rule.|`"dangerousActions": "ecs:*,oss:*,log:*"`|

