# RAM鉴权

在使用RAM用户调用配置审计API前，需要阿里云账号通过创建授权策略对RAM账号进行授权。在授权策略中，使用资源描述符（Alibaba Cloud Resource Name, ARN）指定授权资源。

## ARN格式说明

ARN格式：`acs:config:*:\{AccountId\}:*`

ARN格式中各字段说明如下表所示。

|字段|说明|
|--|--|
|`acs`|Alibaba Cloud Service的首字母缩写，表示阿里云的公共云平台。|
|`config`|配置审计服务名称。|
|`*`|地域信息。配置审计统一使用通配符星号（`*`）来代替。|
|`{AccountId}`|阿里云账号ID，例如：171322098523\*\*\*\*。|
|`*`|具体的资源描述。配置审计统一使用通配符星号（`*`）来代替。|

## RAM鉴权说明

配置审计所有API中可授权的操作（Action）和资源（Resource）的格式如下：

-   Action格式：`config:API名称`
-   Resource格式：``acs:config:${region}:${AccountId}:*``

例如：API为CreateConfigRule，Action为`config:CreateConfigRule`，Resource为`acs:config:${region}:${AccountId}:*`。

