# EIP

本文介绍配置审计为弹性公网IP（EIP）提供的托管规则详情，以及当规则不合规时的修复方法。

## eip\_attached

您可以使用该规则检测弹性公网IP实例是否已绑定到ECS实例或NAT实例。如果弹性公网IP已绑定到ECS或NAT实例，视为“合规”。

触发机制：配置变更

资源：ACS::EIP::EipAddress

参数：无

修复指南：查看您的弹性公网IP是否绑定实例，如果未绑定，则会导致该规则不合规。将弹性公网IP绑定到实例上，绑定的实例类型有ECS实例和NAT实例。配置审计会在10分钟内感知到您的修改并自动启动审计。修复方法如下：

-   控制台

    关于弹性公网IP实例如何绑定ECS实例和NAT网关，请参见[绑定云资源](/intl.zh-CN/用户指南/绑定云资源/绑定云资源.md)。

-   API

    调用AssociateEipAddress接口将弹性公网IP绑定到同地域的云资源上，请参见[AssociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md)。


