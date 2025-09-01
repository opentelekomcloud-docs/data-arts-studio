:original_name: dataartsstudio_01_0117.html

.. _dataartsstudio_01_0117:

Adding Workspace Members and Assigning Roles
============================================

For IAM users with **DARTS User** account permissions, their permissions in a DataArts Studio workspace are determined by workspace roles. If you want to share a DataArts Studio instance with an IAM user with the **DARTS User** account permissions, prepare an IAM user by referring to :ref:`Creating an IAM User and Assigning DataArts Studio Permissions <dataartsstudio_01_0004>`, add the user as a workspace member, and assign a role to the member.


.. figure:: /_static/images/en-us_image_0000002424508617.png
   :alt: **Figure 1** Permission system

   **Figure 1** Permission system

A workspace role determines the permissions of a user in a workspace. Preset roles include admin, developer, deployer, operator, and viewer. You can also customize roles by referring to :ref:`(Optional) Defining a Workspace Role <dataartsstudio_01_0107>`. For the detailed descriptions of the permissions of each role, see "Permissions" in *Service Overview*.

-  Admin: This role has all operation permissions in a workspace. You are advised to assign the admin role to the project owner, development owner, and O&M administrator.
-  Developer: This role has permissions to create and manage resources in a workspace. You are advised to assign this role to users who develop and process tasks.
-  Operator: This role has the operation permissions of services such as O&M and scheduling in a workspace, but cannot modify resources or configurations. You are advised to assign this role to users responsible for O&M management and status monitoring.
-  Viewer: This role can view data in a workspace but cannot perform any other operation. You are advised to assign this role to users who only need to view data in a workspace but do not need to perform operations.
-  Deployer: This role is unique to the enterprise mode and has permissions to release task packages in a workspace. In enterprise mode, when a developer submits a script or job version, the system generates a release task. After the developer confirms the release and the deployer approves the release request, the modified job is synchronized to the production environment.
-  Custom roles: If the preset roles cannot meet your requirements, you can create custom roles. You can configure permissions for such roles to meet the the principle of least privilege (PoLP).

Context
-------

If an IAM user is granted the **DARTS User** permissions, you also need to add the user as a workspace member and assign a role to the user. Otherwise, the IAM user cannot view existing DataArts Studio workspaces.

Notes and Constraints
---------------------

Due to the limitations of the authentication cache mechanism, a change to the role of a workspace member does not take effect immediately. The change takes effect six minutes after the workspace member stops accessing the DataArts Studio console.

Prerequisites
-------------

You are using either of the following accounts:

-  **DARTS** **Administrator** or **Tenant Administrator**
-  **DARTS User**, which is the administrator of the current workspace

Adding a Member and Assigning a Role
------------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002234235668.png
      :alt: **Figure 2** Workspace Information dialog box

      **Figure 2** Workspace Information dialog box

#. Click **Add** next to **Workspace Members**. In the displayed **Add Member** dialog box, select **User** or **Group** for **Account Type**, select a user or group from the **Member Account** drop-down list, and select a role.


   .. figure:: /_static/images/en-us_image_0000002269198449.png
      :alt: **Figure 3** Adding a member

      **Figure 3** Adding a member

#. Click **OK**. You can view or modify the members and roles in the member list, or delete members from the workspace.

Related Operations
------------------

-  Removing a workspace member: In the **Workspace Information** dialog box, select the workspace members to remove, and click **Remove**. In the **Remove Member** dialog box, click **Yes**.

   .. note::

      The creator of a workspace cannot be removed.


   .. figure:: /_static/images/en-us_image_0000002234239000.png
      :alt: **Figure 4** Removing a member

      **Figure 4** Removing a member
