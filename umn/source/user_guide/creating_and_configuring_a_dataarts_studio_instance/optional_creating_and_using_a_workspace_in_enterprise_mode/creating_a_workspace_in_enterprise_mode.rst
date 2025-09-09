:original_name: dataartsstudio_01_5135.html

.. _dataartsstudio_01_5135:

Creating a Workspace in Enterprise Mode
=======================================

If you are using a workspace in simple mode and want to isolate the development and production environments, you can upgrade the workspace to one in enterprise mode. If you have not used any workspace in simple mode and do not need to inherit data, you can directly create a workspace in enterprise mode by following the instructions in this section.

Restrictions
------------

You can upgrade your workspace mode or create a workspace in enterprise mode only if you are assigned the DARTS Administrator or Tenant Administrator role.

Prerequisites
-------------

Before creating a workspace, ensure that:

-  You have understood the differences between workspaces in simple mode and those in enterprise mode, such as the differences in the development process. For details, see :ref:`Introduction to the Simple Mode and Enterprise Mode <dataartsstudio_01_5099__section165131840175316>`.
-  You have configured workspace-level scheduling identities, including public agencies and public IAM accounts. For details, see :ref:`Configuring a Public Agency <dataartsstudio_01_0555__section3485198599>` and :ref:`Configuring a Public IAM Account <dataartsstudio_01_0555__section11898926149>`.
-  You have prepared two sets of isolated data lake engines, one for the development environment and the other for the production environment.

   -  Configure two sets of data lake services to isolate the development environment from the production environment.

      For clustered data sources, such as MRS, GaussDB(DWS), RDS, MySQL, Oracle, and ECS, you can create data connections in Management Center to distinguish data lake services in the development environment from those in the production environment. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of data lake services that have the same version, specifications, components, region, VPC, subnet, and other related configurations. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.

      When creating a data connection, you can select different clusters for the development environment and production environment to isolate them.


      .. figure:: /_static/images/en-us_image_0000002234077360.png
         :alt: **Figure 1** Selecting different clusters during data connection creation

         **Figure 1** Selecting different clusters during data connection creation

   -  Configure environment isolation for DLI.

      Configure environment isolation in enterprise mode, including DLI queue configuration and DB configuration.

      For serverless services (such as DLI), you can configure the mapping between data lake services in the production environment and those in the development environment through environment isolation in Management Center. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of queues and database resources in the serverless data lake service and distinguish them by name suffix. For details, see :ref:`Configuring Environment Isolation for a DataArts Studio Workspace in Enterprise Mode <dataartsstudio_01_5105>`.

   -  Configure two databases in the same data lake service to isolate the development environment from the production environment.

      For GaussDB(DWS), MRS Hive, and MRS Spark, if you select the same cluster when creating a data connection (as shown in :ref:`Figure 2 <dataartsstudio_01_5135__en-us_topic_0000001555291685_fig6703125117183>`), you must configure database mapping on the **Configure Data Source Resource Mapping** page shown in :ref:`Figure 3 <dataartsstudio_01_5135__en-us_topic_0000001555291685_fig17291130105915>` to isolate the development and production environments. For details, see :ref:`DB configuration <dataartsstudio_01_5105__section20609134272018>`.

      .. _dataartsstudio_01_5135__en-us_topic_0000001555291685_fig6703125117183:

      .. figure:: /_static/images/en-us_image_0000002269196641.png
         :alt: **Figure 2** Selecting the same cluster during data connection creation

         **Figure 2** Selecting the same cluster during data connection creation

      .. _dataartsstudio_01_5135__en-us_topic_0000001555291685_fig17291130105915:

      .. figure:: /_static/images/en-us_image_0000002424511029.png
         :alt: **Figure 3** DB Configuration

         **Figure 3** DB Configuration

-  Prepare and synchronize data.

   -  After creating data lake services, you must create databases, database schemas (required only for DWS), and data tables in the data lake services of the development and production environments based on the project plan (for example, the databases and tables required for data development).

      -  For clustered data sources (such as MRS, DWS, RDS, MySQL, Oracle, and ECS), use two clusters, one for the development environment and the other for the production environment. The names of the databases, database schemas (required only for DWS), and data tables in the two environments must be the same.
      -  For serverless services (such as DLI), you are advised to associate and distinguish the two queues and databases by name suffix (add suffix **\_dev** to the names of the queues and databases in the development environment and add no suffix to those in the production environment). The names of data tables in the development environment must be the same as those in the production environment.
      -  For DWS, MRS Hive, and MRS Spark data sources, if the same cluster is used for the development and production environments, use two databases to isolate the development and production environments (add suffix **\_dev** to the database for the development environment and add no suffix to the database for the production environment). The names of database schemas (required only for DWS) and data tables in the development environment must be the same as those in the production environment.

   -  After creating databases, database schemas (required only for DWS), and data tables, you must synchronize data of existing tables (if any) between the two data lake services.

      -  Existing data in data lakes: Use data migration services such as CDM and DRS to synchronize data in batches between data lakes.
      -  Data to be migrated from the data source: Use peering jobs of data migration services such as CDM and DRS to synchronize data between the data lake service of the production environment and that of the development environment.

Change Description
------------------

After the workspace mode is upgraded, a development environment isolated from the production environment is added.

Upgrading the Simple Mode to Enterprise Mode
--------------------------------------------

With the DARTS Administrator or Tenant Administrator role, you can upgrade a workspace in simple mode to one in enterprise mode.

-  Pre-upgrade operations

   Configure a workspace-level public agency or public IAM account in DataArts Factory to avoid an upgrade failure.

   For details about how to configure an agency, see :ref:`Configuring a Scheduling Identity <dataartsstudio_01_0555>`.


   .. figure:: /_static/images/en-us_image_0000002269203809.png
      :alt: **Figure 4** Configuring a workspace-level agency

      **Figure 4** Configuring a workspace-level agency

-  Upgrade operations

   #. Log in to the DataArts Studio console.

   #. Locate a DataArts Studio instance and click **Access**. Then, click the **Workspaces** tab.

   #. Locate the workspace you want to upgrade and click **Edit** in **Operation** column.

   #. In the displayed **Workspace Information** dialog box, click **Upgrade** next to the **Mode** text box. In the displayed dialog box, click **Upgrade**.


      .. figure:: /_static/images/en-us_image_0000002234244332.png
         :alt: **Figure 5** Upgrading to the enterprise mode

         **Figure 5** Upgrading to the enterprise mode

-  Post-upgrade operations

   After the upgrade is complete, you (as the admin) need to modify data connections, configure environment isolation, and define roles such as the admin, developer, deployer, and operator in the workspace.

   #. Modify data connections. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.
   #. Configure environment isolation. For details, see :ref:`Configuring Environment Isolation for a DataArts Studio Workspace in Enterprise Mode <dataartsstudio_01_5105>`.
   #. Define workspace roles for other users. For details, see :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.


Creating a Workspace in Enterprise Mode
---------------------------------------

If you have not used the simple mode before and do not need to inherit business data, you can directly create a workspace in enterprise mode.

-  Create a workspace.

   #. Log in to the DataArts Studio console using an account with the DARTS Administrator or Tenant Administrator permission.

   #. Locate an instance and click **Access**. Then click the **Workspaces** tab.

   #. Click **Create**. In the displayed **Create** dialog box, set parameters based on :ref:`Table 1 <dataartsstudio_01_5135__en-us_topic_0196417517_table1413713319103>` and click **OK**.

      .. _dataartsstudio_01_5135__en-us_topic_0196417517_table1413713319103:

      .. table:: **Table 1** Parameters for creating a workspace

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                |
         +===================================+============================================================================================================================================================================================================================================================================================================================================================================================+
         | Name                              | Workspace name. It can contain a maximum of 32 characters, including only letters, digits, underscores (_), and hyphens (-). The workspace name must be unique in the current DataArts Studio instance.                                                                                                                                                                                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Workspace description                                                                                                                                                                                                                                                                                                                                                                      |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Mode                              | Mode of the workspace. Available options include **Simple** and **Enterprise**. Select **Enterprise**.                                                                                                                                                                                                                                                                                     |
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
         |                                   | -  If you do not set this parameter, job logs of DataArts Factory are stored in the OBS bucket named **dlf-log-{projectId}** by default.                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
         |                                   |    .. note::                                                                                                                                                                                                                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
         |                                   |       The execution logs of data development jobs are stored in *xxxxx*.log format in an OBS bucket. *xxxxx* indicates the job ID. Deleting the historical records of SQL statements that have been executed does not affect services.                                                                                                                                                     |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Dirty Data Path                   | OBS bucket for storing dirty data generated during DLI SQL execution in DataArts Factory of DataArts Studio. To use DataArts Factory to develop and execute DLI SQL statements, workspace members must have the read and write permissions on the OBS bucket where DLI dirty data is stored. Otherwise, the system cannot read or write the dirty data generated during DLI SQL execution. |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                            |
         |                                   | -  Click **Select**. You can select a created OBS bucket. The selected OBS bucket is globally configured in the current workspace.                                                                                                                                                                                                                                                         |
         |                                   | -  If you do not set this parameter, dirty data generated during DLI SQL execution is stored in the OBS bucket named **dlf-log-{projectId}** by default.                                                                                                                                                                                                                                   |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Perform follow-up operations.

   After creating the workspace, you (as the admin) need to create data connections, configure environment isolation, and define roles such as the admin, developer, deployer, and operator in the workspace.

   #. Create data connections. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.

   #. Configure environment isolation. For details, see :ref:`Configuring Environment Isolation for a DataArts Studio Workspace in Enterprise Mode <dataartsstudio_01_5105>`.

   #. Define workspace roles for other users. For details, see :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.

   #. Configure a workspace-level public agency or public IAM account in DataArts Factory. For details about how to configure an agency, see :ref:`Configuring a Scheduling Identity <dataartsstudio_01_0555>`.


      .. figure:: /_static/images/en-us_image_0000002269123729.png
         :alt: **Figure 6** Configuring a workspace-level agency

         **Figure 6** Configuring a workspace-level agency
