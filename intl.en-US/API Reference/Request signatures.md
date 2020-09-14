# Request signatures

You must sign all API requests to ensure security. Alibaba Cloud uses the request signature to verify the identity of the API caller. Therefore, each API request must contain signature information, regardless of whether it is sent by using HTTP or HTTPS.

## Overview

You must add the signature to the Resource Management API request in the following format:

```
https://Endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

where:

-   SignatureMethod: the encryption method of the signature string. Set the value to HMAC-SHA1.
-   SignatureVersion: the version of the signature encryption algorithm. Set the value to 1.0.
-   SignatureNonce: a unique, random number used to prevent replay attacks. You must use different numbers for different requests. We recommend that you use universally unique identifiers \(UUIDs\).
-   Signature: the signature generated after the request has been symmetrically encrypted by using the AccessKey secret.

The signature encryption algorithm complies with RFC 2104 HMAC-SHA1 specifications. The AccessKey secret is used to calculate the hash-based message authentication code \(HMAC\) value of the encoded and sorted query string, and the HMAC value is used as the signature string. Request signatures include operation-specific parameters. Therefore, the signature of a request varies depending on the request parameters. To calculate a signature, follow the steps in this topic.

```
Signature = Base64( HMAC-SHA1( AccessSecret, UTF-8-Encoding-Of(StringToSign)) )
```

## Step 1: Compose and encode a string-to-sign

1.  Use request parameters to construct a canonicalized query string.
    1.  Create a canonicalized query string by arranging the request parameters \(including all common and operation-specific parameters except Signature\) in alphabetical order.

        **Note:** If you use the GET method to submit the request, these parameters are the part located after the question mark \(?\) and connected by the ampersands \(&\) in the request uniform resource identifier \(URI\).

    2.  Encode the canonicalized query string in UTF-8. The following table describes the encoding rules.

        |Character|Encoding rule|
        |---------|-------------|
        |A to Z, a to z, 0 to 9, hyphens \(-\), underscores \(\_\), periods \(.\), and tildes \(~\)|These characters do not need to be encoded.|
        |Other characters|These characters must be percent encoded in `%XY` format. `XY` represents the ASCII code of the characters in hexadecimal notation. For example, double quotation marks \("\) are encoded as `%22`.|
        |Extended UTF-8 characters|These characters are encoded in `%XY%ZA...` format.|
        |Spaces|Spaces must be encoded as `%20`. Do not encode spaces as plus signs \(+\). This encoding method is different from the `application/x-www-form-urlencoded` MIME encoding algorithm \(such as the `java.net.URLEncoder` class provided by the Java standard library\). However, you can apply the encoding algorithm and then replace the plus sign \(+\) in the encoded string with `%20`, the asterisk \(\*\) with `%2A`, and `%7E` with the tilde \(~\). To do this, you can use the following `percentEncode` method:

        ```
private static final String ENCODING = "UTF-8";
private static String percentEncode(String value) throws UnsupportedEncodingException 
{
return value ! = null ? URLEncoder.encode(value, ENCODING).replace("+", "%20").replace("*", "%2A").replace("%7E", "~") : null;
}
        ``` |

    3.  Connect the encoded parameter names and values by using equal signs \(=\).
    4.  Sort the connected parameter name and value pairs in the order specified in step i and connect the pairs by using ampersands \(&\) to obtain the canonicalized query string.
2.  Create a string-to-sign from the encoded canonicalized query string as follows:

    ```
    StringToSign=
          HTTPMethod + "&" +
          percentEncode("/") + "&" +
           percentEncode(CanonicalizedQueryString)
    ```

    where:

    -   HTTPMethod: the HTTP method used to make the request, such as GET.
    -   percentEncode\("/"\): Encode backslashes \(/\) as %2F according to the URL encoding rule described in step 1.1.
    -   percentEncode\(CanonicalizedQueryString\): Encode the canonicalized query string based on the URL encoding rule described in step 1.2.

## Step 2: Calculate the signature

1.  Calculate the HMAC value of the string-to-sign based on RFC 2104.

    **Note:** Use the SHA1 algorithm to calculate the HMAC value of the string-to-sign. The combination of your AccessKey secret and an ampersand \(&\) \(ASCII code 38\) that follows the secret is used as the key for the HMAC calculation.

2.  Encode the HMAC value in Base64 to obtain the signature string.
3.  Add the signature string to the request as the Signature parameter.

    **Note:** When the obtained signature value is submitted as the final request parameter value, the value must be URL-encoded like other parameters based on rules defined in [RFC 3986](https://tools.ietf.org/html/rfc3986).


## Signature example

Take a DescribeDiscoveredResource API request as an example, where the following sample request URL is to be signed:

```
http://config.cn-shanghai.aliyuncs.com/?AccessKeyId=testid&Action=DescribeDiscoveredResource&Format=JSON&Region=cn-shanghai&RegionId=cn-shanghai&ResourceId=i-uf6hm9lnlzsarrc7****&ResourceType=ACS%3A%3AECS%3A%3AInstance&SignatureMethod=HMAC-SHA1&SignatureNonce=b9942750-e6a8-11ea-b411-73ba779dcf0c&SignatureVersion=1.0&Timestamp=2020-08-25T07%3A58%3A13Z&Version=2019-01-08
```

The following string is the `string-to-sign`:

```
GET&%2F&AccessKeyId%3Dtestid%26Action%3DDescribeDiscoveredResource%26Format%3DJSON%26Region%3Dcn-shanghai%26RegionId%3Dcn-shanghai%26ResourceId%3Di-uf6hm9lnlzsarrc7****%26ResourceType%3DACS%25253A%25253AECS%25253A%25253AInstance%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3Db9942750-e6a8-11ea-b411-73ba779dcf0c%26SignatureVersion%3D1.0%26Timestamp%3D2020-08-25T07%25253A58%25253A13Z%26Version%3D2019-01-08
```

Assume that the AccessKey ID is testid and the AccessKey secret is testsecret. The key that is used to calculate the HMAC value of the string-to-sign is testsecret&.

The calculated signature string is `i+JJvbbP6iDAXEUOP6pTnRSCewc=`.

In this example, the following signed request URL is generated:

```
http://config.cn-shanghai.aliyuncs.com/?Signature=i+JJvbbP6iDAXEUOP6pTnRSCewc=&AccessKeyId=testid&Action=DescribeDiscoveredResource&Format=JSON&Region=cn-shanghai&RegionId=cn-shanghai&ResourceId=i-uf6hm9lnlzsarrc7****&ResourceType=ACS%3A%3AECS%3A%3AInstance&SignatureMethod=HMAC-SHA1&SignatureNonce=b9942750-e6a8-11ea-b411-73ba779dcf0c&SignatureVersion=1.0&Timestamp=2020-08-25T07%3A58%3A13Z&Version=2019-01-08
```

