:original_name: dataartsstudio_01_0117.html

.. _dataartsstudio_01_0117:

Adding a Member and Assigning a Role
====================================

For IAM users with the **DARTS User** permission, a workspace role determines their permissions in the workspace. If you want to allow another IAM user with the **DARTS User** permission to use your DataArts Studio instance, create an IAM user by referring to :ref:`Creating an IAM User and Assigning DataArts Studio Permissions <dataartsstudio_01_0004>`, and add the user as the workspace member and configure a role for the user by following the instructions in this section.

A workspace role determines the permissions of a user in the workspace. Currently, the following preset roles are available: admin, developer, deployer, operator, and viewer. You can also customize roles based on :ref:`(Optional) Defining a Workspace Role <dataartsstudio_01_0120>`. For details about the permissions of each role, see "DataArts Studio Permissions" in *Service Overview*.

-  Admin: This role has all operation permissions in a workspace. You are advised to assign the admin role to the project owner, development owner, and O&M administrator.
-  Developer: This role has permissions to create and manage resources in a workspace. You are advised to assign this role to users who develop and process tasks.
-  Operator: This role has the operation permissions of services such as O&M and scheduling in a workspace, but cannot modify resources or configurations. You are advised to assign this role to users responsible for O&M management and status monitoring.
-  Viewer: This role can view data in a workspace but cannot perform any other operation. You are advised to assign this role to users who only need to view data in a workspace but do not need to perform operations.
-  Deployer: This role is unique to the enterprise mode and has permissions to release task packages in a workspace. In enterprise mode, when a developer submits a script or job version, the system generates a release task. After the developer confirms the release and the deployer approves the release request, the modified job is synchronized to the production environment.
-  Custom roles: If the preset roles cannot meet your requirements, you can create custom roles. You can configure permissions for such roles to meet the the principle of least privilege (PoLP).

Background
----------

If the permissions of **DARTS** **User** has been assigned to the created IAM user, you must add workspace members and roles. Otherwise, the IAM user cannot view existing DataArts Studio workspaces.

Constraints
-----------

Due to the limitation of the authentication cache mechanism, changes to the roles of workspace members do not take effect immediately. Instead, the changes take effect only after the workspace members stop accessing the DataArts Studio console and wait for 6 minutes.

Prerequisites
-------------

You have changed your account to either of the following:

-  **DARTS** **Administrator** or **Tenant Administrator**
-  **DARTS User**, which is the workspace administrator


Adding a Member and Assigning a Role
------------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002305437605.png
      :alt: **Figure 1** Workspace Information dialog box

      **Figure 1** Workspace Information dialog box

#. Click **Add** under **Workspace Members**. In the displayed **Add Member** dialog box, select **Add User** or **Add Group**, select a member account from the drop-down list, and select a role for it.


   .. figure:: /_static/images/en-us_image_0000002305438069.png
      :alt: **Figure 2** Adding a member

      **Figure 2** Adding a member

#. Click **OK**. You can view or modify the members and roles in the member list, or remove members from the workspace.

Related Operations
------------------

-  Remove workspace members: In the **Workspace Information** dialog box, select the members to remove and click **Remove**. In the **Remove Member** dialog box, click **Yes**.

   .. note::

      The creator of a workspace cannot be removed.


   .. figure:: /_static/images/en-us_image_0000002305404981.png
      :alt: **Figure 3** Removing members

      **Figure 3** Removing members
