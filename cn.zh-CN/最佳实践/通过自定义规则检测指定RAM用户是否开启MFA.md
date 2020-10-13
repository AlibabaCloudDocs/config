# 通过自定义规则检测指定RAM用户是否开启MFA

当您通过RAM用户管理资源时，需要为其授权部分高风险操作。为了提升RAM用户的登录安全，您需要开启多因素认证（MFA）。由于配置审计提供的托管规则用于检测所有RAM用户是否开启MFA，不能满足仅检测高风险操作的RAM用户的需求，因此您需要通过自定义规则检测指定RAM用户是否开启MFA。

-   请确保您已开通消息服务MNS服务，操作方法请参见[开通MNS服务]()。
-   请确保您已开通函数计算服务，操作方法请参见[开通函数计算服务]()。

## 示例说明

本文假设某RAM用户拥有高风险的系统权限AliyunECSFullAccess（管理云服务器ECS的权限）。在下面示例中，我们将新建自定义规则，检测该用户是否开启了MFA。

## 数据规划

数据规划如下表所示。

|云服务|参数|示例|
|---|--|--|
|配置审计|规则名称|RAMUserMFA|
|规则触发机制|周期执行|
|触发频率|1小时|
|规则入参名称|dangerousActions|
|阈值|ecs:\*,oss:\*,log:\*|
|消息服务|主题名称|MNSTestConfig|
|主题地域|华东2（上海）**说明：**

由于配置审计部署在华东2（上海），为了减少网络损耗，建议消息服务MNS的主题地域选择**华东2（上海）**。 |
|访问控制|RAM用户|test123@169827232854\*\*\*\*.onaliyun.com|
|默认权限策略|AliyunECSFullAccess|
|函数计算|服务|Ram\_User|
|函数|RamDangerousPolicyUserBindMFA|

## 操作流程

操作流程如下图所示。

![操作流程](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8267942061/p171675.png)

## 操作步骤

1.  新建服务。

    1.  登录[函数计算控制台](https://fc.console.aliyun.com)。

    2.  在顶部菜单栏，选择地域，例如：华东2（上海）。

    3.  在左侧导航栏，选择**服务/函数**。

    4.  从下拉列表中选择**新建服务**。

    5.  在**新建服务**页面，**服务名称**输入**Ram\_User**。

    6.  单击**创建**。

2.  新建函数。

    1.  在**服务/函数**页面，单击**新建函数**。

    2.  在**创建函数**页面，选择**创建方式**为**事件函数**，单击**下一步**。

    3.  在**配置函数**页面，**所在服务**选择**Ram\_User**，**函数名称**输入**RamDangerousPolicyUserBindMFA**，**运行环境**选择**python3**，其他参数保持默认值。

        ![新建函数](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2412322061/p171239.png)

    4.  单击**完成**。

3.  配置函数的环境变量。

    1.  在左侧导航栏，选择**服务/函数**。

    2.  在目标服务的**函数列表**页签，单击目标函数名称对应的链接。

    3.  在目标函数**概览**页签的**函数属性**区域，单击**配置**。

    4.  在**配置函数**页面，配置该函数的环境变量。

        |键|值|示例|
        |--|--|--|
        |AK|当前阿里云账号的AccessKey ID，请参见[获取AccessKey]()。|LTAI4G6JZSANb8MZMkm1\*\*\*\*|
        |SK|当前阿里云账号的AccessKey Secret，请参见[获取AccessKey]()。|EMLHThhpD2UJqH1DXuAKii2sI\*\*\*\*|
        |ResourceTypes|资源类型。|ACS::RAM::User|

    5.  单击**提交**。

4.  配置检测RAM用户是否开启MFA的代码。

    1.  在左侧导航栏，选择**服务/函数**。

    2.  在目标服务的**函数列表**页签，单击目标函数名称对应的链接。

    3.  在目标函数的管理页面，单击**代码执行**页签。

    4.  在**代码执行**页签，选择**在线编辑**，拷贝并粘贴如下代码。

        ```
        #!/usr/bin/env python
        # -*- encoding: utf-8 -*-
        
        import logging
        import json
        import os
        from aliyunsdkcore.client import AcsClient
        from aliyunsdkram.request.v20150501 import ListPoliciesForUserRequest
        from aliyunsdkram.request.v20150501 import GetPolicyRequest
        from aliyunsdkram.request.v20150501 import GetUserMFAInfoRequest
        from aliyunsdkcore.auth.credentials import StsTokenCredential
        from aliyunsdkcore.acs_exception.exceptions import ClientException
        from aliyunsdkcore.acs_exception.exceptions import ServerException
        from aliyunsdkcore.request import CommonRequest
        
        logger = logging.getLogger()
        
        # Matched resource types
        MATCH_RESOURCE_TYPES = os.environ.get('resourceTypes')
        
        # AccessKey/SecretKey, need AliyunConfigFullAccess policy
        AK = os.environ.get('AK')
        SK = os.environ.get('SK')
        
        # Valid compliace type
        COMPLIACE_TYPE_COMPLIANT = 'COMPLIANT'
        COMPLIACE_TYPE_NON_COMPLIANT = 'NON_COMPLIANT'
        COMPLIACE_TYPE_NOT_APPLICABLE = 'NOT_APPLICABLE'
        COMPLIACE_TYPE_INSUFFICIENT_DATA = 'INSUFFICIENT_DATA'
        
        
        def handler(event, context):
            # Validate event
            evt = validate_event(event)
            if not evt:
                return None
        
            rule_parameters = evt.get('ruleParameters')
            result_token = evt.get('resultToken')
            invoking_event = evt.get('invokingEvent')
        
            # Initilize
            compliance_type = COMPLIACE_TYPE_NOT_APPLICABLE
            annotation = None
        
            # Get configuration item
            configuration_item = invoking_event.get('configurationItem')
            if not configuration_item:
                logger.error('Configuration item is empty.')
                return None
        
            ordering_timestamp = configuration_item.get('captureTime')
            resource_id = configuration_item.get('resourceId')
            resource_type = configuration_item.get('resourceType')
        
            creds = context.credentials
            # Get compliace result
            compliance_type, annotation = evaluate_configuration_item(rule_parameters, configuration_item, creds)
        
            # Compliance result
            evaluations = [
                {
                    'complianceResourceId': resource_id,
                    'complianceResourceType': resource_type,
                    'orderingTimestamp': ordering_timestamp,
                    'complianceType': compliance_type,
                    'annotation': annotation
                }
            ]
        
            # Put evaluation result by invoking open api
            put_evaluations(context, result_token, evaluations)
        
            return evaluations
        
        
        def evaluate_configuration_item(rule_parameters, configuration_item, creds):
            # Initilize
            compliance_type = COMPLIACE_TYPE_NOT_APPLICABLE
            annotation = None
        
            # Get resource type and configuration
            resource_type = configuration_item['resourceType']
            full_configuration = configuration_item['configuration']
        
            # Check resource type
            if MATCH_RESOURCE_TYPES and resource_type not in MATCH_RESOURCE_TYPES.split(','):
                annotation = 'Resource type is {}, not in {}.'.format(
                    resource_type, MATCH_RESOURCE_TYPES)
                return compliance_type, annotation
        
            # Check configuration
            if not full_configuration:
                annotation = 'Configuration is empty.'
                return compliance_type, annotation
        
            # Parse to json object
            configuration = parse_json(full_configuration)
            if not configuration:
                annotation = 'Configuration:{} in invald.'.format(full_configuration)
                return compliance_type, annotation
        
            # =========== Customer code start =========== #
            if 'UserName' in configuration and configuration['UserName']:
                user_name = configuration['UserName']
                if rule_parameters and 'dangerousActions' in rule_parameters and rule_parameters['dangerousActions']:
                    actions = rule_parameters['dangerousActions'].split(',')
                    isvalid, reason = validate_user_bind_MFADevice(user_name, actions,
                                                                                 'only_custom' in rule_parameters and
                                                                   rule_parameters['only_custom'] == 'true')
                    if isvalid:
                        compliance_type, annotation = COMPLIACE_TYPE_COMPLIANT, None
                    else:
                        compliance_type, annotation = COMPLIACE_TYPE_NON_COMPLIANT, reason
                else:
                    compliance_type, annotation = COMPLIACE_TYPE_COMPLIANT, 'rule parameter:{dangerousActions} not specified'
            else:
                compliance_type, annotation = COMPLIACE_TYPE_INSUFFICIENT_DATA, 'ram user not named'
        
            # =========== Customer code end =========== #
        
            return compliance_type, annotation
        
        
        def validate_user_bind_MFADevice(user_name, input_actions, only_custom):
            client = AcsClient(AK, SK)
            list_user_policy_req = ListPoliciesForUserRequest.ListPoliciesForUserRequest()
            list_user_policy_req.set_UserName(user_name)
            list_user_policy_res = None
            try:
                list_user_policy_res = client.do_action_with_exception(list_user_policy_req)
            except ServerException as se:
                if se.get_http_status() == 404 and se.get_error_code() == 'EntityNotExist.User':
                    return True, None
                else:
                    return False, se.get_error_msg()
            if list_user_policy_res is None:
                return True, None
            list_user_policy_json_res = json.loads(list_user_policy_res)
            user_policies = None
            try:
                user_policies = list(filter(lambda x: x['PolicyType'] == 'Custom',
                                            list_user_policy_json_res['Policies']['Policy'])) if only_custom else \
                    list_user_policy_json_res['Policies']['Policy']
            except Exception as ex:
                return True, None
            if user_policies is None or len(user_policies) == 0:
                return True, None
            policy_action_list = list()
            for policy in user_policies:
                get_policy_req = GetPolicyRequest.GetPolicyRequest()
                get_policy_req.set_PolicyName(policy['PolicyName'])
                get_policy_req.set_PolicyType(policy['PolicyType'])
                get_policy_res = None
                try:
                    get_policy_res = client.do_action_with_exception(get_policy_req)
                    policy_document = json.loads(json.loads(get_policy_res)['DefaultPolicyVersion']['PolicyDocument'])
                    for action in list(map(lambda x: x['Action'],
                                           list(filter(lambda x: x['Effect'] == 'Allow', policy_document['Statement'])))):
                        if type(action) is list:
                            policy_action_list.extend(action)
                        else:
                            policy_action_list.append(action)
                except ServerException as se:
                    logger.error(se)
                except Exception as ex:
                    logger.error(ex)
            policy_action_set = set(policy_action_list)
            if policy_action_set.intersection(set(input_actions)):
                get_user_mfa_req = GetUserMFAInfoRequest.GetUserMFAInfoRequest()
                get_user_mfa_req.set_UserName(user_name)
                get_user_mfa_res = None
                try:
                    get_user_mfa_res = client.do_action_with_exception(get_user_mfa_req)
                    if ('SerialNumber' not in get_user_mfa_res) or ('MFADevice' not in get_user_mfa_res):
                        return False, 'user MFADevice empty'
                    else:
                        return True, None
                except ServerException as se:
                    return False, se.get_error_msg()
            else:
                return True, None
        
        
        def validate_event(event):
            if not event:
                logger.error('Event is empty.')
        
            evt = parse_json(event)
            logger.info('Loading event: %s .' % evt)
        
            if 'resultToken' not in evt:
                logger.error('ResultToken is empty.')
                return None
        
            if 'ruleParameters' not in evt:
                logger.error('RuleParameters is empty.')
                return None
        
            if 'invokingEvent' not in evt:
                logger.error('InvokingEvent is empty.')
                return None
        
            return evt
        
        
        def parse_json(content):
            try:
                return json.loads(content)
            except Exception as e:
                logger.error('Parse content:{} to json error:{}.'.format(content, e))
                return None
        
        
        def put_evaluations(context, result_token, evaluations):
            # ak/sk, need AliyunConfigFullAccess policy
            client = AcsClient(AK, SK, 'cn-shanghai')
        
            # Open api request
            request = CommonRequest()
            request.set_domain('config.cn-shanghai.aliyuncs.com')
            request.set_version('2019-01-08')
            request.set_action_name('PutEvaluations')
            request.add_body_params('ResultToken', result_token)
            request.add_body_params('Evaluations', evaluations)
            request.set_method('POST')
        
            try:
                response = client.do_action_with_exception(request)
                logger.info('PutEvaluations with request: {}, response: {}.'.format(request, response))
            except Exception as e:
                logger.error('PutEvaluations error: %s' % e)
        ```

        本段代码用于检测RAM用户是否开启MFA，代码中主要参数说明如下表所示。

        |参数|说明|示例|
        |--|--|--|
        |user\_name|RAM用户。|test123@169827232854\*\*\*\*.onaliyun.com|
        |rule\_parameters|规则参数。|dangerousActions|
        |input\_actions|指定的危险操作。|ecs:\*,oss:\*,log:\*|
        |configuration\_item|资源的配置详情。|请参见[自定义规则的数据结构如何]()。|
        |only\_custom|是否只检测自定义策略。取值：        -   true

配置审计只检测RAM用户的自定义策略。

        -   false

配置审计检测RAM用户的所有策略，包括系统策略和自定义策略。

|true|

        **说明：** 本段代码以检测RAM用户是否开启MFA为例。如果您需要通过其他参数检测RAM用户，请参见[自定义规则的数据结构如何]()。

    5.  单击**保存**。

        **说明：** 请勿单击**保存并执行**，即请勿手动执行代码。否则将导致操作失败。

5.  新建RAM用户，例如：test123。

    操作方法请参见[创建RAM用户](/cn.zh-CN/用户管理/创建RAM用户.md)。

6.  为RAM用户授权，例如：AliyunECSFullAccess。

    操作方法请参见[为RAM用户授权](/cn.zh-CN/用户管理/为RAM用户授权.md)。

7.  确认RAM用户未开启MFA。

    1.  登录[RAM控制台](https://ram.console.aliyun.com/)。

    2.  在左侧导航栏，选择**人员管理** \> **用户**。

    3.  单击目标RAM用户登录名称对应的链接。

    4.  在认证管理页签的多因素认证设备（MFA）区域，确认目标RAM用户的**设备状态**为**未启用**。

8.  设置资源合规事件投递到消息服务MNS的指定主题（Topic），例如：MNSTestConfig。

    操作方法请参见[发送资源事件到消息服务MNS](/cn.zh-CN/资源事件/发送资源事件到消息服务MNS.md)。

9.  新建自定义规则。

    1.  登录[配置审计控制台](https://config.console.aliyun.com)。

    2.  在左侧导航栏，选择**管理合规规则**。

    3.  在**管理合规规则**页面，单击**新建规则**。

    4.  在**基本设置**页面，选择**规则配置方式**为**通过函数计算**，函数Arn的**所在地域**选择**华东2（上海）**、**服务**选择**Ram\_User**、**函数**选择**RamDangerousPolicyUserBindMFA**，输入**规则名称**，单击**下一步**。

        ![新建自定义规则](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2412322061/p171242.png)

    5.  在**参数设置**页面，**规则触发机制**选择**周期执行**，**触发频率**选择**1小时**，规则关联的资源类型选择**Ram用户**，**规则入参名称**输入**dangerousActions**，**阈值**输入**ecs:\*,oss:\*,log:\***，单击**下一步**。

        ![设置参数](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8350032061/p171244.png)

        **说明：** **规则入参名称**和**阈值**必须与检测RAM用户是否开启MFA代码中的参数rule\_parameters和input\_actions保持一致。

    6.  在**修正设置**页面，**修正执行方式**默认为**不执行修正**，单击**提交**。

10. 查看RAM用户test123的检测结果。

    **说明：** 与此同时，您会收到来自消息服务MNS的不合规通知。

    1.  在新建规则的完成页面，单击**查看规则详情**。

    2.  在规则详情的关联资源的合规结果区域，单击目标资源ID链接，查看该资源的合规结果。

        ![查看规则评估结果](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5111232061/p171966.png)


