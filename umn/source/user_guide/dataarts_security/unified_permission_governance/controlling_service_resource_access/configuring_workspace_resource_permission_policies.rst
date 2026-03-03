:original_name: dataartsstudio_01_1161.html

.. _dataartsstudio_01_1161:

Configuring Workspace Resource Permission Policies
==================================================

This section describes how to use workspace resource permission policies to implement refined permission control on all the data connections and IAM agencies (only those whose agency object is DGC) in the Management Center based on users, user groups, or roles.

-  If no workspace resource permission policy is configured for a resource, all users can view and use the resource by default.
-  If the permissions of a resource (such as a connection or an agency) are granted to any user, user group, or role, other common users cannot view and use the resource, except the DARTS Administrator, Tenant Administrator, data security administrator, and preset workspace administrator.

Prerequisites
-------------

Only the DARTS Administrator, Tenant Administrator, data security administrator, and preset workspace administrator have the permission to create, edit, or delete workspace resource permission policies.

Constraints
-----------

-  Resources of workspaces in simple mode can be managed, but those of workspaces in enterprise mode cannot.
-  If no permission is assigned to a resource, permission control is disabled for the resource.
-  Currently, only the DataArts Factory component supports workspace resource permission policies. Other components are not restricted by workspace resource permission policies. In the following scenarios of DataArts Factory, authentication is performed based on workspace resource permission policies:

   -  Selecting a connection, job agency, or public agency during script or job development
   -  Submitting a script or job

-  Resource permission management is not supported for the data connections created in DataArts Factory in earlier versions.
-  When a workspace resource is deleted, the corresponding workspace resource permission policy will not be automatically deleted.

Creating a Workspace Resource Permission Policy
-----------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Workspace Resource Permissions**.


   .. figure:: /_static/images/en-us_image_0000002234084516.png
      :alt: **Figure 1** Workspace Resource Permissions

      **Figure 1** Workspace Resource Permissions

#. On the **Workspace Resource Permissions** page, click **Create**. In the slide-out panel, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1161__en-us_topic_0000001678432349_table177118297118>` and click **Save**.

   .. _dataartsstudio_01_1161__en-us_topic_0000001678432349_table177118297118:

   .. table:: **Table 1** Parameters for creating a workspace resource permission policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================================+
      | \*Policy Name                     | Enter the name of the workspace resource permission policy. To facilitate policy management, you are advised to include the resource object and authorization object in the name.                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Resource Object**               |                                                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection                   | Select the data connections in the Management Center to be authorized. For details about how to create a data connection, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                        |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                        |
      |                                   |    -  Permission control is disabled for the data connections that are not selected.                                                                                                                                                                                                                                   |
      |                                   |    -  Unauthorized common users (except the DARTS Administrator, Tenant Administrator, data security administrator, and preset workspace administrator) cannot view or use the selected connections. When you view or modify a job that uses the connection, the data connection and its configurations are invisible. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                            | Select the IAM agencies to be authorized. Only cloud service agencies whose agency object is DGC are supported. For details about how to create an agency, see :ref:`Reference: Creating an Agency <dataartsstudio_01_0555__section17505112912402>`.                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                        |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                        |
      |                                   |    -  Permission control is disabled for the agencies that are not selected.                                                                                                                                                                                                                                           |
      |                                   |    -  Unauthorized common users (except the DARTS Administrator, Tenant Administrator, data security administrator, and preset workspace administrator) cannot view or use the selected agencies.                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Authorization Object**          |                                                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | user                              | Select the users to be authorized. The workspace users are available for selection.                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | user group                        | Select the user groups to be authorized. The workspace user groups are available for selection.                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | role                              | Select the roles to be authorized. The preset and custom roles are available for selection.                                                                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002234084520.png
      :alt: **Figure 2** Creating a workspace resource permission policy

      **Figure 2** Creating a workspace resource permission policy

Related Operations
------------------

-  Editing policies: On the **Workspace Resource Permissions** page, locate a policy and click **Edit** in the **Operation** column to edit the policy.
-  Deleting policies: On the **Workspace Resource Permissions** page, locate a policy and click **Delete** in the **Operation** column to delete the policy. To delete multiple policies at a time, select the policies and click **Delete** above the policy list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.
