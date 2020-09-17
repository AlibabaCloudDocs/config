# Make API requests

To send a Cloud Config API request, you must send an HTTP GET request to the Cloud Config endpoint. You must add the request parameters that correspond to the API operation being called. After you call the API operation, the system returns a response. The request and response are encoded in UTF-8.

## Request structure

Cloud Config API operations use the RPC protocol. You can call Cloud Config API operations by sending HTTP GET requests.

The request syntax is as follows:

```
http://Endpoint/?Action=xx&Parameters
```

The following table describes the parameters in the request syntax.

|Parameter|Description|
|---------|-----------|
|Endpoint|The endpoint of the Cloud Config API. Set the value to config.ap-southeast-1.aliyuncs.com.|
|Action|The name of the operation being performed. For example, to query the configuration of a resource, you must set the Action parameter to DescribeDiscoveredResource.|
|Version|The version number of the API. Set the value to 2019-01-08.|
|Parameters|The request parameters for the operation. Separate multiple parameters with ampersands \(&\). Request parameters include both common parameters and operation-specific parameters. Common parameters include the API version and authentication information. For more information, see [Common parameters](/intl.en-US/API Reference/Common parameters.md). |

## Sample requests

The following example demonstrates how to call the DescribeDiscoveredResource operation to query the configuration of a resource:

**Note:** The following code has been formatted to ease reading.

```
https://config.ap-southeast-1.aliyuncs.com/?Action=DescribeDiscoveredResource
&Format=xml
&Version=2019-01-08
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&TimeStamp=2020-05-01T12:00:00Z
...
```

