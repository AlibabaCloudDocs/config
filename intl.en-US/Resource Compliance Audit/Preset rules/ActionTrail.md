# ActionTrail

This topic describes the managed rules that are related to ActionTrail and the methods to fix non-compliance issues.

## actiontrail-enabled

Checks whether you have created a trail and enabled logging for the trail.

Trigger type: configuration change

Applicable resource type: ACS::ActionTrail::Trail

Input parameter: none

Cause: Logging is not enabled for a trail of your account. Solution: Turn on the **Status** switch for the trail. Cloud Config detects the configuration change and starts to re-evaluate the resource within 10 minutes. You can fix this non-compliance issue by using one of the following methods:

-   ActionTrail console
    1.  Log on to the [ActionTrail console](https://actiontrail.console.aliyun.com).
    2.  In the left-side navigation pane, choose **ActionTrail** \> **Trails**.
    3.  On the **Trails** page, find the trail and click the trail name. On the page that appears, turn on the **Status** switch.
-   API

    You can also call the StartLogging API operation to enable logging. For more information, see [StartLogging](/intl.en-US/API Reference/Tracking-related APIs/StartLogging.md).


