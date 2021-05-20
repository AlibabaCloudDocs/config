# Delete an account group

The management account of a resource directory can delete an account group. After an account group is deleted, the management account can no longer view the resources of all member accounts in the account group in a centralized manner. The rules and compliance packages created by the management account in the account group are also deleted and cannot be restored. However, the rules and compliance packages created by member accounts in the account group are retained.

A management account is used to log on to the Cloud Config console.

After you delete an account group, the following changes occur to Cloud Config:

-   The tabs of the account group disappear from the **Overview**, **Resources**, **Compliance Package**, and **Rules** pages.
-   The rules and compliance packages of the account group are deleted and cannot be recovered.
-   All compliance results generated in the account group are automatically deleted and cannot be restored.
-   Service-linked roles for Cloud Config of member accounts in the account group are retained.
-   If the account groups to which a member account belongs are all deleted, the member account uses Cloud Config as an independent Alibaba Cloud account.

1.  Log on to the [Cloud Config console](https://config.console.aliyun.com).

2.  In the left-side navigation pane, click **Account Group**.

3.  On the **Account Group** page, find the account group that you want to delete. Click **Delete** in the **Actions** column.

4.  In the **Delete** dialog box, click **OK**.


