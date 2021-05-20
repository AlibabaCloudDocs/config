# Modify an account group

The management account of a resource directory can modify the name or description of an account group. It can also add or remove member accounts from the account group. After an account group is modified, you must manually refresh the tabs of the account group on the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages by using the management account.

A management account is used to log on to the Cloud Config console.

**Note:** Custom account groups can be modified whereas global account groups cannot.

The following table shows the impacts on the management account and member accounts if a member account is added to or removed from an account group.

|Operation|Impacts on the management account|Impacts on member accounts|
|---------|---------------------------------|--------------------------|
|Add a member account to the account group|-   The management account can query the resources of the member account.
-   The rules and compliance packages created in the account group by the management account take effect on the member account.
-   The delivery methods of resource data and notification methods of resource events configured by the management account take effect on the member account.

|-   If a service-linked role for Cloud Config has not been created for the member account, the role is automatically created.
-   The existing rules and compliance packages of the member account are retained.
-   The delivery methods of resource data and notification methods of resource events configured for the member account are automatically cleared. The configuration permissions for the member account are removed. The member account must follow the configurations of the management account.
-   On the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages, the member account can view the **Current Account** tab and the tab of the account group. The member account can view its own resources, and rules and compliance packages created by the management account in the account group. The member account cannot modify rules and compliance packages. When the member account views the details of rules and compliance packages, only its own resources are displayed.
-   The existing rules and compliance packages in the account group automatically take effect on the member account. |
|Remove a member account from a resource directory|-   The management account cannot query the resources of the member account.
-   The rules and compliance packages created in the account group by the management account no longer take effect on the member account.
-   The delivery methods of resource data and notification methods of resource events configured by the management account no longer take effect on the member account.

|-   On the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages, the member account can no longer view the **Current Account** tab and the tab of the account group.
-   The existing rules and compliance packages of the account group no longer take effect on the member account.
-   The service-linked role for Cloud Config of the member account is retained.
-   The rules and compliance packages created by the member account are retained.
-   The delivery methods of resource data and notification methods of resource events configured for the member account are automatically cleared. The member account regains the permissions to re-configure the delivery methods of resource data and notification methods of resource events.
-   The member account uses Cloud Config as an independent Alibaba Cloud account and is no longer managed by the management account. |

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Account Group**.

3.  On the **Account Group** page, find the account group that you want to modify. Click **Edit** in the **Actions** column.

4.  In the **Edit** panel, configure a name and description for the account group, and then click **Edit Member**.

5.  Specify member accounts from the resource directory and click **OK**.

    -   Add member accounts: In the **Resource Directories** section, select the member accounts that you want to add. In the **Selected Accounts** section, the member accounts are displayed.
    -   Remove member accounts: In the **Selected Accounts** section, clear the member accounts that you want to remove.
6.  Click **Submit**.

    In the **Account Group** list, view the modification results of the account group. You can also view the name, description, and member account quantity of the account group.


