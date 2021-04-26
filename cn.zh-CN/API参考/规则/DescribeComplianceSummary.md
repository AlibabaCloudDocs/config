# DescribeComplianceSummary

调用DescribeComplianceSummary接口查询合规结果统计概要。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Config&api=DescribeComplianceSummary&type=RPC&version=2019-01-08)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeComplianceSummary|要执行的操作，取值：**DescribeComplianceSummary**。 |
|MultiAccount|Boolean|否|false|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |
|MemberId|Long|否|123456789|该参数计划于2021年06月30日00时00分00秒前下线，其替代功能账号组的API将于2021年05月30日00时00分00秒前上线。如果您正在使用该参数，建议您在2021年05月30日00时00分00秒之后切换为账号组的API。关于账号组，请参见[账号组](~~211534~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CAEE6F34-DEDC-4AAA-AA8C-946D5D008735|请求ID。 |
|ComplianceSummary|Object| |合规结果统计概要。 |
|ComplianceSummaryByResource|Object| |资源维度的合规结果统计概要。 |
|CompliantCount|Integer|1|合规的资源数量。 |
|NonCompliantCount|Integer|12|不合规的资源数量。 |
|ComplianceSummaryTimestamp|Long|1589853712165|合规结果统计的时间戳。 |
|TotalCount|Long|13|资源总数。 |
|ComplianceSummaryByConfigRule|Object| |规则维度的合规结果统计概要。 |
|CompliantCount|Integer|111|合规的规则数量。 |
|NonCompliantCount|Integer|12|不合规的规则数量。 |
|ComplianceSummaryTimestamp|Long|1589853712165|合规结果统计的时间戳。 |
|TotalCount|Long|123|规则总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeComplianceSummary
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeComplianceSummaryResponse>
    <RequestId>CAEE6F34-DEDC-4AAA-AA8C-946D5D008735</RequestId>
    <ComplianceSummary>
        <ComplianceSummaryByResource>
            <CompliantCount>29</CompliantCount>
            <NonCompliantCount>581</NonCompliantCount>
            <ComplianceSummaryTimestamp>1589853712165</ComplianceSummaryTimestamp>
        </ComplianceSummaryByResource>
        <ComplianceSummaryByConfigRule>
            <TotalCount>79</TotalCount>
            <CompliantCount>1</CompliantCount>
            <NonCompliantCount>34</NonCompliantCount>
            <ComplianceSummaryTimestamp>1589853712128</ComplianceSummaryTimestamp>
        </ComplianceSummaryByConfigRule>
    </ComplianceSummary>
    <HttpStatusCode>200</HttpStatusCode>
    <Success>true</Success>
</DescribeComplianceSummaryResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CAEE6F34-DEDC-4AAA-AA8C-946D5D008735",
  "ComplianceSummary" : {
    "ComplianceSummaryByResource" : {
      "CompliantCount" : 29,
      "NonCompliantCount" : 581,
      "ComplianceSummaryTimestamp" : 1589853712165
    },
    "ComplianceSummaryByConfigRule" : {
      "TotalCount" : 79,
      "CompliantCount" : 1,
      "NonCompliantCount" : 34,
      "ComplianceSummaryTimestamp" : 1589853712128
    }
  },
  "HttpStatusCode" : 200,
  "Success" : true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|NoPermission|You are not authorized to perform this operation.|您无权执行此操作。|
|404|AccountNotExisted|Your account does not exist.|您的账号不存在。|
|503|ServiceUnavailable|The request has failed due to a temporary failure of the server.|服务不可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Config)查看更多错误码。

