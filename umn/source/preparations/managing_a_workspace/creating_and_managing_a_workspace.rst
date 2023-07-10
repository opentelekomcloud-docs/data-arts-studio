:original_name: dataartsstudio_01_0116_0.html

.. _dataartsstudio_01_0116_0:

Creating and Managing a Workspace
=================================

By default, a workspace will be automatically created after you create a DataArts Studio instance. You will be automatically assigned the admin role and can use the default workspace or create a new workspace.

A workspace in a DataArts Studio instance is the basic unit for member management and role and permission allocation. It provides all DataArts Studio functions. Workspaces are allocated by branch or subsidiary (such as the group, subsidiary, and department), business domain (such as the procurement, production, and sales), or implementation environment (such as the development, test, and production environment). There are no fixed rules.

Admins can manage user (member) permissions, resources, and compute engines in a workspace. To enable users to work together, admins can add users to a workspace and assign the preset roles of DataArts Studio (admin, developer, operator, and visitor) to the users. Users other than admins can access Management Center, DataArts Migration, DataArts Factory, only after they are added to a workspace and assigned relevant roles.

Constraints
-----------

The storage of job logs and dirty data depends on the OBS service. If the OBS service is unavailable, job logs and dirty data cannot be stored.

Prerequisites
-------------

A DataArts Studio instance has been create. For details, see :ref:`Creating a DataArts Studio Basic Package <dataartsstudio_01_0115_0>`.

Background
----------

-  After you a DataArts Studio instance, you have the permission to create workspaces. DataArts Studio creates a default workspace for you and assign the admin role to you.
-  In a DataArts Studio instance created by a master account, if an IAM user of the account needs to create a workspace, the IAM user must be assigned the **DAYU Administrator** or **Tenant Administrator** policy. By default, the master account has all the permissions for a DataArts Studio instance created by a sub-user.
-  After workspaces are created, they cannot be deleted. You can disable workspaces when they are no longer needed. You can enable them again when you need these workspaces.
-  Users assigned the **DAYU User** policy can access a workspace only after you add them as members of the workspace.

Creating a Workspace
--------------------

#. Log in to the DataArts Studio console using the **DAYU** **Administrator** account.

#. Click the **Workspaces** tab.

#. Click **Create**. On the **Workspace Information** page, set the parameters based on :ref:`Table 1 <dataartsstudio_01_0116_0__en-us_topic_0196417517_table1413713319103>`. After the configuration is complete, click **OK**.

   .. _dataartsstudio_01_0116_0__en-us_topic_0196417517_table1413713319103:

   .. table:: **Table 1** Parameters for creating a workspace

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Workspace names can contain only letters, numbers, underscores (_), and hyphens (-). They cannot exceed 32 characters. In a DataArts Studio instance, workspace names must be unique.                                                                                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the workspace.                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | The enterprise project associated with your DataArts Studio instance.                                                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | This parameter is available only when an enterprise project has been created. If you want to connect the DataArts Studio instance to a cloud service (such as DWS, MRS, and RDS), ensure that the enterprise project of the DataArts Studio instance is the same as that of the cloud service instance.                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | -  You can create only one DataArts Studio instance for an enterprise project.                                                                                                                                                                                                                                                                                                                              |
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

Editing a Workspace
-------------------

#. Log in to the DataArts Studio console.
#. Select a DataArts Studio instance and click **Access**. Then, click the **Workspaces** tab.
#. On the **Workspaces** tab page, locate the target workspace and click **Edit** in the row that contains the workspace.
#. Click **Edit** at the top of the **Workspace Information** page to edit the workspace information and manage workspace members.
#. After the configuration is complete, click **Save** at the top of the **Workspace Information** page to save the settings.

Disabling a Workspace
---------------------

After a workspace is created, it is enabled by default. You can disable or enable it as required.

.. note::

   If you disable a workspace, you cannot access the workspace, edit the workspace content, or schedule jobs in the workspace.

#. Log in to the DataArts Studio console.
#. Select a DataArts Studio instance and click **Access**. Then, click the **Workspaces** tab.
#. On the **Workspaces** tab page, locate the target workspace, and turn off |image1| in the **Status** column.
#. In the **Disable Workspace** dialog box displayed, read the impact of disabling a workspace. Click **Yes** to disable the workspace.

Enabling a Workspace
--------------------

#. Log in to the DataArts Studio console.
#. Select a DataArts Studio instance and click **Access**. Then, click the **Workspaces** tab.
#. On the **Workspaces** tab page, locate the target workspace, and turn on |image2| in the **Status** column.
#. In the **Enable Workspace** dialog box displayed, read the impact of enabling a workspace. If you want to continue, click **Yes** to enable the workspace.

.. |image1| image:: /_static/images/en-us_image_0000001322088552.png
.. |image2| image:: /_static/images/en-us_image_0000001321928856.png
