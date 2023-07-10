:original_name: dataartsstudio_01_0117_0.html

.. _dataartsstudio_01_0117_0:

Adding a Member and Assigning a Role
====================================

If you want to allow another IAM user to use your DataArts Studio instance, create an IAM user by referring to :ref:`Creating an IAM User and Assigning DataArts Studio Permissions <dataartsstudio_01_0004>`, and add the user as the workspace member and configure a role for the user by following the instructions in this section.

A workspace role determines the permissions of a user in the workspace. Currently, four preset roles are available: admin, developer, operator, and viewer. For details about the permissions of the roles, see "DataArts Studio Permissions" in *Service Overview*.

-  Admin: Users with this role have the permissions to perform all operations in a workspace. You are advised to assign this role to the project owner, development owner, and O&M administrator.
-  Developer: Users with this role have the permissions to create and manage work items, but cannot perform operations on workspaces, clusters, and reviewers. You are advised to assign this tole to users who develop and process tasks.
-  Operator: Users with this role have the permissions to perform operations such as O&M and scheduling, but cannot modify work items or configurations. You are advised to assign this role to users for O&M management and status monitoring.
-  Viewer: Users with this role can only read data from DataArts Studio, but cannot perform operations on workspaces or modify work items or configurations. You are advised to assign this role to users who only want to view information in the workspace but do not perform any operation.

Background
----------

The **DAYU** **Administrator** account or the administrator can add members to the workspace.


Adding a Member and Assigning a Role
------------------------------------

#. Log in to the DataArts Studio console and access the **Workspaces** page.
#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.
#. Click **Add** under **Workspace Members**. In the displayed **Add Member** dialog box, select **Add User** or **Add Group**, select a member account from the drop-down list, and select a role for it.
#. Click **OK**. You can view or modify the members and roles in the member list, or remove members from the workspace.

Removing a Workspace Member
---------------------------

#. Log in to the DataArts Studio console and access the **Workspaces** page.
#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.
#. On the **Workspace information** page, select the target member and click **Remove**.

   .. note::

      The creator of a workspace cannot be removed.

#. In the **Remove Member** dialog box displayed, click **Yes**.
