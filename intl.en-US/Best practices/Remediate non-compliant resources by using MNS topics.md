# Remediate non-compliant resources by using MNS topics

This topic describes how to push alert notifications to specified Message Service \(MNS\) topics if Cloud Config detects non-compliant configuration changes of resources. If you receive a non-compliance alert, Cloud Config uses the relevant functions of Alibaba Cloud Function Compute to automatically remediate these resources.

-   Cloud Config is authorized to access your resources and a rule is created based on a managed rule. For more information, see [Authorize Cloud Config to access your resources](/intl.en-US/Quick Start/Authorize Cloud Config to access your resources.md) and [Create a rule by using a managed rule](/intl.en-US/Resource Compliance Audit/Manage rules/Create a rule.md).
-   MNS is activated. For more information, see [Activate Message Service]().
-   Object Storage Service \(OSS\) is activated and an OSS bucket is created. For more information, see [Activate OSS](/intl.en-US/Console User Guide/Sign up for OSS.md) and [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).
-   Function Compute is activated. For more information, see [Activate the Function Compute service]().

## Scenarios

You create a rule function and link it to a resource type named ACS::OSS::Bucket based on the managed rule named oss-bucket-public-read-prohibited. Cloud Config evaluates all resources of this type. One of the resources is evaluated as **Non-compliant**, as shown in the following figure.

![Bucket non-compliance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p147935.png)

## Parameters

In this example, the read and write permissions of an OSS bucket are remediated. The following table describes the parameters that you can specify.

|Cloud service|Parameter|Example|
|-------------|---------|-------|
|Cloud Config|Managed Rule|oss-bucket-public-read-prohibited|
|Rule Name|test-oss-bucket-public-read-prohibited|
|MNS|Topic|MNSTestConfig|
|MNS Topic Region|Singapore \(Singapore\)|
|OSS|OSS Bucket|config-snapshot|
|Bucket ACL|Public-read|
|Function Compute|Service Name|resource\_repair|
|System Policies|AliyunOSSFullAccess|
|Function Name|oss\_repair\_acl\_trigger|
|Trigger Name|ConfigRuleNonComplianceMNSTrigger|

**Note:**

Cloud Config is deployed in the Singapore \(Singapore\) region. To reduce packet loss, we recommend that you select **Singapore \(Singapore\)** for the MNS Topic Region parameter.

## Workflow

The following figure shows how non-compliant resources are to automatically remediated.

![Remediation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p148001.png)

## Procedure

1.  Subscribe to resource events.

    For more information, see [Send notifications of resource events to an MNS topic](/intl.en-US/Events/Send notifications of resource events to an MNS topic.md).

2.  Create a service.

    1.  Log on to the [Function Compute console](https://fc.console.aliyun.com).

    2.  In the top navigation bar, select a region, for example, Singapore \(Singapore\)

    3.  In the left-side navigation pane, click **Service/Function**.

    4.  On the Service/Function page, select **Create Service** from the drop-down list.

    5.  On the **Create Service** page, specify **Service Name** and **Description**.

        ![Create a service](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p161827.png)

    6.  Click **Create**.

3.  Authorize the created service to access OSS buckets.

    1.  On the **Service Configurations** tab, click **Update**.

    2.  In the **Role Config** section, select **AliyunOSSFullAccess** from the **System Policies** drop-down list.

        ![Authorize the service to access OSS buckets](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p143868.png)

    3.  Click **Authorize**.

    4.  On the **Role Templates** page, specify **Policy Name**.

        ![Create a role](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p143881.png)

    5.  Click **Confirm Authorization Policy**.

4.  Create a function.

    1.  On the **Service/Function** page, click **Create Function**.

    2.  In the **Create Function** step, specify **Event Function** for the **Function Type** parameter, and then click **Next**.

    3.  In the **Configure Function** step, select **resource\_repair** from the **Service Name** drop-down list, and **python3** from the **Runtime** drop-down list. Keep the default values of other parameters.

        ![Configure the function](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8747290061/p143857.png)

    4.  Click **Create**.

5.  Set the environment variables of the function.

    1.  In the left-side navigation pane, click **Service/Function**.

    2.  Click the created service. On the **Functions** tab, click the function name.

    3.  In the **Function Properties** section of the **Overview** tab, click **Configure**.

    4.  On the **Configure Function** page, set the required parameters.

        -   Enter **prepareRuleName** in the **Key** field.

            The values of the **prepareRuleName** parameter and **ENV\_RULE\_NAME** parameter must be the same.

        -   Enter **test-oss-bucket-public-read-prohibited** in the **Value** field.

            The value of the **test-oss-bucket-public-read-prohibited** parameter is the rule name.

    5.  Click **Submit**.

6.  Create a trigger.

    1.  Click the created service. On the **Functions** tab, click the function name.

    2.  On the **details** page, click the **Triggers** tab.

    3.  On the **Triggers** tab, click **Create Trigger**.

    4.  In the **Create Trigger** dialog box, set the required parameters.

        ![Create a trigger](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9747290061/p161831.png)

        Set the following parameters:

        -   Select **MNS Topic Trigger** from the **Trigger Type** drop-down list.
        -   Enter **ConfigRuleNonComplianceMNSTrigger** in the **Trigger Name** field.
        -   Select **China \(Shanghai\)** from the **MNS Topic Region** drop-down list.
        -   Select **MNSTestConfig** from the **Topic** drop-down list.
        -   Select **JSON** from the **Event Format** drop-down list.
        **Note:** When you use the MNS topic trigger for the first time, you can specify **Quick Authorize** for the **Role Operation** parameter. You can authorize MNS to use the role AliyunMNSNotificationRjole to access your cloud resources as prompted. Then you can close and reopen the **Create Trigger** page. The role is displayed on the page.

    5.  Click **OK**.

        After the trigger is created, you will receive notifications of non-compliant events when Cloud Config evaluates resource compliance.

7.  Configure the automatic remediation code.

    1.  In the left-side navigation pane, click **Service/Function**.

    2.  Click the created service. On the **Functions** tab, click the function name.

    3.  On the details page, click the **Code** tab.

    4.  On the **Code** tab, select **In-line Edit**, copy and paste the following code.

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
                    # os.environ.get(ENV_RULE_NAME) // Obtain the rule name, for example, test-oss-bucket-public-read-prohibited.
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

        **Note:** prepareRuleName is used as an example rule name in this code to describe the automatic remediation method of non-compliant resources. For information about how to remediate non-compliant resources by using other parameters, see [Resource non-compliance events](/intl.en-US/Events/Event types/Resource non-compliance events.md).

    5.  Click **Save**.

        **Note:** Do not click **Save and Invoke**. Otherwise, the code cannot be executed.

8.  After 10 minutes, you can check the remediation result.

    **Note:** If a resource is evaluated by the rule as non-compliant and no configurations are changed, you must re-evaluate resources before you perform this step. For more information, see [Manually re-evaluate resources](/intl.en-US/Resource Compliance Audit/Manage rules/Manually re-evaluate resources.md).

    -   View the remediation result in the Cloud Config console.

        ![OSS bucket compliance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9747290061/p144367.png)

    -   View the remediation result in the OSS console.

        ![OSS bucket compliance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9747290061/p146232.png)


