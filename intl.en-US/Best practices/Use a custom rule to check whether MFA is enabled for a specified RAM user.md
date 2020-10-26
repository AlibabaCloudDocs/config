# Use a custom rule to check whether MFA is enabled for a specified RAM user

This topic describes how to use a custom rule to check whether multi-factor authentication \(MFA\) is enabled for a specified RAM user. When you use a RAM user to manage resources, the RAM user must be authorized to perform the required high-risk operations. To enhance the logon security of a RAM user, you must enable MFA for the RAM user. The managed rules that Cloud Config provides can check whether MFA is enabled only for all RAM users. To check whether MFA is enabled for a specified RAM user who is authorized to perform high-risk operations, you must use a custom rule.

-   Message Service \(MNS\) is activated. For more information, see [Activate Message Service]().
-   Function Compute is activated. For more information, see [Activate the Function Compute service]().

## Overview

Assume that a RAM user is attached with the AliyunECSFullAccess policy, which is used to grant the full permissions on managing Elastic Compute Service \(ECS\) resources. In the following example, a custom rule is created to check whether MFA is enabled for the RAM user.

## Parameters

To create a custom rule in Cloud Config, you must set the following parameters in the consoles of Cloud Config, MNS, Resource Access Management \(RAM\), and Function Compute, as described in the following table.

|Service|Parameter|Example|
|-------|---------|-------|
|Cloud Config|Rule Name|RAMUserMFA|
|Trigger Type|Periodic|
|Frequency|1 Hour|
|Key|dangerousActions|
|Value|ecs:\*,oss:\*,log:\*|
|MNS|Topic Name|MNSTestConfig|
|Region|Singapore**Note:**

Cloud Config is deployed in the Singapore \(Singapore\) region. To reduce packet loss, we recommend that you select **Singapore \(Singapore\)** for the MNS Topic Region parameter. |
|RAM|Logon Name|test123@169827232854\*\*\*\*.onaliyun.com|
|Custom Policy|AliyunECSFullAccess|
|Function Compute|Service Name|Ram\_User|
|Function Name|RamDangerousPolicyUserBindMFA|

## Procedure

1.  Create a service in Function Compute.

    1.  Log on to the [Function Compute console](https://fc.console.aliyun.com).

    2.  In the top navigation bar, select a region, such as Singapore.

    3.  In the left-side navigation pane, click **Service/Function**.

    4.  On the Service/Function page, select **Create Service** from the drop-down list.

    5.  On the **Create Service** page, set the **Service Name** parameter to **Ram\_User**.

    6.  Click **Create**.

2.  Create a function in Function Compute.

    1.  On the **Service/Function** page, click **Create Function**.

    2.  In the **Create Function** step, set the **Function Type** parameter to **Event Function** and click **Next**.

    3.  In the **Configure Function** step, set the **Service Name** parameter to **Ram\_User**, the **Function Name** parameter to **RamDangerousPolicyUserBindMFA**, and the **Runtime** parameter to **python3**. Keep the default settings for other parameters.

        ![Create a function](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3784733061/p171239.png)

    4.  Click **Create**.

3.  Set the environment variables of the function.

    1.  In the left-side navigation pane, click **Service/Function**.

    2.  Click the created service. On the **Functions** tab, click the name of the function that you want to manage.

    3.  In the **Function Properties** section of the **Overview** tab, click **Configure**.

    4.  On the **Configure Function** page, set the Environment Variables parameter.

        |Key|Value|Example|
        |---|-----|-------|
        |AK|The AccessKey ID of your Alibaba Cloud account. For more information how to obtain the AccessKey ID, see [Obtain an AccessKey pair]().|LTAI4G6JZSANb8MZMkm1\*\*\*\*|
        |SK|The AccessKey secret of your Alibaba Cloud account. For more information how to obtain the AccessKey secret, see [Obtain an AccessKey pair]().|EMLHThhpD2UJqH1DXuAKii2sI\*\*\*\*|
        |ResourceTypes|The type of the resource.|ACS::RAM::User|

    5.  Click **Submit**.

4.  Compile the code that checks whether MFA is enabled for a RAM user.

    1.  In the left-side navigation pane, click **Service/Function**.

    2.  Click the created service. On the **Functions** tab, click the name of the function that you want to manage.

    3.  On the details page of the function, click the **Code** tab.

    4.  On the **Code** tab, select **In-line Edit**. Then, copy the following code to the code editor.

        ```
        #! /usr/bin/env python
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
            client = AcsClient(AK, SK, 'ap-southeast-1')
        
            # Open api request
            request = CommonRequest()
            request.set_domain('config.ap-southeast-1.aliyuncs.com')
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

        The code checks whether MFA is enabled for a RAM user. The following table describes the main parameters in the code.

        |Parameter|Description|Example|
        |---------|-----------|-------|
        |user\_name|The name of the RAM user.|test123@169827232854\*\*\*\*.onaliyun.com|
        |rule\_parameters|The parameters of the rule.|dangerousActions|
        |input\_actions|The high-risk operations that you want to manage.|ecs:\*,oss:\*,log:\*|
        |configuration\_item|The configuration items of the resource.|For more information, see [What is the data structure of functions that can be used to create custom rules?](/intl.en-US/FAQ/What is the data structure of functions that can be used to create custom rules?.md)|
        |only\_custom|Specifies whether to check only custom policies. Valid values:        -   true

Cloud Config checks only the custom policies of the RAM user.

        -   false

Cloud Config checks both system and custom policies of the RAM user.

|true|

        **Note:** The code in this example is used to check whether MFA is enabled for a specified RAM user. For more information about other parameters that can be used to check RAM users, see [What is the data structure of functions that can be used to create custom rules?](/intl.en-US/FAQ/What is the data structure of functions that can be used to create custom rules?.md)

    5.  Click **Save**.

        **Note:** Do not click **Save and Invoke**. Otherwise, the code cannot be executed.

5.  Create a RAM user, such as test123.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

6.  Grant permissions to the RAM user, such as the permissions of the AliyunECSFullAccess policy.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).

7.  Check whether MFA is enabled for the RAM user.

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/).

    2.  In the left-side navigation pane, choose **Identities** \> **Users**.

    3.  Click the name of the RAM user that you want to query.

    4.  In the MFA Device section of the Authentication tab, check whether the value of the **Device Status** parameter is **Disabled**.

8.  Specify an MNS topic to which resource non-compliance events are delivered, such as MNSTestConfig.

    For more information, see [Send notifications of resource events to an MNS topic](/intl.en-US/Events/Send notifications of resource events to an MNS topic.md).

9.  Create a custom rule.

    1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

    2.  In the left-side navigation pane, click **Rules**.

    3.  On the **Rules** page, click **Create Rule**.

    4.  In the **Basic Settings** step, select **Function Compute** for **Method**. In the Function ARN section, select **Singapore** from the **Region** drop-down list, **Ram\_User** from the **Service** drop-down list, and **RamDangerousPolicyUserBindMFA** from the **Function** drop-down list. Set the **Rule Name** parameter. Then, click **Next**.

        ![Create a custom rule](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4784733061/p171268.png)

    5.  In the **Parameter Settings** step, select **Periodic** for **Trigger Type** and select **1 Hour** from the **Frequency** drop-down list. In the Select related resources section, select **Ram User**. In the Parameter Settings section, click Add Rule Parameter. Set the **Key** parameter to **dangerousActions** and the **Value** parameter to **ecs:\*,oss:\*,log:\***. Then, click **Next**.

        ![Parameter Settings](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4784733061/p171244.png)

        **Note:** The **Key** and **Value** parameters must be the same as the rule\_parameters and input\_actions parameters in the preceding function code.

    6.  In the **Remediation Settings** step, keep the default option **Disable Remediation** for the **Remediation Method** parameter and click **Submit**.

10. View the check result.

    **Note:** In the meantime, you will receive a non-compliance notification from MNS.

    1.  In the Complete step of the Create Rule page, click **View Details**.

    2.  In the Compliance Result of Related Resources section of the Rule Details tab, click the ID of the specified resource to view the compliance evaluation results of the resource.

        ![Details: Evaluation Result](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4784733061/p171966.png)


