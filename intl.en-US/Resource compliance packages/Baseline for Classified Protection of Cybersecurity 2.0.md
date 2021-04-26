# Baseline for Classified Protection of Cybersecurity 2.0

This topic describes Baseline for Classified Protection of Cybersecurity 2.0 and the protection screening feature of Cloud Config.

## What is Baseline for Classified Protection of Cybersecurity 2.0?

Baseline for Classified Protection of Cybersecurity 2.0 stipulates the national cybersecurity standards in China. The Chinese government officially released it on May 13, 2019 and officially implemented it on December 1, 2019. Currently, 58% of the countries and regions in the world have formulated national strategies for cybersecurity. Major countries and regions have legislated for cybersecurity. The following figure shows the development of Baseline for Classified Protection of Cybersecurity 2.0.

## Important changes in Baseline for Classified Protection of Cybersecurity 2.0

-   Information systems on the cloud can be evaluated.

    Based on Baseline for Classified Protection of Cybersecurity 1.0, Baseline for Classified Protection of Cybersecurity 2.0 adds specifications for cloud computing platforms, big data platforms, Internet of Things \(IoT\) platforms, mobile computing systems, and industrial control systems. The specifications fully consider the diversity and complexity of the business carried by current enterprise information systems.

-   Cloud vendors and cloud tenants are evaluated separately.

    In Baseline for Classified Protection of Cybersecurity 1.0, the level of a cloud platform on which enterprise resources are hosted determines the level of an information system that a cloud tenant builds on the platform. As cloud services become increasingly complex and flexible, cloud tenants have increased control over hosted resources. Therefore, from Baseline for Classified Protection of Cybersecurity 2.0 on, the information systems built by cloud tenants on cloud platforms will be evaluated independently.

-   Continuous security evaluation is emphasized.

    According to Baseline for Classified Protection of Cybersecurity 1.0, the compliance of a system is evaluated only once. After the evaluation is completed, you cannot monitor whether the system can continuously be compliant with the specifications. Baseline for Classified Protection of Cybersecurity 2.0 integrates the requirement for continuous compliance into the specifications to guide and supervise enterprises so they can build information systems with sustainable security capabilities. Based on the policy-centered protection, detection, and response \(PPDR\) model, enterprises are instructed to construct a three-dimensional and in-depth defense system that is trusted, controllable, and manageable. The defense system must be constructed based on security authentication and with access control as the core.

    |Requirement|Description|
    |-----------|-----------|
    |Trusted|Construct a trusted execution environment for business systems based on trusted computing. To prevent users from being impersonated and prevent viruses and intrusions, users, platforms, and applications must be trusted. A trusted environment guarantees the security and reliability of the business systems, which always run as expected with no unexpected processes.|
    |Controllable|Enable subjects to control the access behavior of objects based on access control to make sure that all access activities are controllable. Controlled access effectively prevents both internal and external attacks. Controlled access also protects information systems from unauthorized operations and unauthorized resource access. This guarantees that information systems are secure and controllable.|
    |Manageable|Construct a management platform that allows administrators to manage permissions in a centralized and hierarchical way and grant minimal permissions to users for better system management. Such a management platform makes up for less focus on management. This also guarantees that information systems are secure and controllable.|

    Baseline for Classified Protection of Cybersecurity 2.0 uses "one center, triple protection" as the design philosophy for cybersecurity technology. One center refers to the security management center. Triple protection refers to the secure computing environment, the security zone border, and the secure communications network.

    -   The security management center must implement centralized control in system management, security management, and audit management. The protection must be transformed from passive to active, from static to dynamic, from single-point to all-around, and from extensive to precise.
    -   Triple protection requires enterprises to use security devices and technologies to implement security measures such as identity authentication, access control, intrusion prevention, data integrity, confidentiality, and personal information protection. Triple protection enables all-around protection for cloud platforms.

The following table lists the differences between Baseline for Classified Protection of Cybersecurity 1.0 and 2.0.

|Baseline for Classified Protection of Cybersecurity 1.0|Baseline for Classified Protection of Cybersecurity 2.0|
|-------------------------------------------------------|-------------------------------------------------------|
|In-depth defense with attack prevention, attack response, and security audit.|All-around defense with active prevention, security authentication, threat detection, and comprehensive audit.|
|If the evaluation points are greater than 0, the official evaluation is passed. The official evaluation for Level 3 Protection of Cybersecurity is required every year and that for Level 4 Protection of Cybersecurity is required every six months.|If the evaluation points reach 75, the official evaluation is passed. Annual evaluation is required for both Level 3 Protection of Cybersecurity and Level 4 Protection of Cybersecurity.|

## Five difficulties for information systems on the cloud to conform to Baseline for Classified Protection of Cybersecurity 2.0

Baseline for Classified Protection of Cybersecurity 2.0 focuses on continuous compliance supervision and requires annual evaluation for both Level 3 Protection of Cybersecurity and Level 4 Protection of Cybersecurity. Information systems on the cloud have difficulties in conforming to Baseline for Classified Protection of Cybersecurity 2.0 because resources are hosted on the cloud.

|Difficulty|Description|
|----------|-----------|
|Unclear evaluation targets|Some concepts of the virtualized IT infrastructure are different from those of the traditional IT infrastructure. Evaluating complex cloud configurations becomes difficult.|
|Non-centralized resource management|If a cloud platform does not support configuration management databases \(CMDBs\), you have to endure a cumbersome process of providing evidence and demonstrating information systems on the cloud to authoritative agencies during the repeated evaluation and rectification.|
|Less control over the system data|Resources are hosted on the cloud. You must obtain security audits from the cloud platform if Baseline for Classified Protection of Cybersecurity 2.0 requires management logs and compliance reports as evidence.|
|Impossible self-evaluation by writing code|In the past, all enterprises had on-premises CMDBs and could write code to monitor and evaluate configurations on their own before the official evaluation. However, resources are now hosted on the cloud. Evaluating configurations on their own by writing code requires continuous configuration synchronization from the cloud, which is too costly.|
|Separated deployment of a business system|If the deployment mode is hybrid cloud, a business system is deployed separately on the cloud and on-premises. In this case, you must perform self-evaluation, scanning, monitoring, or detection twice, which leads to large costs in labor and time.|

## Continuous monitoring on cloud platforms

To resolve the preceding difficulties, Alibaba Cloud provides the protection screening feature in Cloud Config free of charge. This feature assists enterprises in self-evaluation and rectification.

Cloud Config interprets the specifications of Baseline for Classified Protection of Cybersecurity 2.0 as rules, continuously monitors resource changes, evaluates resource compliance in real time, and triggers alerts for non-compliance. This informs enterprises in a timely manner whether information systems on the cloud are compliant.

![Evaluation process of Baseline for Classified Protection of Cybersecurity 2.0](../images/p88109.png)

## Features

Based on Baseline for Classified Protection of Cybersecurity 2.0, Cloud Config provides the following features:

-   Rules based on Baseline for Classified Protection of Cybersecurity 2.0: Cloud Config interprets the specifications of Baseline for Classified Protection of Cybersecurity 2.0 as rules. Before the official evaluation, you can enable continuous protection screening with one click.
-   Dynamic, continuous, and controllable evaluation: Cloud Config continuously tracks resource changes and evaluates resources in real time according to rules. According to Baseline for Classified Protection of Cybersecurity 2.0, if the evaluation points reach 75, the evaluation targets conform to the standards. In this case, you can stop or ignore the evaluation of compliant resources and skip persistent alerts that do not require attention.
-   Alerts for non-compliance and automatic rectification: Cloud Config allows you to subscribe to notifications for resources that are not compliant with Baseline for Classified Protection of Cybersecurity 2.0 and remediate non-compliant resources on the cloud. Cloud Config also supports automatic rectification after you specify the rectification logic for specific specifications.
-   Protection screening report download: You can download the protection screening reports to a local computer. This facilitates local task allocation and rectification on the cloud. The reports can also be presented as a piece of evidence to authoritative agencies.

