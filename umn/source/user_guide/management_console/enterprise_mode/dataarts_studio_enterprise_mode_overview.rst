:original_name: dataartsstudio_01_5099.html

.. _dataartsstudio_01_5099:

DataArts Studio Enterprise Mode Overview
========================================

DataArts Studio provides two workspace modes, the simplified mode and enterprise mode, to help you manage your production data with varied security control requirements. This section describes the differences between the two modes from multiple dimensions, such as the physical form and impact on development.

.. important::

   Currently, only Management Center and DataArts Factory support the enterprise mode.

In simple mode, you need to create two workspaces, one for the development environment and the other for the production environment. In this way, you can isolate the development and production environment. You can export scripts or jobs from the development workspace and import them to the production workspace. In this mode, you cannot synchronize the production and development environment easily as there is no approval for the synchronization. To address these issues, you can use a workspace in enterprise mode to isolate the development and production environment. The one-click release and approval process improves your efficiency in task release.

You are advised to upgrade to the enterprise mode for your workspace to better manage the development process. For details, see :ref:`Creating a Workspace in Enterprise Mode <dataartsstudio_01_5135>`.

Background
----------

This section contains the following parts which resolve the problems you may encounter when using the enterprise mode.

.. table:: **Table 1** Basics about the enterprise mode

   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Category                                                                                                                                    | Description                                                                                                                                                                                                                                       |
   +=============================================================================================================================================+===================================================================================================================================================================================================================================================+
   | :ref:`Introduction to the Simple Mode and Enterprise Mode <dataartsstudio_01_5099__section165131840175316>`                                 | Introduction to the two workspace modes                                                                                                                                                                                                           |
   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Comparison of Workspaces Using Different Modes in Production Task Development and O&M <dataartsstudio_01_5099__section4664142816018>` | Introduction to the task development and O&M mechanisms built based on the physical attributes of DataArts Studio workspaces                                                                                                                      |
   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Advantages and Disadvantages of Workspace Modes <dataartsstudio_01_5099__section615719325918>`                                        | Comparison of the advantages and disadvantages of the workspace modes                                                                                                                                                                             |
   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Process of Using DataArts Studio in Different Workspace Modes <dataartsstudio_01_5099__section1967911532139>`                         | Process control of the workspace in enterprise mode                                                                                                                                                                                               |
   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Operations Allowed by DataArts Studio Modules in Different Workspace Modes <dataartsstudio_01_5099__section870765071512>`             | In the simple mode, only the production environment is available. In the enterprise mode, the development environment and production environment are available. This part describes the mapping between environments and DataArts Studio modules. |
   +---------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Important Notes
---------------

-  Different workspace modes have certain requirements on the data lake engine. To isolate the development environment from the production environment of a workspace that uses the enterprise mode, you must configure a data lake engine for both environments. You can configure isolation between the development and production environments using any of the methods shown in the following figure.


   .. figure:: /_static/images/en-us_image_0000002270791220.png
      :alt: **Figure 1** Configuring isolation between the development and production environments

      **Figure 1** Configuring isolation between the development and production environments

   -  Configure two sets of data lake services to isolate the development environment from the production environment.

      For clustered data sources, such as MRS, GaussDB(DWS), RDS, MySQL, Oracle, DIS, and ECS, you can create data connections in Management Center to distinguish data lake services in the development environment from those in the production environment. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of data lake services that have the same version, specifications, components, region, VPC, subnet, and other related configurations. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_1299>`.

      When creating a data connection, you can select different clusters for the development environment and production environment to isolate them.


      .. figure:: /_static/images/en-us_image_0000002270791224.png
         :alt: **Figure 2** Selecting different clusters during data connection creation

         **Figure 2** Selecting different clusters during data connection creation

   -  Configure environment isolation for DLI.

      Configure environment isolation in enterprise mode, including DLI queue configuration and DB configuration.

      For serverless services (such as DLI), you can configure the mapping between data lake services in the production environment and those in the development environment through environment isolation in Management Center. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of queues and database resources in the serverless data lake service and distinguish them by name suffix. For details, see :ref:`Configuring Environment Isolation for a Workspace in Enterprise Mode <dataartsstudio_01_5105>`.

   -  Configure two databases in the same data lake service to isolate the development environment from the production environment.

      For GaussDB(DWS), MRS Hive, and MRS Spark, if you select the same cluster when creating a data connection (as shown in :ref:`Figure 3 <dataartsstudio_01_5099__fig6703125117183>`), you must configure database mapping on the **Configure Data Source Resource Mapping** page shown in :ref:`Figure 4 <dataartsstudio_01_5099__fig17291130105915>` to isolate the development and production environments. For details, see :ref:`DB configuration <dataartsstudio_01_5105__section20609134272018>`.

      .. _dataartsstudio_01_5099__fig6703125117183:

      .. figure:: /_static/images/en-us_image_0000002270791236.png
         :alt: **Figure 3** Selecting the same cluster during data connection creation

         **Figure 3** Selecting the same cluster during data connection creation

      .. _dataartsstudio_01_5099__fig17291130105915:

      .. figure:: /_static/images/en-us_image_0000002305441025.png
         :alt: **Figure 4** DB Configuration

         **Figure 4** DB Configuration

-  Data development jobs in the development environment of a workspace that uses the enterprise mode are not scheduled by default. They can be scheduled only after released to the production environment.

.. _dataartsstudio_01_5099__section165131840175316:

Introduction to the Simple Mode and Enterprise Mode
---------------------------------------------------

Typically, DataArts Studio workspaces use the simple mode. In this mode, you cannot isolate the development and production environment in the DataArts Factory and Management Center modules of DataArts Studio, or control the data development process or table permissions. Instead, you can only perform simple data development operations. A data lake functions as the production environment of DataArts Studio.


.. figure:: /_static/images/en-us_image_0000002270791240.png
   :alt: **Figure 5** A workspace using the simple mode

   **Figure 5** A workspace using the simple mode

The enterprise mode of DataArts Studio workspaces eliminates the risks of the simple mode. In this mode, you can isolate the development environment from the production environment in the DataArts Factory and Management Center modules of DataArts Studio. This prevents developers' operations from affecting services in the production environment. This mode requires two data lakes, one as the development environment and the other as the production environment.

-  The development environment is accessible only to developers for script and job development and release of scripts and jobs to the production environment.
-  The production environment is accessible only to end users and allows no change. Any change that is required must be made in the development environment and released to the production environment again.


.. figure:: /_static/images/en-us_image_0000002270848090.png
   :alt: **Figure 6** A workspace using the enterprise mode

   **Figure 6** A workspace using the enterprise mode

.. note::

   -  You can create a workspace in either mode to experience DataArts Studio. With a workspace in enterprise mode, you can isolate the code, compute resources, and permissions of the development environment from those of the production environment, and manage the task release process.
   -  If you are using a workspace in simple mode and want to experience the enterprise mode while retaining the code of the workspace, you can upgrade the workspace. For details, see :ref:`Creating a Workspace in Enterprise Mode <dataartsstudio_01_5135>`.

.. _dataartsstudio_01_5099__section4664142816018:

Comparison of Workspaces Using Different Modes in Production Task Development and O&M
-------------------------------------------------------------------------------------

.. table:: **Table 2** Comparison of workspaces using different modes in production task development and O&M

   +-------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Comparison Item                                       | Simple Mode                                                                                                   | Enterprise Mode (Recommended)                                                                                                                                                                                                                                                          |
   +=======================================================+===============================================================================================================+========================================================================================================================================================================================================================================================================================+
   | Management of the production task development process | -  After a task is submitted, it can be periodically executed to generate result data without being released. | -  You need to submit a task to the development environment and release the task to the production environment. Then the task can be automatically executed.                                                                                                                           |
   |                                                       |                                                                                                               |                                                                                                                                                                                                                                                                                        |
   |                                                       | The process is submission and then production.                                                                | The process is submission, release, and then production.                                                                                                                                                                                                                               |
   |                                                       |                                                                                                               |                                                                                                                                                                                                                                                                                        |
   |                                                       |                                                                                                               | -  The production environment is accessible only to end users and allows no change. Any change that is required must be made in the development environment and released to the production environment again.                                                                          |
   +-------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Management of the production task O&M permissions     | Developers can directly edit scripts and jobs of production tasks.                                            | Developers can edit and submit code on the DataArts Factory console, but cannot directly release code to the production environment. To release code to the production environment, developers must have the O&M permission. (The deployer, admin, and operator have this permission). |
   |                                                       |                                                                                                               |                                                                                                                                                                                                                                                                                        |
   |                                                       |                                                                                                               | -  All scripts and jobs can be edited only in the development environment. The code in the production environment cannot be modified.                                                                                                                                                  |
   |                                                       |                                                                                                               | -  You can plan and manage task development and O&M processes on DataArts Studio based on the features of workspaces in enterprise mode and the role permission system of DataArts Studio. For details, see :ref:`Service Process in Enterprise Mode <dataartsstudio_01_5100>`.        |
   +-------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Management of production data permissions             | Developers can directly use production data for tests, posing security threats to production data.            | Developers can use test data in the development environment. Data in the production environment is read-only.                                                                                                                                                                          |
   +-------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_5099__section615719325918:

Advantages and Disadvantages of Workspace Modes
-----------------------------------------------

.. table:: **Table 3** Advantages and disadvantages of workspace modes

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Comparison Item       | Simple Mode                                                                                                                                                                              | Enterprise Mode                                                                                                                                                                                                                                                                                         |
   +=======================+==========================================================================================================================================================================================+=========================================================================================================================================================================================================================================================================================================+
   | Advantages            | Simple, convenient, and easy to use                                                                                                                                                      | Secure and normalized                                                                                                                                                                                                                                                                                   |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       | -  You only need to assign the developer role to data developers, and they are able to perform all data development tasks.                                                               | -  A secure and normalized code release and management process (including code review and diff for checking code differences) is available. It ensures the stability of the production environment by avoiding unexpected circumstances such as dirty data spread and task errors caused by code logic. |
   |                       | -  After submitting a script or job, you do not need to release it. The script or job can be periodically executed to generate result data.                                              | -  Data access is effectively controlled to ensure data security.                                                                                                                                                                                                                                       |
   |                       |                                                                                                                                                                                          | -  All scripts and jobs can be edited only in the development environment.                                                                                                                                                                                                                              |
   |                       |                                                                                                                                                                                          | -  Data in the development environment is isolated from that in the production environment. Developers cannot modify data in the production environment.                                                                                                                                                |
   |                       |                                                                                                                                                                                          | -  In the development environment, scripts and jobs are executed by the current developer. In the production environment, scripts and jobs are executed by a workspace-level public IAM account or public agency.                                                                                       |
   |                       |                                                                                                                                                                                          | -  If any change is required for the production environment, the change must be made by a developer in the development environment first and then submitted to the production environment. The change can be successfully released only after being approved by the admin or deployer.                  |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disadvantages         | Unstable and insecure                                                                                                                                                                    | The process is relatively complex. Generally, one person cannot complete all data development and production tasks.                                                                                                                                                                                     |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       | -  The development environment cannot be isolated from the production environment. Only simple data development can be performed.                                                        |                                                                                                                                                                                                                                                                                                         |
   |                       | -  The permissions of production tables cannot be controlled.                                                                                                                            |                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       |    .. note::                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       |       During development and commissioning, developers can directly access data in the production data lake and add, delete, and modify data in tables, posing threats to data security. |                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       | -  The data development process cannot be managed.                                                                                                                                       |                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       |    .. note::                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                         |
   |                       |                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                         |
   |                       |       Developers can add or modify scripts or jobs and submit them to the scheduling system without approval at any time, posing threats to service stability.                           |                                                                                                                                                                                                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_5099__section1967911532139:

Process of Using DataArts Studio in Different Workspace Modes
-------------------------------------------------------------

-  In the simple mode, you cannot isolate the development and production environment in the DataArts Factory and Management Center modules of DataArts Studio, or control the data development process or table permissions. Instead, you can only perform simple data development operations. After submitting a script or job, you do not need to release it. The script or job can be periodically executed to generate result data.


   .. figure:: /_static/images/en-us_image_0000002270848086.png
      :alt: **Figure 7** Process in simple mode

      **Figure 7** Process in simple mode

-  In the enterprise mode, you can isolate the development environment from the production environment in the DataArts Factory and Management Center modules of DataArts Studio. This prevents developers' operations from affecting services in the production environment. The development environment is accessible only to developers for script and job development and release of scripts and jobs to the production environment. The production environment is accessible only to end users and allows no change. Any change that is required must be made in the development environment and released to the production environment again.


   .. figure:: /_static/images/en-us_image_0000002305441041.png
      :alt: **Figure 8** Process in enterprise mode

      **Figure 8** Process in enterprise mode

.. _dataartsstudio_01_5099__section870765071512:

Operations Allowed by DataArts Studio Modules in Different Workspace Modes
--------------------------------------------------------------------------

.. table:: **Table 4** Operations allowed by modules in different workspace modes

   +------------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DataArts Studio Module | Simple Mode                                                                                               | Enterprise Mode                                                                                                                                                        |
   +========================+===========================================================================================================+========================================================================================================================================================================+
   | Management Center      | Perform operations in the production environment (data connection operations and data import and export). | Perform operations in the development and production environments (data source resource mapping configuration, data connection operations, and data import and export) |
   +------------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DataArts Factory       | Perform operations on instances and databases in the production environment.                              | Perform operations on instances and databases in the development and production environments.                                                                          |
   +------------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
