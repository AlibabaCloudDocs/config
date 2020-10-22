# ECS

This topic describes the managed rules that are related to Elastic Compute Service \(ECS\) and the methods that are used to fix non-compliance issues.

## ecs-cpu-min-count-limit

Checks whether the number of vCPU cores for an ECS instance under your account is smaller than the specified threshold value.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: cpuCount. You can specify the minimum number of vCPU cores for an ECS instance.

Cause: The number of vCPU cores for an ECS instance under your account is smaller than the specified threshold value. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Change the instance type. You must make sure that the number of vCPU cores for the ECS instance is greater than or equal to the specified threshold value. Before you can change the instance type, you must stop the ECS instance. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes. You can change the instance type by using one of the following methods:
    -   ECS console

        Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and click **Change Instance Type** in the Actions column. On the page that appears, specify the instance type and click Change.

    -   API

        You can also call the ModifyInstanceSpec operation to modify the value of the InstanceType parameter. For more information, see [ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md).

-   Method 2: Add the instance type of the ECS instance to the value of the input parameter.


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-desired-instance-type

Checks whether an ECS instance under your account is of a specified instance type.

Applicable resource type: ACS::ECS::Instance

Trigger type: configuration change

Input parameter: instanceTypes. You can specify the instance types. Separate multiple instance types with commas \(,\), such as `t2.small, m4.large, i2.xlarge`.

Cause: An ECS instance under your account is not of a specified instance type. The rule evaluates the ECS instance as compliant if the type of the ECS instance is included in the value of the input parameter. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Change the instance type. You must make sure that the ECS instance is of a specified instance type. Before you can change the instance type, you must stop the ECS instance. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes. You can change the instance type by using one of the following methods:
    -   ECS console

        Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and click **Change Instance Type** in the Actions column. On the page that appears, specify the instance type and click Change.

    -   API

        You can also call the ModifyInstanceSpec operation to modify the value of the InstanceType parameter. For more information, see [ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md).

-   Method 2: Add the instance type of the ECS instance to the value of the input parameter.


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-disk-encrypted

Checks whether disks attached to your ECS instances are encrypted. If you specify the ID of a Key Management Service \(KMS\) key that is used to encrypt the disks, this rule checks whether the attached disks are encrypted with the key.

Applicable resource type: ACS::ECS::Disk

Trigger type: configuration change

Input parameter: kmsKeyIds. You can specify the ID of the KMS key that is used to encrypt the disks.

Cause:

-   None of the disks attached to your ECS instances are encrypted.
-   A disk that is attached to your ECS instance is encrypted with a KMS key. The ID of the KMS key is not listed in the value of the input parameter.

If a disk is encrypted with a KMS key, and the ID of the KMS key is listed in the value of the input parameter, the disk is considered compliant. The disk encryption feature applies only to data disks. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Create a disk and encrypt it with a KMS key. The ID of the KMS key is listed in the value of the input parameter. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

    You can also release a non-compliant disk.

    After the disk is released, the data stored on the disk is cleared. For more information, see [Release a disk](/intl.en-US/Block Storage/Cloud disks/Release a disk.md).

-   Method 2: Add the ID of the KMS key that is used to encrypt the disks to the value of the input parameter.

Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-disk-in-use

Checks whether a disk under your account is attached to any ECS instance.

Applicable resource type: ACS::ECS::Disk

Trigger type: configuration change

Input parameter: none

Cause: A disk under your account is not attached to an ECS instance. If a disk is attached to an ECS instance and the status of the disk becomes **In Use**, the disk is considered compliant. You can fix this non-compliance issue by using one of the following methods:

-   ECS console

    Log on to the ECS console. In the left-side navigation pane, choose Storage & Snapshots \> Disks. On the Disks page, find the disk and choose **More** \> **Attach** in the Actions column. In the dialog box that appears, select an ECS instance and click Attach.

-   API

    You can also call the AttachDisk operation to attach a pay-as-you-go data disk to an ECS instance. For more information, see [AttachDisk](/intl.en-US/API Reference/Disk/AttachDisk.md).


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-gpu-min-count-limit

Checks whether the number of GPU cores for an ECS instance under your account is smaller than the specified threshold value.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: gpuCount. You can specify the minimum number of GPU cores for an ECS instance.

Cause: The number of GPU cores for an ECS instance under your account is smaller than the specified threshold value. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Change the instance type. You must make sure that the number of GPU cores for the ECS instance is greater than or equal to the specified threshold value. Before you can change the instance type, you must stop the ECS instance. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes. You can change the instance type by using one of the following methods:

    -   ECS console

        Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and click **Change Instance Type** in the Actions column. On the page that appears, specify the instance type and click Change.

    -   API

        You can also call the ModifyInstanceSpec operation to modify the value of the InstanceType parameter. For more information, see [ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md).

    You cannot change the instance type of an ECS instance that is attached to a local disk. In this case, you must purchase an ECS instance that meets the requirements of Cloud Config.

    You can also release a non-compliant ECS instance. You can release pay-as-you-go ECS instances in the ECS console at any time. After a subscription ECS instance expires, you can manually release the instance. If you do not renew the subscription within 15 days after the instance expires, the instance is automatically released. Before the instance expires, you can submit a ticket to apply for a refund and release the subscription ECS instance. You can also change the billing method of the ECS instance from subscription to pay-as-you-go, and then release the instance.

    After an ECS instance is released, the instance data is cleared. We recommend that you back up your data in advance.

    For more information, see [Release an instance](/intl.en-US/Instance/Manage instances/Release an instance.md).

-   Method 2: Add the instance type of the ECS instance to the value of the input parameter.

Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-instance-attached-security-group

Checks whether an ECS instance under your account is added to one or more specified security groups.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: securityGroupIds. You can specify the IDs of the security groups. Separate multiple IDs with commas \(,\), such as `sg-hp3ebbv7ir****,sg-hp3ebbv****`.

Cause: An ECS instance under your account is not added to a security group with a specified ID. If an ECS instance is added to a security group with a specified ID, the ECS instance is considered compliant. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Add the ECS instance to a security group with a specified ID. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.
-   Method 2: Add the ID of the security group to the value of the input parameter. This is the security group to which an ECS instance is added. You can add an ECS instance to a security group by using one of the following methods:
    -   ECS console

        Method 1: Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, click an instance ID to go to the details page of the instance. On the instance details page, click the **Security Groups** tab. On the tab that appears, click **Security Groups**, and then click **Add to Security Group**.

        ![ECS_6](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4160019951/p73705.png)

        Method 2: Log on to the ECS console. In the left-side navigation pane, choose Network & Security \> Security Groups. On the Security Groups page, click an security group ID to go to the details page of the security group. In the left-side navigation pane, click **Instances in Security Group**. In the upper-right corner of the page that appears, click **Add Instance**.

        ![ECS_7](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4160019951/p73706.png)

    -   API

        You can also call the JoinSecurityGroup operation to add an ECS instance to a specified security group. For more information, see [JoinSecurityGroup](/intl.en-US/API Reference/Security groups/JoinSecurityGroup.md).


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-instance-deletion-protection-enabled

Checks whether release protection is enabled for a pay-as-you-go ECS instance under your account.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: none

Cause: Release protection is not enabled for a pay-as-you-go ECS instance under your account. You can fix this non-compliance issue by using one of the following methods:

-   ECS console

    Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and choose **More** \> **Instance Settings** \> **Change Release Protection Setting**. In the dialog box that appears, turn on **Release Protection**. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

-   API

    You can also call the ModifyInstanceAttribute operation and set the DeletionProtection parameter to true to enable release protection for an ECS instance. For more information, see [ModifyInstanceAttribute](/intl.en-US/API Reference/Instances/ModifyInstanceAttribute.md).


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-instances-in-vpc

Checks whether an ECS instance under your account resides in a virtual private cloud \(VPC\). You can specify the VPC IDs to associate with your ECS instances. Then, Cloud Config can be used to evaluate your resources based on the specified VPC IDs. If an ECS instance is not deployed in a VPC, the compliance evaluation result Not Applicable is returned. If an ECS instance is deployed in a VPC with a specified ID, the ECS instance is considered compliant. Otherwise, an ECS instance is considered non-compliant.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: vpcIds. You can specify the IDs of the VPCs where the ECS instances reside. Separate multiple VPC IDs with commas \(,\), such as `vpc-25vk5****,vpc-6wesmaymqkgiuru5x****,vpc-8vbc16loavvujlzli****`.

Cause: An ECS instance under your account does not reside in a specified VPC. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Create an ECS instance and deploy the instance in a VPC with a specified ID. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

    You can also release a non-compliant ECS instance. You can release pay-as-you-go ECS instances in the ECS console at any time. After a subscription ECS instance expires, you can manually release the instance. If you do not renew the subscription within 15 days after the instance expires, the instance is automatically released. Before the instance expires, you can submit a ticket to apply for a refund and release the subscription ECS instance. You can also change the billing method of the ECS instance from subscription to pay-as-you-go, and then release the instance.

    After an ECS instance is released, the instance data is cleared. We recommend that you back up your data in advance.

    For more information, see [Release an instance](/intl.en-US/Instance/Manage instances/Release an instance.md).

    When you purchase an ECS instance, set the **Network Type** parameter to VPC.

-   Method 2: Add the ID of the VPC where the ECS instance is deployed to the value of the input parameter.

Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-instance-no-public-ip

Checks whether an ECS instance under your account is associated with a public IP address. This rule is applicable only to IPv4 addresses.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: none

Cause: An ECS instance under your account is associated with a public IP address. If an ECS instance is associated with a private IP address, the ECS instance is considered compliant. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: If the ECS instance is associated with an elastic IP address \(EIP\), disassociate the EIP from the ECS instance. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

    To disassociate the EIP from the ECS instance, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and choose **More** \> **Network and Security Group** \> **Unbind EIP** in the Actions column. In the message that appears, click OK. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

-   Method 2: If the ECS instance is associated with a public IP address, convert the public IP address to an EIP and then disassociate the EIP from the ECS instance. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

    To modify the network settings of the ECS instance, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and choose **More** \> **Network and Security Group** \> **Convert to EIP** in the Actions column. Then, disassociate the EIP from the ECS instance by using Method 1. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

-   Method 3: Purchase an ECS instance and do not select **Assign Public IP Address** in the **Public IP Address** section in the **Networking** step. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes.

    You can also release a non-compliant ECS instance. You can release pay-as-you-go ECS instances in the ECS console at any time. After a subscription ECS instance expires, you can manually release the instance. If you do not renew the subscription within 15 days after the instance expires, the instance is automatically released. Before the instance expires, you can submit a ticket to apply for a refund and release the subscription ECS instance. You can also change the billing method of the ECS instance from subscription to pay-as-you-go, and then release the instance.

    After an ECS instance is released, the instance data is cleared. We recommend that you back up your data in advance.

    For more information, see [Release an instance](/intl.en-US/Instance/Manage instances/Release an instance.md).


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## ecs-memory-min-size-limit

Checks whether the memory size for an ECS instance under your account is smaller than the specified threshold value.

Trigger type: configuration change

Applicable resource type: ACS::ECS::Instance

Input parameter: memorySize. You can specify the minimum memory size for an ECS instance.

Cause: The memory size for an ECS instance under your account is smaller than the specified threshold value. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Change the instance type. You must make sure that the memory size for the ECS instance is greater than or equal to the specified threshold value. Before you can change the instance type, you must stop the ECS instance. You can change the instance type by using one of the following methods:
    -   ECS console

        Log on to the ECS console. In the left-side navigation pane, choose Instances & Images \> Instances. On the Instances page, find the ECS instance and click **Change Instance Type** in the Actions column. On the page that appears, specify the instance type and click Change.

    -   API

        You can also call the ModifyInstanceSpec operation to modify the value of the InstanceType parameter. For more information, see [ModifyInstanceSpec](/intl.en-US/API Reference/Instances/ModifyInstanceSpec.md).

-   Method 2: Add the instance type of the ECS instance to the value of the input parameter.

Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## sg-public-access-check

Checks whether an ECS security group under your account allows access from all IP addresses.

Trigger type: configuration change

Applicable resource type: ACS::ECS::SecurityGroup

Input parameter: none

Cause: An inbound rule of an ECS security group under your account allows access from all IP addresses. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Modify the settings of the inbound rule that allows access from all IP addresses.
-   Method 2: Delete the inbound rule that allows access from all IP addresses.
    -   ECS console

        To modify the settings of the inbound rule, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Network & Security \> Security Groups. On the Security Groups page, click the security group ID. On the **Inbound** tab of the **Security Group Rules** page, find the inbound rule and click Modify in the Actions column. Then, you can set the Action parameter to Forbid or modify the authorization object.

        To delete the inbound rule, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Network & Security \> Security Groups. On the Security Groups page, click the security group. On the **Inbound** tab of the **Security Group Rules** page, find the inbound rule and click Delete in the Actions column. In the message that appears, click OK.

    -   API

        You can call the ModifySecurityGroupRule operation to modify the value of the Policy or SourceCidrIp parameter of the inbound rule. For more information, see [ModifySecurityGroupRule](/intl.en-US/API Reference/Security groups/ModifySecurityGroupRule.md).

        You can also call the RevokeSecurityGroup operation to delete the inbound rule from the ECS security group. For more information, see [RevokeSecurityGroup](/intl.en-US/API Reference/Security groups/RevokeSecurityGroup.md).


Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

## sg-risky-ports-check

Checks whether an ECS security group under your account allows inbound or outbound traffic on high-risk ports.

Trigger type: configuration change

Applicable resource type: ACS::ECS::SecurityGroup

Input parameter: ports. You can specify the ports that produce high risks.

Cause: The port range of an inbound or outbound rule of an ECS security group includes the specified ports, or the range is set to -1/-1 to indicate all ports. You can fix this non-compliance issue by using one of the following methods:

-   Method 1: Find the inbound or outbound rule and set the Action parameter to Forbid. The rule contains a port range that includes the specified ports.
-   Method 2: Delete the inbound rule or outbound rule. The rule contains a port range that includes the specified ports.
-   Method 3: Find the inbound or outbound rule and modify the port range. The rule contains a port range that includes the specified ports.
-   Method 4: Remove the port number from the value of the input parameter.
    -   ECS console

        To modify the inbound or outbound rule in the ECS console, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Network & Security \> Security Groups. On the Security Groups page, click the security group ID. On the **Security Group Rules** page, find the inbound rule or outbound rule and click Modify in the Actions column. Set the **Action** parameter to Forbid or change the value of the **Port Range** parameter, and click OK.

        To delete the inbound or outbound rule, perform the following steps: Log on to the ECS console. In the left-side navigation pane, choose Network & Security \> Security Groups. On the Security Groups page, click the security group ID. On the **Security Group Rules** page, find the inbound rule or outbound rule and click **Delete** in the Actions column.

    -   API
        -   You can call the ModifySecurityGroupRule or ModifySecurityGroupEgressRule operation to modify the values of the Policy and PortRange parameters of an inbound or outbound rule. For more information, see [ModifySecurityGroupRule](/intl.en-US/API Reference/Security groups/ModifySecurityGroupRule.md) and [ModifySecurityGroupEgressRule](/intl.en-US/API Reference/Security groups/ModifySecurityGroupEgressRule.md).
        -   You can also call the RevokeSecurityGroup or RevokeSecurityGroupEgress operation to delete an inbound or outbound rule of the ECS security group. For more information, see [RevokeSecurityGroup](/intl.en-US/API Reference/Security groups/RevokeSecurityGroup.md).

Re-evaluation method: Log on to the Cloud Config console. In the left-side navigation pane, click Rules. On the Rules page, click the rule ID to go to the details page of the rule. In the upper-right corner of the page, click **Re-evaluate**. You can also wait for 10 minutes for Cloud Config to automatically re-evaluate resources.

