# ActionTrail

本文介绍配置审计为操作审计提供的托管规则详情，以及当规则不合规时的修复方法。

## actiontrail-enabled

检测您账号是否在操作审计中创建了跟踪，如果未创建，则视为不合规。

触发机制：配置更改

资源：ACS::ActionTrail::Trail

参数：无

修复指南：当跟踪状态为关闭时，会导致该规则不合规。打开**跟踪状态**开关。配置审计会在10分钟内感知到您的修改并自动启动审计。修复方法如下：

-   控制台
    1.  登录[操作审计控制台](https://actiontrail.console.aliyun.com)。
    2.  在左侧导航栏，选择**操作审计** \> **跟踪列表**。
    3.  在**跟踪列表**页面，单击目标跟踪名称链接，打开**跟踪状态**开关。
-   API

    调用StartLogging接口启动跟踪，请参见[StartLogging](/cn.zh-CN/API参考/跟踪相关接口/StartLogging.md)。


