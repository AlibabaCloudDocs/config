# Create a custom rule by using Function Compute

If the managed rules that Cloud Config provides do not meet your requirements, you can use Function Compute to create a custom rule. When a custom rule is triggered, Cloud Config evaluates the resources based on the rule function and displays the compliance evaluation results.

Function Compute is activated. For more information, see [Activate the Function Compute service]().

The following section describes the differences between custom rules and managed rules:

-   Managed rules

    A managed rule is a rule function that is created in Function Compute. You can select the rule as required in the Cloud Config console. For more information about the managed rules that Cloud Config provides, see [Managed rules](/intl.en-US/Resource Compliance Audit/Preset rules/Managed rules.md).

-   Custom rules

    A custom rule is a rule that you can create based on a rule function in Function Compute. After you create a rule function, you can enter the Alibaba Cloud Resource Name \(ARN\) of the function in the Cloud Config console to create a custom rule.


## Create a custom rule

1.  Create a function in the Function Compute console.

    For more information, see [Function operations](https://www.alibabacloud.com/help/doc-detail/52077.htm).

    **Note:**

    -   When you create a function, set the **Function Type** parameter to **Event Function**, the **Runtime** parameter to **python3**, and the **Function Handler** parameter to the default value **index.handler**.
    -   For more information about Function Compute, see [Function Compute](https://www.alibabacloud.com/help/zh/product/50980.htm).
2.  View the ARN of the created function in the Function Compute console.

    After a function is created, a function ARN is generated. You can view the ARN on the **Overview** tab of the function details page.

3.  Create a rule in the Cloud Config console. When you create a rule, select the region, service, and function in the Function ARN section.

    For more information, see [Create a rule by using Function Compute](/intl.en-US/Resource Compliance Audit/Manage rules/Create a rule.md).


## Develop the code of a rule function

A rule is a piece of logic judgment code that is stored in a rule function. When the rule is used to evaluate resources, the rule function is triggered to evaluate the resources. The following code of the sample rule contains two key functions.

-   handler

    The handler function is the entry function that is called when the custom rule is triggered. You must define the handler function when you develop the code of the rule function.

-   put\_evaluations

    The put\_evaluations function is called in the handler function to return the compliance evaluation result. You can use the following sample code in JSON format to create a rule:

    ```
    #! /usr/bin/env python
    # -*- encoding: utf-8 -*-
    import logging
    import json
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.auth.credentials import StsTokenCredential
    from aliyunsdkcore.acs_exception.exceptions import ClientException
    from aliyunsdkcore.acs_exception.exceptions import ServerException
    from aliyunsdkcore.request import CommonRequest
    
    logger = logging.getLogger()
    
    # The resource types to which the rule function applies. Separate multiple resource types with commas (,).
    MATCH_RESOURCE_TYPES = ''
    
    # The compliance evaluation results.
    COMPLIACE_TYPE_COMPLIANT = 'COMPLIANT'
    COMPLIACE_TYPE_NON_COMPLIANT = 'NON_COMPLIANT'
    COMPLIACE_TYPE_NOT_APPLICABLE = 'NOT_APPLICABLE'
    COMPLIACE_TYPE_INSUFFICIENT_DATA = 'INSUFFICIENT_DATA'
    
    
    def handler(event, context):
        """
        Process an event.
        :param event: the event.
        :param context: the context.
        :return: the compliance evaluation result.
        """
        # Check whether the event is valid.
        evt = validate_event(event)
        if not evt:
            return None
    
        rule_parameters = evt.get('ruleParameters')
        result_token = evt.get('resultToken')
        invoking_event = evt.get('invokingEvent')
    
        # Initialize the return values.
        compliance_type = COMPLIACE_TYPE_NOT_APPLICABLE
        annotation = None
    
        # Obtain the configuration item.
        configuration_item = invoking_event.get('configurationItem')
        if not configuration_item:
            logger.error('Configuration item is empty.')
            return None
    
        ordering_timestamp = configuration_item.get('captureTime')
        resource_id = configuration_item.get('resourceId')
        resource_type = configuration_item.get('resourceType')
    
        # Obtain the compliance evaluation result.
        compliance_type, annotation = evaluate_configuration_item(
            rule_parameters, configuration_item)
    
        # The compliance evaluation result.
        evaluations = [
            {
                'complianceResourceId': resource_id,
                'complianceResourceType': resource_type,
                'orderingTimestamp': ordering_timestamp,
                'complianceType': compliance_type,
                'annotation': annotation
            }
        ]
    
        # Return the compliance evaluation result.
        put_evaluations(context, result_token, evaluations)
    
        return evaluations
    
    
    def evaluate_configuration_item(rule_parameters, configuration_item):
        """
        Evaluate a configuration item.
        :param rule_parameters: the input parameters of the rule.
        :param configuration_item: the configuration item.
        :return: the compliance evaluation result and annotation.
        """
        # Initialize the return values.
        compliance_type = COMPLIACE_TYPE_NOT_APPLICABLE
        annotation = None
    
        # Obtain the resource type and resource ID.
        resource_type = configuration_item['resourceType']
        full_configuration = configuration_item['configuration']
    
        # Check whether the resource type is valid.
        if MATCH_RESOURCE_TYPES and resource_type not in MATCH_RESOURCE_TYPES.split(','):
            annotation = 'Resource type is {}, not in {}.'.format(
                resource_type, MATCH_RESOURCE_TYPES)
            return compliance_type, annotation
    
        # Check whether the configuration is empty.
        if not full_configuration:
            annotation = 'Configuration is empty.'
            return compliance_type, annotation
    
        # Convert the configuration to a JSON object.
        configuration = parse_json(full_configuration)
        if not configuration:
            annotation = 'Configuration:{} in invald.'.format(full_configuration)
            return compliance_type, annotation
    
        # =========== Your code starts here. =========== #
    
    
        # =========== Your code ends here. =========== #
    
        return compliance_type, annotation
    
    
    def validate_event(event):
        """
        Check whether an event is valid.
        :param event: Event
        :return: the JSON object.
        """
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
        """
        Convert a JSON string to a JSON object.
        :param content: the JSON string.
        :return: the JSON object.
        """
        try:
            return json.loads(content)
        except Exception as e:
            logger.error('Parse content:{} to json error:{}.'.format(content, e))
            return None
    
    
    def put_evaluations(context, result_token, evaluations):
        """
        Call the Cloud Config API to return the evaluation result.
        :param context: the Function Compute context.
        :param result_token: the result token.
        :param evaluations: the compliance evaluation result.
        :return: None
        """
        # You must enter the AccessKey ID and AccessKey secret of your Alibaba Cloud account and your account must have the AliyunConfigFullAccess permission.
        client = AcsClient(
            'XXXX',
            'XXXXXXX',
            'ap-southeast-1',
        )
    
        # Create a request and set the required parameters. Set the domain parameter to config.ap-southeast-1.aliyuncs.com.
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


## Input parameters of a rule function

In an event message, the ruleParameters field stores the input parameters of a rule function. Other fields provide the event information when the custom rule is triggered. The following code shows the fields in an event message in JSON format:

```
{
    version:"version number",
    orderingTimestamp:"time when the command is executed",
    invokingEvent:{
      messageType:"message type",
        configurationItem:{
          "accountId":"ID of your Alibaba Cloud account",
            "arn":"resource ARN",
            "availabilityZone":"zone",
            "regionId":"region ID",
            "configuration":"resource configuration in the form of a string, which varies with resources",
            "configurationDiff":"configuration changes",
            "relationship":"relationship of the resource with others",
            "relationshipDiff":"relationship changes",
            "captureTime":"time when the change is captured",
            "resourceCreationTime":"time when the resource is created",
            "resourceStatus":"resource status",
            "resourceId":"resource ID",
            "resourceName":"resource name",
            "resourceType":"resource type",
            "supplementaryConfiguration":"supplementary configuration",
            "tags":"tags of the resource"
        },
        notificationCreationTimestamp:"time when the event message is generated"
    },
    ruleParameters:{
      "key":"value"
    },
    resultToken:"the result token in Function Compute" 
}
```

context: the context information that is automatically set when the custom rule is triggered.

-   `context.credentials.access_key_id:"accessKey"`
-   `context.credentials.access_key_secret:"accessSecret"`
-   `context.region:"region information"`

