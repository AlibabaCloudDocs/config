# Overview

Cloud Config evaluates resource compliance in a continuous and automatic manner. It sends notifications of resource changes events, resource non-compliance events, and resource snapshot delivery events to a specified topic of Message Service \(MNS\). This allows you to monitor the changes and compliance of your cloud resources at the earliest opportunity.

The following table describes the types of events that are supported by Cloud Config.

|Event type|Description|
|----------|-----------|
|[Resource change events](/intl.en-US/Events/Event types/Resource change events.md)|When a resource change is detected, Cloud Config sends a notification to you by using MNS.|
|[Resource non-compliance events](/intl.en-US/Events/Event types/Resource non-compliance events.md)|If a resource is evaluated to be non-compliant, Cloud Config sends a notification to you by using MNS.|
|[Resource snapshot delivery events](/intl.en-US/Events/Event types/Resource snapshot delivery events.md)|When a resource snapshot is delivered to a specified Object Storage Service \(OSS\) bucket, Cloud Config sends a notification to you by using MNS.|

