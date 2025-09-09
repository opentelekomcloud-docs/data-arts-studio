:original_name: dataartsstudio_01_0024.html

.. _dataartsstudio_01_0024:

Creating a Link Between CDM and a Data Source
=============================================

Scenario
--------

Before creating a data migration job, create a link to enable the CDM cluster to read data from and write data to a data source. A migration job requires a source link and a destination link. For details on the data sources that can be exported (source links) and imported (destination links) in different migration modes (table/file migration), see :ref:`Supported Data Sources <dataartsstudio_01_0215>`.

The link configurations depend on the data source. This section describes how to create these links.

Constraints
-----------

-  If changes occur in the connected data source (for example, the MRS cluster capacity is expanded), you need to edit and save the connection.
-  Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

Prerequisites
-------------

-  A CDM cluster is available.
-  The CDM cluster can communicate with the destination data source.

   -  If the destination data source is an on-premises database, you need the Internet or Direct Connect. When using the Internet, ensure that an EIP has been bound to the CDM cluster, the security group of CDM allows outbound traffic from the host where the off-cloud data source is located, the host where the data source is located can access the Internet, and the connection port has been enabled in the firewall rules.
   -  If the destination data source is a cloud service (such as DWS, MRS, and ECS), the following requirements must be met for network interconnection:

      -  If the CDM cluster and the cloud service are in different regions, a public network or a dedicated connection is required for enabling communication between the CDM cluster and the cloud service. If the Internet is used for communication, ensure that an EIP has been bound to the CDM cluster, the host where the data source is located can access the Internet, and the port has been enabled in the firewall rules.
      -  If the CDM cluster and the cloud service are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding Routes to a Route Table" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in Virtual Private Cloud (VPC) x.x.x User Guide in Virtual Private Cloud (VPC) x.x.x Usage Guide.
      -  The cloud service instance and the CDM cluster belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

-  You have obtained the URL and the account for accessing the data source. The account is granted with the read and write permissions for the data source.

Creating Links
--------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`. On the DataArts Studio console, locate a workspace and click **DataArts Migration** to access the CDM console.

#. On the CDM console, choose **Cluster Management** in the left navigation pane. Locate the row that contains the target cluster and click **Job Management** in the **Operation** column. On the displayed **Links** page, click **Create Link**. On the displayed page, select a connector.

   The connectors are classified based on the type of the data source to be connected. All supported data types are displayed.


   .. figure:: /_static/images/en-us_image_0000002234235252.png
      :alt: **Figure 1** Selecting a connector type

      **Figure 1** Selecting a connector type

#. Select a data source and click **Next**. The following describes how to create a MySQL link.

   The link parameters of different data sources vary. :ref:`Table 1 <dataartsstudio_01_0024__en-us_topic_0108275477_table6478165716378>` describes the link parameters.

   .. _dataartsstudio_01_0024__en-us_topic_0108275477_table6478165716378:

   .. table:: **Table 1** Link parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Connector                         | Description                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================+
      | -  RDS for PostgreSQL             | Because the JDBC drivers used by these relational databases are the same, the parameters to be configured are also the same and are described in :ref:`PostgreSQL/SQLServer Link Parameters <dataartsstudio_01_0044>`. |
      | -  RDS for SQL Server             |                                                                                                                                                                                                                        |
      | -  PostgreSQL                     |                                                                                                                                                                                                                        |
      | -  Microsoft SQL Server           |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Warehouse Service            | For details about the parameters, see :ref:`GaussDB(DWS) Link Parameters <dataartsstudio_01_0226>`.                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SAP HANA                          | For details about the parameters, see :ref:`SAP HANA Link Parameters <dataartsstudio_01_0227>`.                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MySQL                             | For details about the parameters, see :ref:`RDS for MySQL/MySQL Database Link Parameters <dataartsstudio_01_1211>`.                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Oracle                            | For details about the parameters, see :ref:`Oracle Database Link Parameters <dataartsstudio_01_1212>`.                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database Sharding                 | For details about the parameters, see :ref:`Shard Link Parameters <dataartsstudio_01_1214>`.                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Object Storage Service (OBS)      | For details about the parameters, see :ref:`OBS Link Parameters <dataartsstudio_01_0045>`.                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  MRS HDFS                       | If the data source is HDFS of MRS, Apache Hadoop, or FusionInsight HD, see :ref:`HDFS Link Parameters <dataartsstudio_01_0040>`.                                                                                       |
      | -  FusionInsight HDFS             |                                                                                                                                                                                                                        |
      | -  Apache HDFS                    |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  MRS HBase                      | If the data source is HBase of MRS, Apache Hadoop, or FusionInsight HD, see :ref:`HBase Link Parameters <dataartsstudio_01_0039>`.                                                                                     |
      | -  FusionInsight HBase            |                                                                                                                                                                                                                        |
      | -  Apache HBase                   |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  MRS Hive                       | If the data source is Hive on MRS, Apache Hadoop, or FusionInsight HD, see :ref:`Hive Link Parameters <dataartsstudio_01_0026>`.                                                                                       |
      | -  FusionInsight Hive             |                                                                                                                                                                                                                        |
      | -  Apache Hive                    |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | CloudTable Service                | If the data source is CloudTable, see :ref:`CloudTable Link Parameters <dataartsstudio_01_0027>`.                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  FTP                            | If the data source is an FTP or SFTP server, see :ref:`FTP/SFTP Link Parameters <dataartsstudio_01_0028>`.                                                                                                             |
      | -  SFTP                           |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTP                              | These connectors are used to read files with an HTTP/HTTPS URL, such as reading public files on the third-party object storage system and web disks.                                                                   |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | When creating an HTTP link, you only need to configure the link name. The URL is configured during job creation.                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MongoDB                           | If the data source is a local MongoDB, see :ref:`MongoDB Link Parameters <dataartsstudio_01_0030>`.                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Document Database Service (DDS)   | If the data source is DDS, see :ref:`DDS Link Parameters <dataartsstudio_01_0031>`.                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  Redis                          | If the data source is Redis or DCS, see :ref:`Redis Link Parameters <dataartsstudio_01_0032>`.                                                                                                                         |
      | -  Distributed Cache Service      |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | -  MRS Kafka                      | If the data source is MRS Kafka or Apache Kafka, see :ref:`Kafka Link Parameters <dataartsstudio_01_0033>`.                                                                                                            |
      | -  Apache Kafka                   |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud Search Service (CSS)        | If the data source is CSS or Elasticsearch, see :ref:`CSS Link Parameters <dataartsstudio_01_0035>`.                                                                                                                   |
      |                                   |                                                                                                                                                                                                                        |
      | Elasticsearch                     |                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Lake Insight                 | If the data source is DLI, see :ref:`DLI Link Parameters <dataartsstudio_01_0036>`.                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DMS Kafka                         | If the data source is DMS Kafka, see :ref:`DMS Kafka Link Parameters <dataartsstudio_01_0038>`.                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cassandra                         | If the data source is Cassandra, see :ref:`Cassandra Link Parameters <dataartsstudio_01_004501>`.                                                                                                                      |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | .. note::                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |    Cassandra is not supported in version 2.9.3.300 or later.                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Hudi                          | For details about the parameters, see :ref:`MRS Hudi Link Parameters <dataartsstudio_01_0184>`.                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS ClickHouse                    | For details about the parameters, see :ref:`MRS ClickHouse Link Parameters <dataartsstudio_01_0285>`.                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | LogHub (SLS)                      | For details about the parameters, see :ref:`LogHub (SLS) Link Parameters <dataartsstudio_01_0288>`.                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Shentong database                 | For details about the parameters, see :ref:`ShenTong Database Link Parameters <dataartsstudio_01_0290>`.                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      Currently, the following data sources are in the OBT phase: FusionInsight HDFS, FusionInsight HBase, FusionInsight Hive, SAP HANA, Document Database Service, CloudTable Service, Cassandra, DMS Kafka, Cloud Search Service, Sharding Database, and ShenTong Database.

#. After configuring the parameters of the link, click **Test** to check whether the link is available. Alternatively, click **Save**, and the system checks automatically.

   If the network is poor or the data source is too large, the link test may take 30 to 60 seconds.

Managing Links
--------------

CDM allows you to perform the following operations on created links:

-  Deleting links: You can delete links that are not used by any job.
-  Editing a link: You can modify link parameters but cannot reselect the connector. To modify a link, you need to re-enter the password needed to access the data source.
-  Testing connectivity: You can test connectivity of a link that has been saved.
-  Viewing the JSON file of a link: You can view parameters of a link in a JSON file.
-  Editing the JSON file of a link: Modify parameters of a link in a JSON file.
-  Viewing the backend link: You can view the backend link corresponding to a link. For example, you can query details about the backend link if it is enabled.

Before managing a link, ensure that the link is not used by any job to avoid affecting job execution. The procedure for managing connections is as follows:

#. Log in to the management console and choose **Service List** > **Cloud Data Migration**. On the CDM console, choose **Cluster Management** in the left navigation pane. Locate the row that contains the target cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab.
#. On the **Links** page, locate the link to be modified.

   -  Deleting a link: Click **Delete** in the **Operation** column to delete a link. Alternatively, select the links that are not used by any job and click **Delete Link** above the list to delete them.
   -  Editing the link: Click the link name or click **Edit** in the **Operation** column to access the page for modifying the link. When modifying the link, you need to enter the password for logging in to the data source again.
   -  Testing connectivity of the link: Click **Test Connectivity** in the **Operation** column.
   -  Viewing the JSON file of the link: In the **Operation** column, choose **More** > **View Link JSON** to view link parameters in JSON format.
   -  Editing the JSON file of the link: In the **Operation** column, choose **More** > **Edit Link JSON** to modify link parameters in JSON format.
   -  Viewing the backend link: Locate the row that contains a link and click **More** in the **Operation** column and select **View Backend Link** to view the backend link corresponding to the link.
