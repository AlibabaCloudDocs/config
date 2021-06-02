# MLPS 2.0

This topic describes Multi-Level Protection Scheme \(MLPS\) 2.0 and the classified protection precheck feature of Cloud Config.

## What is MLPS 2.0?

MLPS 2.0 stipulates the national cybersecurity standards in China. The Chinese government officially released it on May 13, 2019 and officially implemented it on December 1, 2019. 58% of the countries and regions in the world have formulated national strategies for cybersecurity. Major countries and regions have legislated for cybersecurity.

## Important changes in MLPS 2.0

-   Information systems in the cloud can be evaluated.

    On the basis of MLPS 1.0, MLPS 2.0 adds specifications for cloud computing platforms, big data platforms, Internet of Things \(IoT\) platforms, mobile computing systems, and industrial control systems. The specifications fully consider the diversity and complexity of the business carried by current enterprise information systems.

-   Cloud vendors and cloud tenants are separately evaluated.

    In MLPS 1.0, the level of a cloud platform on which enterprise resources are hosted determines the level of an information system that a cloud tenant builds on the platform. As cloud services become increasingly complex and flexible, cloud tenants have increased control over hosted resources. Therefore, from MLPS 2.0 on, the information systems built by cloud tenants on cloud platforms are independently evaluated.

-   Continuous security evaluation is emphasized.

    In MLPS 1.0, the compliance of a system is evaluated only once. After the evaluation is complete, you cannot continuously monitor the system to check whether it is compliant with the specifications. MLPS 2.0 integrates the requirement for continuous compliance into the specifications to guide and supervise enterprises so that they can build information systems with sustainable security capabilities. On the basis of the policy-centered protection, detection, and response \(PPDR\) model, enterprises are instructed to construct a three-dimensional and in-depth defense system that is trusted, controllable, and manageable. The defense system must be constructed based on security authentication and with access control as the core.

    |Requirement|Description|
    |-----------|-----------|
    |Trusted|Construct a trusted execution environment for business systems based on trusted computing. To prevent users from being impersonated and prevent viruses and intrusions, users, platforms, and applications must be trusted. A trusted environment guarantees the security and reliability of the business systems, which always run as expected with no unexpected processes.|
    |Controllable|Enable subjects to control the access behavior of objects based on access control to make sure that all access activities are controllable. Controlled access prevents both internal and external attacks. Controlled access also protects information systems from unauthorized operations and unauthorized resource access. This ensures that information systems are secure and controllable.|
    |Manageable|Construct a management platform that allows administrators to manage permissions in a centralized and hierarchical way and grant minimal permissions to users for better system management. Such a management platform makes up for less focus on management. This also ensures that information systems are secure and controllable.|

    MLPS 2.0 uses "one center, triple protection" as the design philosophy for cybersecurity technology. One center refers to the security management center. Triple protection refers to the secure computing environment, the security zone border, and the secure communications network.

    -   The security management center must implement centralized control on system management, security management, and audit management. The protection mode must be transformed from passive to active, from static to dynamic, from single-point to all-around, and from extensive to precise.
    -   Triple protection requires enterprises to use security devices and technologies to implement security measures such as identity authentication, access control, intrusion prevention, data integrity, confidentiality, and personal information protection. Triple protection enables all-around protection for cloud platforms.

The following table describes the differences between MLPS 1.0 and MLPS 2.0.

|MLPS 1.0|MLPS 2.0|
|--------|--------|
|In-depth defense with attack prevention, attack response, and security audit.|All-around defense with active prevention, security authentication, threat detection, and comprehensive audit.|
|If the evaluation points are greater than 0, the official evaluation is passed. The official evaluation for MLPS 1.0 Level 3 is required every year and that for MLPS 1.0 Level 4 is required every six months.|If the evaluation points reach 75, the official evaluation is passed. Annual evaluations are required for both MLPS 2.0 Level 3 and MLPS 2.0 Level 4.|

## Five difficulties for information systems in the cloud to conform to MLPS 2.0

MLPS 2.0 focuses on continuous compliance supervision. Annual evaluations are required for both MLPS 2.0 Level 3 and MLPS 2.0 Level 4. Information systems in the cloud have difficulties in conforming to MLPS 2.0 because resources are hosted on the cloud. The following table describes the difficulties.

|Difficulty|Description|
|----------|-----------|
|Unclear evaluation objects|Some concepts of the virtualized IT infrastructure are different from those of the traditional IT infrastructure. Evaluating complex cloud configurations becomes difficult.|
|Non-centralized resource management|If a cloud platform does not support configuration management databases \(CMDBs\), you must endure a cumbersome process of providing evidence and demonstrating information systems in the cloud to authoritative agencies during the repeated evaluation and remediation.|
|Less control over the system data|Resources are hosted on the cloud. You must obtain security audit data from the cloud platform if MLPS 2.0 requires management logs and compliance reports as evidence.|
|Impossible self-evaluation by writing code|In the past, all enterprises had on-premises CMDBs and could write code to monitor and evaluate configurations on their own based on the compliance requirements before the official evaluation. However, resources are now hosted on the cloud. Evaluating configurations on their own by writing code requires continuous configuration synchronization from the cloud, which incurs high costs.|
|Separated deployment of a business system|If the deployment mode is hybrid cloud, a business system is separately deployed on the cloud and on-premises. In this case, you must perform self-evaluation, scanning, monitoring, or detection twice, which leads to high labor costs is time-consuming.|

## Continuous monitoring on cloud platforms

To resolve the preceding difficulties, Alibaba Cloud provides the classified protection precheck feature in Cloud Config free of charge. This feature assists enterprises in self-evaluation and remediation.

Cloud Config interprets the specifications of MLPS 2.0 as rules, continuously monitors resource configuration changes, evaluates resource compliance in real time, and triggers alerts for non-compliance. This allows enterprises to continuously monitor the compliance of information systems.

## Features

Cloud Config provides the following features based on MLPS 2.0:

-   Rules based on MLPS 2.0: Cloud Config interprets the specifications of MLPS 2.0 as rules. Before the official evaluation, you can enable classified protection precheck with a few clicks.
-   Dynamic, continuous, and controllable evaluation: Cloud Config continuously tracks resource configuration changes and evaluates resources in real time based on rules. As stipulated by MLPS 2.0, if the evaluation points reach 75, the evaluation objects conform to the standards. In this case, you can stop or ignore the evaluation of compliant resources and skip persistent alerts that do not require attention.
-   Alerts for non-compliance and automatic remediation: Cloud Config allows you to subscribe to notifications for resources that are not compliant with MLPS 2.0 and correct non-compliant resources in the cloud. Cloud Config also supports automatic remediation after you specify the remediation logic for specific specifications.
-   Export of the reports for classified protection precheck: You can download the reports for classified protection precheck to your computer. This facilitates on-premises task allocation and remediation in the cloud. The reports can also be presented as a piece of evidence to authoritative agencies.

