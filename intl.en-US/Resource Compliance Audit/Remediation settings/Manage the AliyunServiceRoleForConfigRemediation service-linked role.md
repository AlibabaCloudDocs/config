# Manage the AliyunServiceRoleForConfigRemediation service-linked role

This topic describes the scenarios and policy of the AliyunServiceRoleForConfigRemediation service-linked role that is used for automatic remediation. This topic also describes how to create and delete the service-linked role.

## Scenarios

Before you use the automatic remediation feature of Cloud Config to remediate non-compliant resources, you must obtain the permissions to access the non-compliant resources. Cloud Config provides a service-linked role named AliyunServiceRoleForConfigRemediation that you can assume to access non-compliant resources across services.

**Note:** For more information about service-linked roles, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Background information

The following list describes the details of the AliyunServiceRoleForConfigRemediation service-linked role of Cloud config:

-   Role name: AliyunServiceRoleForConfigRemediation.
-   Policy attached to the role: AliyunServiceRolePolicyForConfigRemediation.
-   Policy description: This policy grants Cloud Config access to the resources of related cloud services.

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:TagResources",
            "vpc:TagResources",
            "dds:TagResources",
            "polardb:TagResources",
            "rds:TagResources",
            "kvstore:TagResources",
            "slb:TagResources",
            "oss:PutBucketTagging",
            "oss:GetBucketTagging",
            "nas:AddTags",
            "cdn:TagResources",
            "cbn:TagResources",
            "hbase:TagResources",
            "cen:TagResources",
            "cs:GetClusterInfo",
            "cs:UpdateClusterTags",
            "ddoscoo:CreateTagResources",
            "cdn:SetDomainServerCertificate",
            "oss:PutBucketACL",
            "oss:PutBucketReferer",
            "oss:PutBucketEncryption",
            "ecs:ModifyInstanceAttribute",
            "slb:SetLoadBalancerDeleteProtection",
            "actiontrail:CreateTrail",
            "actiontrail:StartLogging",
            "composer:InvokeFlow",
            "composer:GroupInvokeFlow",
            "composer:CreateFlow",
            "oos:StartExecution",
            "tag:TagResources",
            "tag:ListTagResources"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": "ram:PassRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "acs:Service": [
                "composer.aliyuncs.com",
                "oos.aliyuncs.com"
              ]
            }
          }
        },
        {
          "Action": "ram:DeleteServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "remediation.config.aliyuncs.com"
            }
          }
        }
      ]
    }
    ```


## Create a service-linked role for automatic remediation

You can configure a remediation template for a compliance rule in the Cloud Config console. If Cloud Config detects non-compliant resources based on the rule, Cloud Config creates a service-linked role named AliyunServiceRoleForConfigRemediation for automatic remediation in the RAM console.

## Delete the AliyunServiceRoleForConfigRemediation service-linked role

1.  Delete the remediation settings of a rule.
    -   You can delete the remediation settings of a rule. For more information, see [Delete remediation settings](/intl.en-US/Resource Compliance Audit/Remediation settings/Delete remediation settings.md).
    -   You can delete all the rules whose remediation settings have been configured. For more information, see [Delete a rule](/intl.en-US/Resource Compliance Audit/Manage rules/Delete a rule.md).
2.  Delete the AliyunServiceRoleForConfigRemediation service-linked role.

    For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).


## References

-   [Configure automatic remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure automatic remediation.md)
-   [Configure manual remediation](/intl.en-US/Resource Compliance Audit/Remediation settings/Configure manual remediation.md)
-   [Delete remediation settings](/intl.en-US/Resource Compliance Audit/Remediation settings/Delete remediation settings.md)

