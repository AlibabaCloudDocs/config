# 通过MNS通知机制实现不合规资源的自动修复

当配置审计发现资源配置有变更且不合规时，以事件通知的形式将告警推送到您指定的消息服务MNS主题。当您收到不合规告警时，通过函数计算实现不合规资源的自动修复。

-   请确保您已使用托管规则新建规则。具体操作，请参见[服务授权]()和[新建托管规则](/cn.zh-CN/资源合规审计/管理规则/新建托管规则.md)。
-   请确保您已开通消息服务MNS服务，操作方法请参见[开通消息服务MNS并授权]()。
-   请确保您已开通对象存储OSS服务，且已新建存储空间（Bucket）。具体操作，请参见[开通OSS服务](/cn.zh-CN/控制台用户指南/开通OSS服务.md)和[创建存储空间](/cn.zh-CN/快速入门/控制台快速入门/创建存储空间.md)。
-   请确保您已开通函数计算服务。具体操作，请参见[使用控制台创建函数]()。

## 应用场景

您在配置审计控制台通过托管规则“test-oss-bucket-public-read-prohibited”新建一条资源类型为“OSS存储桶”的规则，配置审计自动审计当前账号下所有OSS存储空间的资源，其中一条资源的合规结果为**不合规**，如下图所示。

![Bucket不合规](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7322085261/p147935.png)

## 数据规划

本文以修复对象存储OSS的存储空间的读写权限为例，为您介绍通过配置审计的MNS通知机制实现不合规资源自动修复的操作方法。相关数据规划如下表所示。

|云服务|参数|示例|
|---|--|--|
|配置审计|托管规则|test-oss-bucket-public-read-prohibited|
|规则名称|test-oss-bucket-public-read-prohibited|
|消息服务|主题名称|MNSTestConfig|
|主题地域|华东2（上海）|
|对象存储OSS|OSS Bucket|config-snapshot|
|Bucket ACL|公共读|
|函数计算|服务|resource\_repair|
|服务的系统模板权限|AliyunOSSFullAccess|
|函数|oss\_repair\_acl\_trigger|
|触发器|ConfigRuleNonComplianceMNSTrigger|

**说明：**

由于配置审计部署在华东2（上海），为了减少网络损耗，建议消息服务MNS的主题地域选择**华东2（上海）**。

## 操作流程

通过配置审计的MNS通知机制实现不合规资源自动修复的操作流程如下图所示。

![修复流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2882559951/p148001.png)

## 操作步骤

1.  登录[配置审计控制台](https://config.console.aliyun.com)，设置资源合规事件投递到消息服务MNS的指定主题（Topic），例如：MNSTestConfig。

    具体操作，请参见[发送资源事件到消息服务MNS](/cn.zh-CN/资源事件/发送资源事件到消息服务MNS.md)。

2.  新建服务。

    1.  登录[函数计算控制台](https://fc.console.aliyun.com)。

    2.  在顶部菜单栏，选择地域，例如：华东2（上海）。

    3.  在左侧导航栏，单击**服务及函数**。

    4.  在**服务列表**区域，单击**新增服务**。

    5.  在**新建服务**页面，**服务名称**输入**resource\_repair**，取消选中**绑定日志**复选框。

    6.  单击**提交**。

3.  授权目标服务修改OSS存储空间的权限。

    1.  在**服务配置**页签，单击**修改配置**。

    2.  在**权限配置**区域，选择已有角色**AliyunFCLogExecutionRole**。

    3.  单击**添加新策略**。

    4.  单击**点击授权**。

    5.  在**添加策略**对话框，选择策略模板为**AliyunOSSFullAccess**。

    6.  单击**RAM配置授权**。

    7.  单击**同意授权**。

    8.  单击**提交**。

4.  新建函数。

    1.  在服务**resource\_repair**页面，单击**新增函数**。

    2.  在**新建函数**页面，鼠标悬浮在**事件函数**区域，单击**配置部署**。

    3.  在**新建函数**页面，**所在服务**选择**resource\_repair**，**函数名称**输入**oss\_repair\_acl\_trigger**，**运行环境**选择**Python 3**，其他参数保持默认值。

    4.  单击**新建**。

5.  配置函数的环境变量。

    1.  在函数**oss\_repair\_acl\_trigger**的**代码执行**页签，单击**概览**页签。

    2.  在**概览**页签的**函数属性**区域，单击**修改配置**。

    3.  在**修改配置**页面，**环境变量**选择**键值**，输入该环境变量的键和值。

        -   **键**为**prepareRuleName**。

            **prepareRuleName**与函数计算自动修复代码中参数**ENV\_RULE\_NAME**的取值保持一致。

        -   **值**为**test-oss-bucket-public-read-prohibited**。

            **test-oss-bucket-public-read-prohibited**为配置审计中的规则名称。

    4.  单击**提交**。

6.  新建触发器。

    1.  在函数**oss\_repair\_acl\_trigger**的**代码执行**页签，单击**触发器**页签。

    2.  在**触发器**页签，单击**创建触发器**。

    3.  在**创建触发器**面板，选择**服务类型**为**MNS主题触发器**。

    4.  设置MNS主题触发器的相关参数。

        参数设置如下：

        -   **触发器名称**输入**ConfigRuleNonComplianceMNSTrigger**。
        -   **MNS Topic所在区域**选择**华东2（上海）**。
        -   **Topic**选择**MNSTestConfig**。
        -   **Event格式**选择**JSON**。
        **说明：** 当您初次使用MNS主题触发器时，如果**角色创建方式**选择**快捷授权**，则在**创建触发器**页面，根据页面提示，为触发器快捷授权角色AliyunMNSNotificationRole后，需要关闭该页面，重新打开，即可看到已授权的服务角色，并根据所需创建触发器。

    5.  单击**确定**。

        新建触发器完成后，当配置审计对目标资源进行评估时，您会接收到该资源的不合规事件通知。

7.  配置自动修复代码。

    1.  在函数**oss\_repair\_acl\_trigger**的**触发器**页签，单击**代码执行**页签。

    2.  在**代码执行**页签的**在线编辑**页面，单击文件**index.py**。

    3.  拷贝并粘贴如下代码至文件**index.py**。

        ```
        # -*- coding: utf-8 -*-
        import logging
        import json
        import os
        import base64
        import binascii
        from aliyunsdkcore.acs_exception.exceptions import ClientException, ServerException
        
        IDENTIFIER = 'evaluationResultIdentifier'
        QUALIFIER = 'evaluationResultQualifier'
        RULE_NAME = 'configRuleName'
        ENV_RULE_NAME = 'prepareRuleName'
        RESOURCE_ID = 'resourceId'
        REGION_ID = 'regionId'
        FAIL = 'fail'
        SUCC = 'success'
        
        logger = logging.getLogger()
        
        
        def handler(event, context):
            logger.info("mns_topic trigger event = {}".format(event))
            decoded = None
            if event:
                try:
                    decoded = base64.b64decode(event)
                except binascii.Error as ex:
                    logger.exception('mns_topic trigger event malformed!')
                    return FAIL
            if not decoded:
                return FAIL
            notify_json = json.loads(decoded)
            if notify_json and IDENTIFIER in notify_json:
                evaluationResultIdentifier = notify_json.get(IDENTIFIER)
                if QUALIFIER in evaluationResultIdentifier and RULE_NAME in evaluationResultIdentifier.get(QUALIFIER):
                    evaluationResultQualifier = evaluationResultIdentifier.get(QUALIFIER)
                    configRuleName = evaluationResultQualifier.get(RULE_NAME)
                    # os.environ.get(ENV_RULE_NAME) 获取您设置的规则名称，例如：test-oss-bucket-public-read-prohibited。
                    if configRuleName == os.environ.get(ENV_RULE_NAME):
                        if RESOURCE_ID in evaluationResultQualifier and REGION_ID in evaluationResultQualifier:
                            bucket_name = evaluationResultQualifier.get(RESOURCE_ID)
                            region = evaluationResultQualifier.get(REGION_ID)
                            if region and bucket_name:
                                try:
                                    remedy_by_fc_assume(context, region, bucket_name)
                                except Exception as ex:
                                    logger.exception('remedy fail!')
            return FAIL
        
        
        def remedy_by_fc_assume(context, region, bucket_name):
            creds = context.credentials
            auth = oss2.StsAuth(creds.access_key_id, creds.access_key_secret, creds.security_token)
            bucket = oss2.Bucket(auth, 'http://oss-' + region + '.aliyuncs.com', bucket_name)
            bucket.put_bucket_acl(oss2.BUCKET_ACL_PRIVATE)
            logger.info('bucket {bucket_name} in {region} acl remedy succ.'.format(bucket_name=bucket_name, region=region))
                                        
        ```

        **说明：** 本段代码以规则名称prepareRuleName为例，为您介绍不合规资源的自动修复方法。如需通过其他参数修复，则请参见[资源不合规事件](/cn.zh-CN/资源事件/事件类型/资源不合规事件.md)。

    4.  在**在线编辑**页面，单击右上角的**部署**。

8.  十分钟后，查看修复结果。

    **说明：** 当资源配置无变更，且审计结果为不合规时，您还需要手动执行审计，然后再执行此步骤。手动执行审计的操作方法，请参见[手动执行审计](/cn.zh-CN/资源合规审计/管理规则/手动执行审计.md)。

    -   通过配置审计控制台查看

        ![OSS Bucket合规](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7322085261/p144367.png)

    -   通过OSS控制台查看

        ![OSS Bucket合规](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3882559951/p146232.png)


