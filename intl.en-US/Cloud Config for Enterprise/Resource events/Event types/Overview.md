# Overview

Cloud Config for Enterprise evaluates resource compliance in a continuous and automatic manner. It sends notifications of resource change events, resource non-compliance events, and resource snapshot delivery events to a specified topic of Message Service \(MNS\). This allows you to monitor the changes and compliance of your cloud resources at the earliest opportunity.

The following table describes the types of events that are supported by Cloud Config for Enterprise.

|Event type|Description|
|----------|-----------|
|[Resource change events]()|When a resource change is detected, Cloud Config for Enterprise sends a notification to you by using MNS.|
|[Resource non-compliance events]()|Cloud Config for Enterprise evaluates the compliance of your resources. If a resource is evaluated to be **non-compliant**, Cloud Config for Enterprise sends a notification to you by using MNS.|
|[Resource snapshot delivery events]()|When a resource snapshot is delivered to a specified Object Storage Service \(OSS\) bucket, Cloud Config for Enterprise sends a notification to you by using MNS.|

