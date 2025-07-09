:original_name: dataartsstudio_01_1299.html

.. _dataartsstudio_01_1299:

Creating a Data Connection
==========================

You can create data connections by configuring data sources. Based on the data connections of the Management Center, DataArts Studio performs data development, governance, services, and operations on the data lake base.

After the data connection between the development environment and production environment is configured, the data connection in the development environment in the script or job during data development is automatically switched to the data connection in the production environment after the process is released.

Constraints
-----------

-  RDS data connections depend on OBS. If OBS is unavailable in the same region as DataArts Studio, RDS data connections are not supported.
-  For host connections, only Linux hosts are supported.
-  If changes occur in the connected data lake (for example, the MRS cluster capacity is expanded), you need to edit and save the connection.
-  If the data lake authentication information in a data connection changes (for example, the password expires), the data connection becomes invalid. Ensure that the data lake authentication information is permanently valid to prevent any loss caused by connection failures.

Prerequisites
-------------

-  You have created a data lake to connect, for example, a database or cloud service supported by DataArts Studio.

   -  Before creating a DWS data connection, ensure that you have created a cluster in DWS and have the permissions required to view Key Management Service (KMS) keys.
   -  Before creating an MRS connection such as an MRS HBase and MRS Hive connection, ensure that you have created an MRS cluster and selected required components.

-  The data lake to connect communicates with the DataArts Studio instance properly.

   -  If the data lake is an on-premises database, a public network or a dedicated connection is required. Ensure that the host where the data source is located can access the public network and the port has been enabled in the firewall rule.
   -  If the data lake is a cloud service (such as DWS and MRS), the following requirements must be met for network interconnection:

      -  If the CDM cluster in the DataArts Studio instance and the cloud service are in different regions, a public network or a dedicated connection is required.
      -  If the CDM cluster in the DataArts Studio instance and the cloud service are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding a Custom Route" in *Virtual Private Cloud (VPC) Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in *Virtual Private Cloud (VPC) Usage Guide*.
      -  The cloud service instance and the DataArts Studio workspace belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

-  If the enterprise mode is used, pay attention to the following points:

   In enterprise mode, the development environment and production environment need to be distinguished. Therefore, you need to prepare two sets of data lake services for the production environment and development environment to isolate the development environment from the production environment.

   -  **If two clusters are used** for clustered data sources, such as MRS, GaussDB(DWS), RDS, MySQL, Oracle, DIS, and ECS, you can create data connections in Management Center to distinguish data lake services in the development environment from those in the production environment. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of data lake services. The versions, specifications, components, regions, VPCs, subnets, and related configurations of the two sets of data lake services must be the same. For details on how to create data connections, see :ref:`Creating a Data Connection <dataartsstudio_01_1299>`.
   -  For serverless services (such as DLI), DataArts Studio configures the mapping between data lake services in the production environment and development environment through environment isolation in the management center. The corresponding data lake is automatically switched during the development and production processes. Therefore, you need to prepare two sets of queues and database resources in the serverless data lake service and distinguish them by name suffix. For details, see :ref:`Configuring Environment Isolation for a Workspace in Enterprise Mode <dataartsstudio_01_5105>`.
   -  For GaussDB(DWS), MRS Hive, and MRS Spark, if you **select the same cluster** when creating a data connection, you must configure database mapping on the **Configure Data Source Resource Mapping** page to isolate the development and production environments. For details, see :ref:`DB configuration <dataartsstudio_01_5105__section20609134272018>`.

   For example, if your data lake service is an MRS cluster, you need to prepare two MRS clusters with the same version, specifications, components, region, VPC, and subnet. If some configurations of an MRS cluster are modified, you also need to synchronize the modifications to the other MRS cluster.


Creating a Data Connection
--------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. On the displayed **Manage Data Connections** page, click **Create Data Connection**.


   .. figure:: /_static/images/en-us_image_0000002305439529.png
      :alt: **Figure 1** Creating a data connection

      **Figure 1** Creating a data connection

#. On the displayed page, select a data connection type and configure the parameters listed in :ref:`Table 1 <dataartsstudio_01_1299__table11826143220444>`.

   .. note::

      -  **If two clusters are used** for clustered data sources, such as MRS, GaussDB(DWS), RDS, MySQL, Oracle, DIS, and ECS, you can create data connections in Management Center to distinguish data lake services in the development environment from those in the production environment. The data lake is automatically switched during development and production. Therefore, you need to prepare two sets of data lake services. The versions, specifications, components, regions, VPCs, subnets, and related configurations of the two sets of data lake services must be the same. For details on how to create data connections, see :ref:`Creating a Data Connection <dataartsstudio_01_1299>`.
      -  For serverless services (such as DLI), DataArts Studio configures the mapping between data lake services in the production environment and development environment through environment isolation in the management center. The corresponding data lake is automatically switched during the development and production processes. Therefore, you need to prepare two sets of queues and database resources in the serverless data lake service and distinguish them by name suffix. For details, see :ref:`Configuring Environment Isolation for a Workspace in Enterprise Mode <dataartsstudio_01_5105>`.
      -  For GaussDB(DWS), MRS Hive, and MRS Spark, if you **select the same cluster** when creating a data connection, you must configure database mapping on the **Configure Data Source Resource Mapping** page to isolate the development and production environments. For details, see :ref:`DB configuration <dataartsstudio_01_5105__section20609134272018>`.

   .. _dataartsstudio_01_1299__table11826143220444:

   .. table:: **Table 1** Data connection parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type              | Description                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================+
      | DWS                               | See :ref:`Configuring a DWS Connection <dataartsstudio_01_1300>`.                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DLI                               | See :ref:`Configuring a DLI Connection <dataartsstudio_01_1301>`.                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hive                          | See :ref:`Configuring an MRS Hive Connection <dataartsstudio_01_1306>`.                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS HBase                         | See :ref:`Configuring an MRS HBase Connection <dataartsstudio_01_1307>`.                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Kafka                         | See :ref:`Configuring an MRS Kafka Connection <dataartsstudio_01_1308>`.                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Spark                         | See :ref:`Configuring an MRS Spark Connection <dataartsstudio_01_1314>`.                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS ClickHouse                    | See :ref:`Configuring an MRS ClickHouse Connection <dataartsstudio_01_1309>`.                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hetu                          | See :ref:`Configuring an MRS Hetu Connection <dataartsstudio_01_1310>`.                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Impala                        | See :ref:`Configuring an MRS Impala Connection <dataartsstudio_01_1311>`.                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Doris                         | See :ref:`Configuring an MRS Doris Connection <dataartsstudio_01_1390>`.                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | RDS                               | See :ref:`Configuring an RDS Connection <dataartsstudio_01_1303>`.                                                                                                              |
      |                                   |                                                                                                                                                                                 |
      |                                   | The RDS connection can connect to relational databases such as RDS for MySQL, PostgreSQL, DM, SQL Server, and SAP HANA.                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MySQL (pending offline)           | You are not advised to select this connection type. Instead, You are advised to select **RDS**. For details, see :ref:`Configuring an RDS Connection <dataartsstudio_01_1303>`. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Oracle                            | See :ref:`Configuring an Oracle Connection <dataartsstudio_01_1302>`.                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host Connection                   | See :ref:`Configuring a Host Connection <dataartsstudio_01_1305>`.                                                                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test** to test connectivity of the data connection. If the test fails, the data connection cannot be created.

#. After the test is successful, click **Save**. The system will create the data connection for you.

Related Operations
------------------

-  Edit a data connection: In the data connection list, locate a connection and click **Edit** in the **Operation** column. On the displayed page, modify the parameters listed in :ref:`Table 1 <dataartsstudio_01_1299__table11826143220444>` as needed.

   .. note::

      If you do not want to change the password, you do not need to set it. The system automatically uses the password set when the connection was created.

   Click **Test** to check whether the data connection is normal. If the connection is normal, click **Save**. If the connection is abnormal, the data connection cannot be created. Modify the connection parameters as prompted and try again.

-  Delete a data connection: In the data connection list, locate a connection and click **Delete** in the **Operation** column. In the displayed dialog box, confirm the data connection information, and click **OK**.

   If the connection to be deleted is being used, it cannot be deleted directly. In this case, you need to stop the connection from being used on the console of each component and try again.

   .. note::

      If a data connection is deleted, the data table information of the data connection will also be deleted. Exercise caution when performing this operation.
