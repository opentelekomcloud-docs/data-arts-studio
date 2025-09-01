:original_name: dataartsstudio_01_0116.html

.. _dataartsstudio_01_0116:

Creating a Workspace in Simple Mode
===================================

The system creates a default workspace named **default** for the DataArts Studio instance you create and assigns administrator permissions to you. You can use the default workspace or create another workspace.

A workspace in a DataArts Studio instance is the basic unit for member management and role and permission allocation. It provides all DataArts Studio functions. Workspaces are allocated by branch or subsidiary (such as the group, subsidiary, and department), business domain (such as the procurement, production, and sales), or implementation environment (such as the development, test, and production environment). There are no fixed rules.

As an admin, you can manage user (member) permissions, resources, and compute engines for a workspace. To enable users to work together, admins can add users to a workspace and assign the preset roles of DataArts Studio (admin, developer, operator, and visitor) to the users. Users other than admins can access Management Center, DataArts Migration, and DataArts Factory only after they are added to a workspace and assigned relevant roles.

Notes and Constraints
---------------------

-  There is no limit on the number of workspaces that can be created for a DataArts Studio instance.
-  The storage of job logs and dirty data depends on the OBS service.

Prerequisites
-------------

You have obtained a DataArts Studio instance. For details, see :ref:`Creating a DataArts Studio Instance <dataartsstudio_01_0115>`.

Context
-------

-  The system creates a default workspace named **default** for the DataArts Studio instance you create and assigns admin role to you.
-  In a DataArts Studio instance created by an account, if an IAM user of the account needs to create a workspace, the IAM user must be assigned the **DARTS** **Administrator** or **Tenant Administrator** permissions. By default, the account has all the permissions for a DataArts Studio instance created by a user of the account.
-  Users with the DARTS User permissions can access a workspace only after they are added as members of the workspace.

Creating a Workspace
--------------------

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, click **Create Workspace**. In the displayed dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103>`.


   .. figure:: /_static/images/en-us_image_0000002269119389.png
      :alt: **Figure 1** Creating a workspace

      **Figure 1** Creating a workspace

   .. _dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103:

   .. table:: **Table 1** Parameters for creating a workspace

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Workspace name. It can contain a maximum of 32 characters, including only letters, digits, underscores (_), and hyphens (-). The workspace name must be unique in the current DataArts Studio instance.                                                                                                                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Workspace description                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mode                              | Select the workspace mode.                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Simple**: This mode is easy to use, but does not allow you to strictly control data development processes and table permissions.                                                                                                                                                                                                                                                      |
      |                                   | -  **Enterprise**: In this mode, you can isolate the development environment from the production environment in the DataArts Factory and Management Center modules of DataArts Studio. This prevents developers' operations from affecting services in the production environment. For details about the enterprise mode, see :ref:`Enterprise Mode Overview <dataartsstudio_01_5099>`.    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project associated with the default workspace of the DataArts Studio instance.                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | This parameter is available only when an enterprise project has been created. If you want to connect the DataArts Studio instance to an instance of another cloud service, such as GaussDB(DWS), MRS, and RDS, ensure that the enterprise project of the DataArts Studio instance's workspace is the same as that of the target cloud service instance.                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  You can create only one DataArts Studio instance for an enterprise project.                                                                                                                                                                                                                                                                                                             |
      |                                   | -  If you want to enable communication between DataArts Studio and another cloud service, ensure that the enterprise project of DataArts Studio is the same as that of the target cloud service.                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    If the enterprise project function is not enabled, only one DataArts Studio instance can be created for each IAM project.                                                                                                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Log Path                      | OBS bucket for storing the job logs of DataArts Factory of DataArts Studio. To use the DataArts Factory module of DataArts Studio, workspace members must have the read and write permissions on the OBS bucket for storing job logs. Otherwise, the system cannot read or write job logs of DataArts Factory.                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  Click **Select**. You can select an existing OBS bucket. The selected OBS bucket is globally configured in the current workspace.                                                                                                                                                                                                                                                       |
      |                                   | -  If this parameter is not set, job logs generated during data development are stored in the OBS bucket named **dlf-log-{projectId}** by default. **{projectId}** indicates the project ID, which can be obtained in the following way:                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    a. Register with and log in to the management console.                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    b. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.                                                                                                                                                                                                                                                                    |
      |                                   |    c. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    The execution logs of data development jobs are stored in *xxxxx*.log format in an OBS bucket. *xxxxx* indicates the job ID. Deleting the historical records of SQL statements that have been executed does not affect services.                                                                                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dirty Data Path                   | OBS bucket for storing dirty data generated during DLI SQL execution in DataArts Factory of DataArts Studio. To use DataArts Factory to develop and execute DLI SQL statements, workspace members must have the read and write permissions on the OBS bucket where DLI dirty data is stored. Otherwise, the system cannot read or write the dirty data generated during DLI SQL execution. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  Click **Select**. You can select a created OBS bucket. The selected OBS bucket is globally configured in the current workspace.                                                                                                                                                                                                                                                         |
      |                                   | -  If you do not set this parameter, dirty data generated during DLI SQL execution is stored in the OBS bucket named **dlf-log-{projectId}** by default.                                                                                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Related Operations
------------------

-  Disabling a workspace: After a workspace is created, it is enabled by default. If you do not need a workspace, you can disable it. If you want to use it in the future, you can enable it again.

   On the **Workspaces** page, locate the target workspace, click **More** in the **Operation** column, and select **Disable Workspace**. In the **Disable Workspace** dialog box displayed, read the impact of disabling a workspace. If you want to continue, click **Yes**.

   .. note::

      If you disable a workspace, you cannot access the workspace, edit the workspace, or view the quota of the workspace. In addition, jobs being scheduled in the workspace will stop.

-  Enabling a workspace: On the **Workspaces** page, locate the workspace you want to enable, click **More** in the **Status** column, and select **Enable Workspace**. In the **Enable Workspace** dialog box displayed, read the impact of enabling a workspace. If you want to continue, click **Yes**.

-  Editing a workspace: On the **Workspaces** page, locate the workspace you want to edit and click **Edit** in the **Operation** column. In the displayed **Workspace Information** dialog box, modify workspace parameters by referring to :ref:`Table 1 <dataartsstudio_01_0116__en-us_topic_0196417517_table1413713319103>` and click **OK**.

   When editing a workspace, you can add workspace members (see :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`).

-  Viewing the quota usage: On the **Workspaces** page, locate a workspace and click **Quota Usage** in the **Operation** column. In the displayed **Quota Usage** dialog box, you can view the quota usage of each module.

-  Pinning a workspace to top: On the **Workspaces** page, locate a workspace, click **More** in the **Operation** column, and select **Pin to Top**.

-  Deleting a workspace: On the **Workspaces** page, locate a workspace, click **More** in the **Operation** column, and select **Delete**. In the **Delete Workspace** dialog box, click **OK**.

   .. note::

      Mis-deletion may result in service loss. To delete a workspace, you must use the **DARTS** **Administrator** or **Tenant Administrator** account and ensure that the workspace does not contain any of the following resources:

      -  Management Center: data connections
      -  DataArts Migration: CDM clusters
      -  DataArts Factory: jobs, job directories, scripts, script directories, and resources

      If any module has resources, a message is displayed, indicating that the workspace cannot be deleted.

   If any module has resources, delete the resources as prompted and try again.


   .. figure:: /_static/images/en-us_image_0000002234240048.png
      :alt: **Figure 2** Message indicating that the workspace cannot be deleted

      **Figure 2** Message indicating that the workspace cannot be deleted
