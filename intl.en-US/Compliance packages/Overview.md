# Overview

Compliance packages dynamically and continuously monitor the compliance of your resources and notify you of resource non-compliance at the earliest opportunity. This topic describes the check items of the eight compliance packages that are provided by Cloud Config.

## CISComplianceCheck

CIS stands for Center for Internet Security. The CISComplianceCheck compliance package dynamically and continuously monitors your resources to check whether the resources are compliant with the CIS Controls that are stipulated by CIS. For more information about CIS, visit [CIS](https://www.cisecurity.org/). If your resources are compliant with the CIS Controls, network security risks can be reduced.

The CIS Controls are a set of 20 control points or objectives designed to help enterprises safeguard their systems and data. The following table describes the check items of the CISComplianceCheck compliance package.

|Item|Description|
|----|-----------|
|Accounts|Checks the passwords set for and permission policies attached to Alibaba Cloud accounts and RAM users.|
|Networks|Checks the network ownership, security group configurations, traffic monitoring configurations, and whether ports are open for instances.|
|Instances|Checks the details of disk encryption, system updates, and endpoint protection, and whether ports are open for instances.|
|Object Storage Service \(OSS\) buckets|Checks the configurations of read and write permissions, secure transmission, and content encryption for OSS buckets.|
|Databases|Checks the connection types, data encryption configurations, and audit configurations of databases.|

## ClassifiedProtectionPreCheck

The ClassifiedProtectionPreCheck compliance package dynamically and continuously monitors your resources to check whether the resources are compliant with Multi-Level Protection Scheme \(MLPS\) 2.0 Level 3. This allows you to perform self-service checks to pass the compliance evaluation of classified protection. For more information about MLPS 2.0, see [MLPS 2.0](/intl.en-US/Compliance packages/MLPS 2.0.md).

The following table describes the check items of the ClassifiedProtectionPreCheck compliance package.

|Item|Description|
|----|-----------|
|Network types|Checks whether the network types of Elastic Compute Service \(ECS\) instances and database instances are virtual private clouds \(VPCs\). If an instance resides in a VPC, and the VPC is included in the expected value of the relevant rule parameter, the instance configuration is considered compliant.|
|Protection configurations|Checks whether the IP address whitelists of ECS instances and database instances are set to 0.0.0.0/0 and whether encryption is enabled for each ECS data disk.|
|OSS buckets|Checks whether OSS buckets are accessed in read-only mode and whether zone-redundant storage and server-side encryption by using OSS-managed keys are enabled.|
|Bandwidths|Checks whether the bandwidths of Server Load Balancer \(SLB\) instances and elastic IP addresses reach the specified lower limits.|

## BestPracticesForOSS

Various customers store important business data in OSS buckets. Therefore, if bucket configurations are non-compliant, business risks such as data leaks or loss may be brought about. The BestPracticesForOSS compliance package dynamically and continuously monitors the compliance of your OSS buckets and notifies you of non-compliance at the earliest opportunity.

The following table describes the check items of the BestPracticesForOSS compliance package.

|Item|Description|
|----|-----------|
|Read/write permissions|Globally checks whether the access control lists \(ACLs\) of OSS buckets are set to public read or public read and write.|
|Protection configurations|Checks whether object encryption and hotlink protection are enabled for OSS buckets. This helps improve data security.|
|Zone-redundant storage|Checks whether zone-redundant storage is enabled for OSS buckets.|

## BestPracticesForNetwork

The BestPracticesForNetwork compliance package dynamically and continuously checks the network architecture, workloads, and security configurations for compliance issues. The compliance package also notifies you of non-compliance at the earliest opportunity.

The following table describes the check items of the BestPracticesForNetwork compliance package.

|Item|Description|
|----|-----------|
|Resource quotas of workloads|Checks the resource quotas of workloads to ensure service continuity. If the resource quotas of workloads cannot reach the lower limits required by business peaks, the service may be interrupted during peak hours.|
|Network architecture|Checks the network architecture to ensure business isolation from the Internet. If network configurations are inappropriate, the business system may be exposed to the Internet, and attacks over the Internet and data leaks may occur.|
|Real-time monitoring|Checks whether real-time monitoring is enabled for networks to ensure that network errors can be identified at the earliest opportunity. This prevents potential business risks.|

## BestPracticesForAccountGovernance

The BestPracticesForAccountGovernance compliance package performs comprehensive compliance checks on Alibaba Cloud accounts and RAM users to help you identify systematic risks in advance and prevent the risks.

The following table describes the check items of the BestPracticesForAccountGovernance compliance package.

|Item|Description|
|----|-----------|
|Logons of Alibaba Cloud accounts or RAM users|Checks the validity periods of the passwords set for Alibaba Cloud accounts and RAM users and whether multi-factor authentication \(MFA\) is enabled for them.|
|Security configurations|Checks whether invalid RAM users, user groups, or permission policies exist, and whether key pairs are created for Alibaba Cloud accounts.|
|Authorization|Checks whether permission policies are attached to RAM users and whether full permissions on Alibaba Cloud services are granted.|

## BestPracticesForDataBase

The BestPracticesForDataBase compliance package continuously checks the compliance of ApsaraDB RDS, ApsaraDB for Redis, ApsaraDB for MongoDB, and PolarDB instances in terms of encryption and access control. This helps prevent data leaks.

The following table describes the check items of the BestPracticesForDataBase compliance package.

|Item|Description|
|----|-----------|
|Validity periods|Checks the validity periods of database instances.|
|Protection configurations|Checks whether release protection is enabled and IP address whitelists are set to 0.0.0.0/0 for database instances.|
|Network types|Checks whether the network types of database instances are VPCs and whether the specified VPCs are included in the expected value of the relevant rule parameter.|

## BestPracticesForECS

The BestPracticesForECS compliance package continuously checks the compliance of ECS instances in terms of statuses, security configurations, protection configurations, and snapshot configurations. This prevents the risks of business interruption and out-of-control costs.

The following table describes the check items of the BestPracticesForECS compliance package.

|Item|Description|
|----|-----------|
|Statuses|Checks the statuses of ECS instances.|
|Security configurations|Checks the validity periods and security groups of ECS instances.|
|Protection configurations|Checks whether release protection and disk encryption are enabled for ECS instances.|
|Snapshot configurations|Checks whether automatic snapshot policies are configured, whether automatic locking is enabled, and whether the retention periods of automatic snapshots meet the requirements for the disks of ECS instances.|

## RMiTComplianceCheck

The RMiTComplianceCheck compliance package checks the compliance of cloud IT systems based on the Risk Management in Technology \(RMiT\) framework for financial institutions in Malaysia.

The following table describes the check items of the RMiTComplianceCheck compliance package.

|Item|Description|
|----|-----------|
|Accounts|Checks the passwords, permission policies, and logons of RAM users, and whether MFA is enabled for the RAM users.|
|SLB instances|Checks whether release protection and HTTPS listeners are enabled for SLB instances, and whether the certificates issued by Alibaba Cloud are valid.|
|ECS instances|Checks whether the network types of ECS instances are VPCs, whether disk encryption is enabled for the ECS instances, and whether the ECS instances are bound to public IPv4 addresses.|
|OSS buckets|Checks whether server-side encryption by using Key Management Service \(KMS\), default server-side encryption, and log storage are enabled for OSS buckets.|
|ApsaraDB RDS instances|Checks whether historical event logging and transparent data encryption \(TDE\) are enabled for ApsaraDB RDS instances and whether the instances support multi-zone deployment.|
|ActionTrail trails|Checks whether an enabled ActionTrail trail exists and whether the trail records all types of event logs.|

