# SLB

This topic describes the managed rules that are related to Server Load Balancer \(SLB\) and the methods to fix non-compliance issues.

## slb-delete-protection-enabled

Checks whether deletion protection is enabled for an SLB instance of your Alibaba Cloud account.

Trigger type: configuration change

Applicable resource type: ACS::SLB::LoadBalancer

Input parameter: none

Cause: Deletion protection is not enabled for an SLB instance of your Alibaba Cloud account. You can fix this non-compliance issue by using one of following methods:

-   SLB console

    You can enable Deletion Protection for the SLB instance in the SLB console.

-   API

    You can also call the SetLoadBalancerDeleteProtection API operation. To enable deletion protection for the SLB instance, set DeletionProtection to on. For more information, see [SetLoadBalancerDeleteProtection](https://www.alibabacloud.com/help/doc-detail/122674.htm).


## slb-listener-https-enabled

Checks whether an HTTPS listener is configured for an SLB instance of your Alibaba Cloud account.

Trigger type: configuration change

Applicable resource type: ACS::SLB::LoadBalancer

Input parameter: none

Cause: No HTTPS listener is configured for an SLB instance of your Alibaba Cloud account. You can fix this non-compliance issue by using one of following methods:

-   SLB console

    You can configure an HTTPS listener for the SLB instance in the SLB console. For more information, see [Add an HTTPS listener](/intl.en-US/User Guide/Listeners/Add an HTTPS listener.md).

-   API

    You can also call the CreateLoadBalancerHTTPSListener API operation to create an HTTPS listener for the SLB instance. For more information, see [CreateLoadBalancerHTTPSListener](/intl.en-US/User Guide/Developer Guide/HTTPS listeners/CreateLoadBalancerHTTPSListener.md).


## slb-loadbalancer-in-vpc

Checks whether an SLB instance of your Alibaba Cloud account is deployed in a virtual private cloud \(VPC\). If you specify the value for the input parameter, the SLB instances that are deployed in the specified VPCs are considered as compliant. If you do not specify the value for the input parameter, the SLB instances that are deployed in all VPCs are considered as compliant.

Trigger type: configuration change

Applicable resource type: ACS::SLB::LoadBalancer

Input parameter: vpcIds. You can specify the IDs of the VPCs. Separate multiple VPC IDs with commas \(,\), for example, `vpc-25vk5****,vpc-6wesmaymqkgiuru5x****,vpc-8vbc16loavvujlzli****`.

Cause: An SLB instance of your Alibaba Cloud account is not deployed in a VPC that is specified in the input parameter. You can fix this non-compliance issue by using one of following methods:

-   Method 1: Create an SLB instance and deploy the instance in a VPC that is specified in the input parameter.

    **Note:**

    -   After you create an SLB instance, you cannot modify its network configurations. Therefore, you must create an SLB instance that follows the rules of Cloud Config.
    -   You can release an SLB instance that is no longer in use. For more information, see [Release an SLB instance](/intl.en-US/User Guide/Instance/Release an SLB instance.md).
    -   You can release pay-as-you-go SLB instances in the SLB console. However, you must submit a ticket before you can release a subscription SLB instance. You can submit a ticket to apply for an unconditional refund within five days after the subscription SLB instance is created.
    1.  Log on to the SLB console and create an SLB instance.

        For more information, see [Create an SLB instance](/intl.en-US/User Guide/Instance/Create an SLB instance.md).

    2.  View the ID of the VPC where the SLB instance is deployed.

        Log on to the SLB console. In the left-side navigation pane, choose Instances \> Instances. On the **Instances** page, find the instance and view the VPC ID in the **IP Address** column.

    3.  Log on to the Cloud Config console and add the VPC ID to the value of the input parameter.

        For more information, see [Modify a rule](/intl.en-US/Resource Compliance Audit/Manage rules/Modify a rule.md).

-   Method 2: Add the ID of the VPC where the SLB instance is deployed to the value of the input parameter.
    1.  View the ID of the VPC where the SLB instance is deployed.

        Log on to the SLB console. In the left-side navigation pane, choose Instances \> Instances. On the **Instance** page, find the instance and view the VPC ID in the **IP Address** column.

    2.  Log on to the Cloud Config console and add the VPC ID to the value of the input parameter.

        For more information, see [Modify a rule](/intl.en-US/Resource Compliance Audit/Manage rules/Modify a rule.md).


## slb-no-public-ip

Checks whether an SLB instances of your Alibaba Cloud account is associated with a public IP address. This rule is only applicable to IPv4 addresses.

Trigger type: configuration change

Applicable resource type: ACS::SLB::LoadBalancer

Input parameter: none

Cause: An SLB instance of your Alibaba Cloud account is associated with a public IP address. You can fix this non-compliance issue by using one of following methods:

-   SLB console

    You can create an SLB instance and set **Instance Type** to **Internal Network** in the SLB console. For more information, see [Create an SLB instance](/intl.en-US/User Guide/Instance/Create an SLB instance.md).

    **Note:**

    -   After you create an SLB instance, you cannot modify its network configurations. Therefore, you must create an SLB instance that follows the rules of Cloud Config.
    -   You can release an SLB instance that is no longer in use. For more information, see [Release an SLB instance](/intl.en-US/User Guide/Instance/Release an SLB instance.md).
    -   You can release pay-as-you-go SLB instances in the SLB console. However, you must submit a ticket before you can release a subscription SLB instance. You can submit a ticket to apply for an unconditional refund within five days after the subscription SLB instance is created.
-   API

    You can also call the CreateLoadBalancer API operation. To create an SLB instance that is associated with a private, set AddressType to intranet. For more information, see [CreateLoadBalancer](/intl.en-US/User Guide/Developer Guide/Server Load Balancer (SLB) instances/CreateLoadBalancer.md).


