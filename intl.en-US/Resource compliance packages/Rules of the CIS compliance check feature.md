# Rules of the CIS compliance check feature

The following table describes the rules that are supported by the CIS compliance check feature.

|Rule|Logic|
|----|-----|
|Encryption is enabled for ECS data disks.|If encryption is enabled for each ECS data disk, the configuration is considered compliant.|
|The network type of the ECS instance is VPC.|If no parameter is set, the system checks whether the network type of each ECS instance is set to VPC. If you specify the required parameter, the system checks whether the VPC where ECS instances reside matches the specified setting. If yes, the configuration is considered compliant.|
|The server-side OSS-managed encryption feature is enabled for OSS buckets.|If server-side encryption is enabled for each OSS bucket, the configuration is considered compliant.|
|The network access settings of the security group are valid.|If the specified port or the specified CIDR block is allowed network access, the configuration is considered compliant.|
|Not all networks are allowed access to high-risk ports of the security group.|If 0.0.0.0/0 is added to the IP whitelist of each security group and port 22 or 3389 is closed, the configuration is considered compliant.|
|Not all networks are allowed access to ApsaraDB RDS instances.|If 0.0.0.0/0 is not added to the IP whitelist of each ApsaraDB RDS instance, the configuration is considered compliant.|
|MFA is enabled for RAM users.|If multi-factor authentication \(MFA\) is enabled for RAM users, the configuration is considered compliant.|
|Each Alibaba Cloud account does not have enabled AccessKey pairs.|If no Alibaba Cloud account has enabled AccessKey pairs, the configuration is considered compliant.|
|MFA is enabled for each Alibaba Cloud account.|If MFA is enabled for the Alibaba Cloud account, the configuration is considered compliant.|
|The password policy of RAM users meets the requirements.|If the settings of a RAM password policy meet the specified values, the configuration is considered compliant.|
|No super administrator exists.|If the Action parameter of RAM users, RAM user groups, and RAM roles are not set to \*, the configuration is considered compliant. In this case, \* indicates the super administrator permission.|
|No permission policy is attached to RAM users.|If no permission policy is attached to RAM users, the configuration is considered compliant.|
|The log storage feature is enabled for OSS buckets.|If the log storage feature is enabled for OSS buckets, the configuration is considered compliant.|
|OSS buckets are encrypted by using the BYOK method.|If OSS buckets are encrypted by using the bring your own key \(BYOK\) method, the configuration is considered compliant.|
|The SQL audit feature is enabled for ApsaraDB RDS instances.|If the SQL audit feature is enabled for ApsaraDB RDS instances, the configuration is considered compliant.|
|The retention period of the SQL audit logs for ApsaraDB RDS instances meets the specified requirement.|If the retention period of the SQL audit logs for ApsaraDB RDS instances meets the specified value, the configuration is considered compliant. Default value: 180 days.|
|The log\_connections parameter of PostgreSQL databases is set to on.|If the log\_connections parameter of PostgreSQL databases on each ApsaraDB RDS instance is set to on, the configuration is considered compliant.|
|The log\_disconnections parameter of PostgreSQL databases is set to on.|If the log\_disconnections parameter of PostgreSQL databases on each ApsaraDB RDS instance is set to on, the configuration is considered compliant.|
|The log\_duration parameter of PostgreSQL databases is set to on.|If the log\_duration parameter of PostgreSQL databases on each ApsaraDB RDS instance is set to on, the configuration is considered compliant.|
|You cannot grant permissions to anonymous accounts in the authorization policies of OSS buckets.|If the read and write permission of OSS buckets is set to private and no read or write permission is granted to anonymous account in authorization polices, the configuration is considered compliant.|
|Configure security access in the authorization policy of each OSS bucket.|If the authorization policy of each OSS bucket includes settings that allow HTTPS request and deny HTTP requests, the configuration is considered compliant.|
|Set IP limits in the authorization policy of each OSS bucket.|If the authorization policy of each OSS bucket includes the required IP whitelists, the configuration is considered compliant.|
|The Security Center agent.is installed on ECS instances.|If the Security Center agent.is installed on ECS instances, the configuration is considered compliant.|
|The vulnerabilities of all ECS instances are fixed.|If the vulnerabilities that are identified by Security Center on all ECS instances are fixed, the configuration is considered compliant.|
|Routing information is specified for each custom VPC CIDR block.|If the related route table includes at least one entry that indicates the routing information of IP addresses for a custom VPC CIDR block, the configuration is considered compliant.|
|The historical event log feature is enabled for ApsaraDB RDS instances.|If the historical event log feature is enabled for ApsaraDB RDS instances, the configuration is considered compliant.|
|The RAM user has logged on within the specified time.|If the RAM user has logged on in the last 90 days, the configuration is considered compliant. If the latest logon time is empty, the system checks the update time of the RAM user.|
|The flow log feature is enabled for VPCs.|If the flow log feature is enabled for VPCs, the configuration is considered compliant.|
|The TDE encryption feature is enabled for ApsaraDB RDS instances.|If the TDE encryption feature is enabled in the data security settings of each ApsaraDB RDS instance, the configuration is considered compliant.|
|The SSL certificate feature is enabled for ApsaraDB RDS instances.|If the SSL certificate feature is enabled in the data security settings of each ApsaraDB RDS instances, the configuration is considered compliant.|

