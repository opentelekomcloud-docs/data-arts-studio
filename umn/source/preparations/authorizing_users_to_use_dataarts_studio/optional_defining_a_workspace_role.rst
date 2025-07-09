:original_name: dataartsstudio_01_0120.html

.. _dataartsstudio_01_0120:

(Optional) Defining a Workspace Role
====================================

For IAM users with the **DARTS User** permission, a workspace role determines their permissions in the workspace. Currently, five preset roles are available: admin, developer, deployer, operator, and viewer. For details about the permissions of each role, see "DataArts Studio Permissions" in *Service Overview*.

If the preset roles can meet your requirements, skip this section. Otherwise, create custom roles by following the instructions in this section.

Background
----------

-  The **DARTS** **Administrator** or **Tenant Administrator** account can create custom roles in a workspace.

Constraints
-----------

-  Due to the restriction of the authentication cache mechanism, when the permission of a custom role changes, the change does not take effect immediately for the workspace members with this role. The permission change takes effect only after the workspace members with this role stop accessing the DataArts Studio console and wait for 6 minutes.
-  Even if a custom role has the same permissions as the admin, the custom role cannot perform some operations that require the admin role for example, exporting all the APIs in DataArts DataService.

Procedure
---------

#. Log in to the DataArts Studio console as **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the **Roles** page, click **Create**. In the displayed dialog box, set the following parameters:

   -  **Role Name**: unique identifier of a custom role. You are advised to name the role to fit its application scenario and avoid any meaningless description.
   -  **Role Description**: description of the role, for example, the key permission differences between the role and preset roles
   -  **Role Type**: The role permissions in simple mode differ from those in enterprise mode. Select an appropriate role type based on the scenario. For details about the enterprise mode, see :ref:`DataArts Studio Enterprise Mode Overview <dataartsstudio_01_5099>`.

      -  If the role is used in a workspace in simple mode, select **CUSTOM**.
      -  If the role is used in the development environment of a workspace in enterprise mode, select **DEV_CUSTOM**.
      -  If the role is used in the production environment of a workspace in enterprise mode, select **PROD_CUSTOM**.

   -  **Reuse**: Use this function if you only need to slightly adjust the permissions of the preset roles to meet your requirements. Otherwise, you can directly select permissions for the role.

      .. important::

         When you create or edit a role, if your account has the **DARTS** **Administrator** or **Tenant Administrator** permission but the system still displays an error message indicating that you do not have the permission to perform this operation, you are advised to change another network and try again.

#. After configuring the role name, type, and permissions, click **OK**.
#. Set the IAM user as a custom role by referring to :ref:`Adding a Member and Assigning a Role <dataartsstudio_01_0117>`.
