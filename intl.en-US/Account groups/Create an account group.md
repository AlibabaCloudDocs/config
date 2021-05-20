# Create an account group

The management account of a resource directory can create an account group in the Cloud Config console. This way, the resources, compliance packages, and rules of multiple member accounts in the account group can be managed in a centralized manner. If you need to apply the same compliance packages and rules to multiple member accounts, we recommend that you add these member accounts to an account group.

A management account is used to log on to the Cloud Config console.

After you create an account group, the following changes occur to Cloud Config:

-   On the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages, the tabs of the account group appear. If you create multiple account groups, tabs of all the account groups appear on the preceding listed pages. Multiple account groups may contain a member account at the same time. The resources of a member account in different account groups are the same. However, the compliance check results of a member account in different account groups may be different due to a difference of account group rules.
-   Cloud Config creates a service-linked role for Cloud Config for the member accounts of an account group. The service-linked role allows Cloud Config to obtain the resource configurations of member accounts.
-   Cloud Config creates a resource list for each member account. The process takes about 2 to 10 minutes.

The following table describes the types of account groups supported by Cloud Config.

|Account group type|Description|
|------------------|-----------|
|Global account group|If you create a global account group, all the member accounts of a resource directory are added to the global account group. If the management account configures a global account group, new member accounts of the resource directory are automatically added to the global account group. This keeps the consistency of the member accounts on which compliance management is implemented.

A management account can create only one global account group. |
|Custom account group|If you create a custom account group, you must manually add all or some member accounts from a resource directory to the custom account group. New member accounts of the resource directory are not automatically added to the global account group. You must manually add the member accounts to the custom account group by using the management account.

If the management account removes a member account from the resource directory, it loses the compliance management permissions on the member account. Therefore, the member account is removed from the custom account group.

If the management account does not configure a global account group for the resource directory, a custom account group is used by default. Even if all member accounts in the resource directory are added to the custom account group, the account group is still a custom account group. |

## Create a global account group

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Account Group**.

3.  On the **Account Group** page, click **Create**.

4.  In the **Create** panel, configure a name and description for the account group, and then set **Account Group Type** to **Global**.

5.  Click **Submit**.

    In the **Account Group** list, find the account group that you created. If the status of the account group is **Created**, the account group is created. You can also view the name, description, member account quantity, type, and creation time of the account group.


## Create a custom resource group.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Account Group**.

3.  On the **Account Group** page, click **Create**.

4.  In the **Create** panel, configure a name and description for the account group, and then click **Add Member**.

5.  Specify member accounts from the resource directory and click **OK**.

6.  Click **Submit**.

    In the **Account Group** list, find the account group that you created. If the status of the account group is **Created**, the account group is created. You can also view the name, description, member account quantity, type, and creation time of the account group.


