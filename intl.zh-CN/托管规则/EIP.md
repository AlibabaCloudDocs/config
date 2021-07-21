# EIP

检测您账号下的弹性公网IP（EIP）是否绑定云资源。当您账号下的弹性公网IP未绑定云资源时，会导致该规则不合规。弹性公网IP绑定的云资源类型有：ECS实例、NAT网关、SLB实例和辅助弹性网卡。

## 规则说明

|参数|说明|
|--|--|
|规则名称|eip-attached|
|触发机制|配置变更|
|监控的资源类型|ACS::EIP::EipAddress|
|规则入参名称|无|
|规则介绍|检测您账号下的弹性公网IP是否绑定云资源。如果绑定云资源视为“合规”；反之，视为“不合规”。|

## 改进建议

-   控制台

    关于如何绑定ECS实例、NAT网关、SLB实例和弹性网卡，请参见[绑定云资源](/intl.zh-CN/用户指南/绑定云资源/绑定云资源.md)。

-   API

    调用AssociateEipAddress接口将弹性公网IP绑定到同地域的云资源上。更多信息，请参见[AssociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md)。


