:original_name: dataartsstudio_01_0116.html

.. _dataartsstudio_01_0116:

Creating and Managing a Workspace
=================================

The system will create a default workspace and assign the admin role to you after you create a DataArts Studio instance. can use the default workspace or create a new workspace.

A workspace in a DataArts Studio instance is the basic unit for member management and role and permission allocation. It provides all DataArts Studio functions. Workspaces are allocated by branch or subsidiary (such as the group, subsidiary, and department), business domain (such as the procurement, production, and sales), or implementation environment (such as the development, test, and production environment). There are no fixed rules.

Admins can manage user (member) permissions, resources, and compute engines in a workspace. To enable users to work together, admins can add users to a workspace and assign the preset roles of DataArts Studio (admin, developer, operator, and visitor) to the users. Users other than admins can access Management Center, DataArts Migration, and DataArts Factory only after they are added to a workspace and assigned relevant roles.

Constraints
-----------

-  There is no limit on the number of workspaces that can be created for a DataArts Studio instance. You can plan the quota as needed.
-  The storage of job logs and dirty data depends on the OBS service.

Prerequisites
-------------

You have created a DataArts Studio instance by referring to :ref:`Creating a DataArts Studio Basic Package <dataartsstudio_01_0115>`.

Background
----------

-  The system will create a default workspace and assign the admin role to you after you create a DataArts Studio instance.
-  In a DataArts Studio instance created by a master account, if an IAM user of the account needs to create a workspace, the IAM user must be assigned the **DARTS Administrator** or **Tenant Administrator** policy. By default, the master account has all the permissions for a DataArts Studio instance created by a sub-user.
-  Users assigned the permissions of **DARTS User** can access a workspace only after they are added as members of the workspace.

Creating a Workspace
--------------------

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, click **Create**. In the displayed dialog box, set parameters based on :ref:`Table 1 <dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103>`.


   .. figure:: /_static/images/en-us_image_0000002270788384.png
      :alt: **Figure 1** Creating a workspace

      **Figure 1** Creating a workspace

   .. _dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103:

   .. table:: **Table 1** Parameters for creating a workspace

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Workspace names can contain only letters, numbers, underscores (_), and hyphens (-). They cannot exceed 32 characters. In a DataArts Studio instance, workspace names must be unique.                                                                                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the workspace.                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mode                              | Workspace mode                                                                                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | -  **Simple**: This traditional mode is easy to use but does not allow you to strictly control the data development process and table permissions.                                                                                                                                                                                                                                                          |
      |                                   | -  **Enterprise**: You can isolate the development environment from the production environment in the DataArts Factory and Management Center modules of DataArts Studio. This prevents developers' operations from affecting services in the production environment. For details about the enterprise mode, see :ref:`DataArts Studio Enterprise Mode Overview <dataartsstudio_01_5099>`.                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project associated with the default workspace of the DataArts Studio instance.                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | This parameter is available only when an enterprise project has been created. If you want to connect the DataArts Studio instance to a cloud service (such as DWS, MRS, and RDS), ensure that the enterprise project of the DataArts Studio workspace is the same as that of the cloud service instance.                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | -  You can only create one DataArts Studio instance in an enterprise project.                                                                                                                                                                                                                                                                                                                               |
      |                                   | -  If you want to enable communication between DataArts Studio and another cloud service, ensure that the enterprise project of DataArts Studio is the same as that of the cloud service.                                                                                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OBS Bucket for Job Logs           | The OBS bucket for storing logs of DataArts Studio data development jobs. To use the DataArts Factory module of DataArts Studio, workspace members must have the read and write permissions on the OBS bucket for storing job logs. Otherwise, the system cannot read or write job logs generated during data development.                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | -  Click **Select**. You can select a created OBS bucket. The selected OBS bucket is globally configured in the current workspace.                                                                                                                                                                                                                                                                          |
      |                                   | -  If this parameter is not set, job logs generated during data development are stored in the OBS bucket named **dlf-log-{projectId}** by default. **{projectId}** indicates the project ID, which can be obtained by referring to :ref:`Obtaining a Project ID and Account ID <dataartsstudio_01_0006__section134096463399>`.                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OBS Bucket for DLI Dirty Data     | The OBS bucket for storing dirty data generated during DLI SQL execution in DataArts Studio Data Development. To use DataArts Studio DataArts Factory to develop and execute DLI SQL statements, workspace members must have the read and write permissions on the OBS bucket where DLI dirty data is stored. Otherwise, the system cannot read or write the dirty data generated during DLI SQL execution. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | -  Click **Select**. You can select a created OBS bucket. The selected OBS bucket is globally configured in the current workspace.                                                                                                                                                                                                                                                                          |
      |                                   | -  If this parameter is not set, dirty data generated during DLI SQL execution is stored in the OBS bucket named **dlf-log-{projectId}** by default.                                                                                                                                                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Related Operations
------------------

-  Disable a workspace: After a workspace is created, it is enabled by default. You can disable or enable it as needed.

   On the **Workspaces** page, locate the target workspace, and click |image1| in the **Status** column to disable the workspace. In the displayed **Disable Workspace** dialog box, learn about the impact of disabling the workspace and click **Yes** to disable the workspace.

   .. note::

      If you disable a workspace, you cannot access the workspace, edit the workspace, view quotas of the workspace, or schedule jobs in the workspace.

-  Enable a workspace: On the **Workspaces** page, locate the target workspace, and click |image2| in the **Status** column to enable the workspace. In the displayed **Enable Workspace** dialog box, click **Yes**.

-  Edit a workspace: On the **Workspaces** page, locate the target workspace, and click **Edit** in the **Operation** column. In the displayed **Workspace Information** dialog box, modify the workspace parameters listed in :ref:`Table 1 <dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103>` and click **OK**.

-  Add/Edit a tag: On the **Workspaces** page, locate a workspace, click **More** in the **Operation** column, and select **tags**. In the displayed **tags** dialog box, click **Add/Edit Tag** to associate tags with the workspace.

-  View quota usage: On the **Workspaces** page, locate a workspace and click **Quota Usage** in the **Operation** column. In the displayed **Quota Usage** dialog box, you can view the quota usage of each service in the workspace.

-  Pin a workspace to top: On the **Workspaces** tab page, locate the target workspace, click **More** in the **Operation** column, and select **Pin to Top**.

-  Delete a workspace: On the **Workspaces** page, locate the target workspace, click **More** in the **Operation** column, and select **Delete**. In the displayed **Delete Workspace** dialog box, click **OK**.

   .. note::

      To prevent service loss caused by mis-deletion, the system allows only the **DARTS** **Administrator** or **Tenant Administrator** to delete workspaces. Before deleting a workspace, ensure that no resource is available in any of the following modules:

      -  Management Center: data connections
      -  DataArts Migration: CDM clusters
      -  DataArts Factory: jobs, job directories, scripts, script directories, and resources

      If any component of a workspace has any service resource, deleting the workspace will fail.

   If any module has resources, delete the resources as prompted and try again.


   .. figure:: /_static/images/en-us_image_0000002270845238.png
      :alt: **Figure 2** Message indicating that the workspace cannot be deleted

      **Figure 2** Message indicating that the workspace cannot be deleted

.. |image1| image:: /_static/images/en-us_image_0000002305438189.png
.. |image2| image:: /_static/images/en-us_image_0000002305405125.png
