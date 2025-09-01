:original_name: dataartsstudio_01_0107.html

.. _dataartsstudio_01_0107:

(Optional) Defining a Workspace Role
====================================

For IAM users with **DARTS User** account permissions, DataArts Studio workspace roles determine their permissions in workspaces. Preset roles include admin, developer, deployer, operator, and viewer. For details about the permissions of each role, see "Permissions" in *Service Overview*.

If the preset roles meet your needs, skip this section. Otherwise, create custom roles by following the instructions in this section.

Context
-------

-  **DARTS** **Administrator** or **Tenant Administrator** can create custom roles in a workspace.

Notes and Constraints
---------------------

-  Due to the constraints of the authentication cache mechanism, when the permissions of a custom role change, permissions of the members of the workspace that this role has been associated with will not be updated immediately. Instead, the updated permissions take effect six minutes after the workspace members with this role stop accessing the DataArts Studio console.
-  A custom role with the same permissions as the workspace admin cannot perform some operations that can only be performed by the admin.

Procedure
---------

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the **Roles** page, click **Create**. In the displayed dialog box, set the following parameters:

   -  **Role Name**: unique identifier of a custom role. You are advised to name the role to fit its application scenario and avoid any meaningless description.
   -  **Role Description**: description of the role, for example, the key permission differences between the role and preset roles
   -  **Role Type**: Select a proper type based on where this role will be used. Role permissions differ in the simple and enterprise mode. For details about the enterprise mode, see :ref:`DataArts Studio Enterprise Mode Overview <dataartsstudio_01_5099>`.

      -  If you want to use this role in a workspace in simple mode, select **DEV&PROD_CUSTOM**.
      -  If you want to use this role in the development environment of a workspace in enterprise mode, select **DEV_CUSTOM**.
      -  If you want to use this role in the production environment of a workspace in enterprise mode, select **PROD_CUSTOM**.

   -  **Reuse**: Use this function if you only need to slightly adjust the permissions of the preset roles to meet your requirements. Otherwise, you can directly select permissions for the role.

      .. important::

         When you create or edit a role, an error message indicating insufficient permissions may be displayed even if you have the **DARTS** **Administrator** or **Tenant Administrator** permissions. This may be caused by network constraints. You can change another network and try again.

#. After configuring the role name, type, and permissions, click **OK**.
#. Assign the created custom role to the IAM user by following the instructions in :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.
