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
-  A custom role with the same permissions as the workspace admin cannot perform some operations that can only be performed by the admin, for example, exporting all APIs in DataArts DataService.

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


   .. figure:: /_static/images/en-us_image_0000002234240220.png
      :alt: **Figure 1** Creating a custom role

      **Figure 1** Creating a custom role

#. After configuring the role name, type, and permissions, click **OK**.

#. Assign the created custom role to the IAM user by following the instructions in :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.

Example 1
---------

A data operations engineer who wants to use the DataArts DataService module of DataArts Studio requires only the permissions of DataArts DataService. If the administrator assigns the preset developer role to the data operations engineer, the engineer also has permissions of other modules, which may pose risks.

To address this issue, the administrator can create a custom role **Developer_DataService** based on the preset developer role with the addition, deletion, modification, and operation permissions of other modules removed, and assign the custom role to the data operations engineer. This method meets service requirements while avoiding the risk of excessive permissions.

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. Click **Create**. In the displayed dialog box, set the following parameters:

   -  **Role Name**: Enter **Developer_DataService** (unique ID of the custom role).
   -  **Role Description**: Enter **This role is based on the developer role, and only the DataArts DataService permissions are retained.**
   -  **Role Type**: Select **DEV&PROD_CUSTOM** as this role is only used in workspaces in simple mode.
   -  **Reuse**: Select **developer**, deselect the **CREATE**, **DELETE**, **OPERATE**, and **EDIT** permissions of other modules, and retain all permissions of DataArts DataService and view permissions of other modules.


   .. figure:: /_static/images/en-us_image_0000002234080392.png
      :alt: **Figure 2** Creating custom role Developer_DataService

      **Figure 2** Creating custom role Developer_DataService

#. Click **OK**.

#. Assign the created **Developer_DataService** role to the data operations engineer by following the instructions in :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.

Example 2
---------

A data development engineer who wants to use DataArts Studio is assigned the preset developer role by the project administrator. However, the data development engineer also needs to modify the DDL template in the configuration center of DataArts Architecture for data development, but the preset developer role does not have this permission. If the administrator assigns the preset admin role to the data operations engineer, the engineer will have more permissions than needed, which may pose risks.

To address this issue, the administrator can create a custom role **Developer_DDL** based on the preset developer role with the permission to edit the configuration center of DataArts Architecture, and assign the custom role to the data development engineer. This method meets service requirements while avoiding the risk of excessive permissions.

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. Go to the **Roles** page and click **Create**. In the displayed dialog box, set the following parameters:

   -  **Role Name**: Enter **Developer_DDL** (unique ID of the custom role).
   -  **Role Description**: Enter **This role is based on the developer role, with the permission to edit the configuration center of DataArts Architecture added**
   -  **Role Type**: Select **DEV&PROD_CUSTOM** as this role is only used in workspaces in simple mode.
   -  **Reuse**: Select **developer** and select **EDIT** in **DataArts Architecture** > **configuration**.


   .. figure:: /_static/images/en-us_image_0000002269199661.png
      :alt: **Figure 3** Creating custom role Developer_DDL

      **Figure 3** Creating custom role Developer_DDL

#. Click **OK**.

#. Assign the created **Developer_DDL** role to the data development engineer by following the instructions in :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.
