:original_name: dataartsstudio_01_0092.html

.. _dataartsstudio_01_0092:

Migrating Data from MySQL to MRS Hive
=====================================

MRS provides enterprise-level big data clusters on the cloud. It contains HDFS, Hive, and Spark components and is applicable to massive data analysis of enterprises.

Hive supports SQL to help users perform extraction, transformation, and loading (ETL) operations on large-scale data sets. Query on large-scale data sets takes a long time. In many scenarios, you can create Hive partitions to reduce the total amount of data to be scanned each time. This significantly improves query performance.

Hive partitions are implemented by using the HDFS subdirectory function. Each subdirectory contains the column names and values of each partition. If there are multiple partitions, many HDFS subdirectories exist. It is not easy to load external data to each partition of the Hive table without relying on tools. With CDM, you can easily load data of the external data sources (relational databases, object storage services, and file system services) to Hive partition tables.

This section describes how to migrate data from the MySQL database to the MRS Hive partition table.

Scenario
--------

Suppose that there is a **trip_data** table in the MySQL database. The table stores cycling records such as the start time, end time, start sites, end sites, and rider IDs. For details about the fields in the **trip_data** table, see :ref:`Figure 1 <dataartsstudio_01_0092__en-us_topic_0111325168_fig5406153795610>`.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_fig5406153795610:

.. figure:: /_static/images/en-us_image_0000001373169085.png
   :alt: **Figure 1** MySQL table fields

   **Figure 1** MySQL table fields

The following describes how to use CDM to import the **trip_data** table in the MySQL database to the MRS Hive partition table. The procedure is as follows:

#. :ref:`Creating a Hive Partition Table on MRS Hive <dataartsstudio_01_0092__en-us_topic_0111325168_section143383811272>`
#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0092__en-us_topic_0111325168_section563314494359>`
#. :ref:`Creating a MySQL Link <dataartsstudio_01_0092__en-us_topic_0111325168_section459563891734>`
#. :ref:`Creating a Hive Link <dataartsstudio_01_0092__en-us_topic_0111325168_section209397834812>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0092__en-us_topic_0111325168_section1821596484>`

Prerequisites
-------------

-  MRS is available.
-  You have obtained the IP address, port, database name, username, and password for connecting to the MySQL database. In addition, the user must have the read and write permissions on the MySQL database.
-  You have uploaded a MySQL database driver by following the instructions provided in :ref:`Managing Drivers <dataartsstudio_01_0132>`.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section143383811272:

Creating a Hive Partition Table on MRS Hive
-------------------------------------------

On MRS Hive, run the following SQL statement to create a Hive partition table named **trip_data** with three new fields **y**, **ym**, and **ymd** used as partition fields. The SQL statement is as follows:

::

   create table trip_data(TripID int,Duration int,StartDate timestamp,StartStation varchar(64),StartTerminal int,EndDate timestamp,EndStation varchar(64),EndTerminal int,Bike int,SubscriberType varchar(32),ZipCodev varchar(10))partitioned by (y int,ym int,ymd int);

.. note::

   The **trip_data** partition table has three partition fields: year, year and month, and year, month, and date of the start time of a ride. For example, if the start time of a ride is **2018/5/11 9:40**, the record is saved in the **trip_data/2018/201805/20180511** partition. When the records in the **trip_data** table are summarized, only part of the data needs to be scanned, greatly improving the performance.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section563314494359:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The CDM and MRS clusters must be in the same VPC, subnet, and security group.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access MySQL.


   .. figure:: /_static/images/en-us_image_0000001322088024.png
      :alt: **Figure 2** Cluster list

      **Figure 2** Cluster list

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section459563891734:

Creating a MySQL Link
---------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.

#. Select **MySQL** and click **Next**. On the page that is displayed, configure MySQL link parameters.

   Click **Show Advanced Attributes** and set optional parameters. For details, see :ref:`Link to a Common Relational Database <dataartsstudio_01_0044>`. Retain the default values of the optional parameters and configure the mandatory parameters according to :ref:`Table 1 <dataartsstudio_01_0092__en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490>`.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490:

   .. table:: **Table 1** MySQL link parameters

      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter       | Description                                                                                                                                                                 | Example Value |
      +=================+=============================================================================================================================================================================+===============+
      | Name            | Unique link name                                                                                                                                                            | mysqllink     |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Server | IP address or domain name of the MySQL database server                                                                                                                      | 192.168.1.110 |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Port            | MySQL database port                                                                                                                                                         | 3306          |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Name   | Name of the MySQL database                                                                                                                                                  | sqoop         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Username        | User who has the read, write, and delete permissions on the MySQL database                                                                                                  | admin         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Password        | Password of the user                                                                                                                                                        | ``-``         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Agent       | Whether to extract data from the data source through an agent                                                                                                               | Yes           |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Agent           | Click **Select** to select the agent created in :ref:`Connecting to an Agent <dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_section1072083564713>`. | ``-``         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Save**. The **Link Management** page is displayed.

   .. note::

      If an error occurs during the saving, the security settings of the MySQL database are incorrect. In this case, you need to enable the EIP of the CDM cluster to access the MySQL database.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section209397834812:

Creating a Hive Link
--------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.

#. Select **MRS Hive** and click **Next** to configure parameters for the MRS Hive link.


   .. figure:: /_static/images/en-us_image_0000001322089284.png
      :alt: **Figure 3** Creating a Hive link

      **Figure 3** Creating a Hive link

   :ref:`Table 2 <dataartsstudio_01_0092__en-us_topic_0111325168_table6441152003419>` describes the parameters. You can configure the parameters according to the actual situation.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_table6441152003419:

   .. table:: **Table 2** MRS Hive link parameters

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                   | Example Value         |
      +=======================+===============================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                                                                                                                                                                                                            | hivelink              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Manager IP            | Floating IP address of MRS Manager. Click **Select** next to the **Manager IP** text box to select an MRS cluster. CDM automatically fills in the authentication information.                                                                                                                                                                                                 | 127.0.0.1             |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Authentication Method | Authentication method used for accessing MRS                                                                                                                                                                                                                                                                                                                                  | SIMPLE                |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  **SIMPLE**: Select this for non-security mode.                                                                                                                                                                                                                                                                                                                             |                       |
      |                       | -  **KERBEROS**: Select this for security mode.                                                                                                                                                                                                                                                                                                                               |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | HIVE Version          | Set this to the Hive version on the server.                                                                                                                                                                                                                                                                                                                                   | HIVE_3_X              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Username              | If **Authentication Method** is set to **KERBEROS**, you must provide the username and password used for logging in to MRS Manager. If you need to create a snapshot when exporting a directory from HDFS, the user configured here must have the administrator permission on HDFS.                                                                                           | cdm                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | To create a data connection for an MRS security cluster, do not use user **admin**. The **admin** user is the default management page user and cannot be used as the authentication user of the security cluster. You can create an MRS user and set **Username** and **Password** to the username and password of the created MRS user when creating an MRS data connection. |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       |    -  If the CDM cluster version is 2.9.0 or later and the MRS cluster version is 3.1.0 or later, the created user must have the permissions of the **Manager_viewer** role to create links on CDM. To perform operations on databases, tables, and data of a component, you also need to add the user group permissions of the component to the user.                        |                       |
      |                       |    -  If the CDM cluster version is earlier than 2.9.0 or the MRS cluster version is earlier than 3.1.0, the created user must have the permissions of **Manager_administrator** or **System_administrator** to create links on CDM.                                                                                                                                          |                       |
      |                       |    -  A user with only the **Manager_tenant** or **Manager_auditor** permission cannot create connections.                                                                                                                                                                                                                                                                    |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Password              | Password used for logging in to MRS Manager                                                                                                                                                                                                                                                                                                                                   | ``-``                 |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS storage support   | The server must support OBS storage. When creating a Hive table, you can store the table in OBS.                                                                                                                                                                                                                                                                              | No                    |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Run Mode              | This parameter is used only when the Hive version is **HIVE_3_X**. Possible values are:                                                                                                                                                                                                                                                                                       | EMBEDDED              |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  **EMBEDDED**: The link instance runs with CDM. This mode delivers better performance.                                                                                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | -  **Standalone**: The link instance runs in an independent process. If CDM needs to connect to multiple Hadoop data sources (MRS, Hadoop, or CloudTable) with both Kerberos and Simple authentication modes, select **STANDALONE** or configure different agents.                                                                                                            |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       |    Note: The STANDALONE mode is used to solve the version conflict problem. If the connector versions of the source and destination ends of the same link are different, a JAR file conflict occurs. In this case, you need to place the source or destination end in the STANDALONE process to prevent the migration failure caused by the conflict.                         |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Use Cluster Config    | You can use the cluster configuration to simplify parameter settings for the Hadoop connection.                                                                                                                                                                                                                                                                               | No                    |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Cluster Config Name   | This parameter is valid only when **Use Cluster Config** is set to **Yes**. Select a cluster configuration that has been created.                                                                                                                                                                                                                                             | hive_01               |
      |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                       | For details, see :ref:`Managing Cluster Configurations <dataartsstudio_01_1096>`.                                                                                                                                                                                                                                                                                             |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section1821596484:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a data migration job. :ref:`Figure 4 <dataartsstudio_01_0092__en-us_topic_0111325168_fig125979433490>` illustrates how to create a migration job.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_fig125979433490:

   .. figure:: /_static/images/en-us_image_0000001322409160.png
      :alt: **Figure 4** Creating a job for migrating data from MySQL to Hive

      **Figure 4** Creating a job for migrating data from MySQL to Hive

   .. note::

      Set **Clear Data Before Import** to **Yes**, so that the data in the Hive table will be cleared before data import.

#. After the parameters are configured, click **Next**. The **Map Field** tab page is displayed. See :ref:`Figure 5 <dataartsstudio_01_0092__en-us_topic_0111325168_fig1461204384916>`.

   Map the fields of the MySQL table and Hive table. The Hive table has three more fields **y**, **ym**, and **ymd** than the MySQL table, which are the Hive partition fields. Because the fields of the source table cannot be directly mapped to the destination table, you need to configure an expression to extract data from the **StartDate** field in the source table.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_fig1461204384916:

   .. figure:: /_static/images/en-us_image_0000001373288809.png
      :alt: **Figure 5** Hive field mapping

      **Figure 5** Hive field mapping

#. Click |image1| to display the **Converter List** dialog box, and then choose **Create Converter** > **Expression conversion**. See :ref:`Figure 6 <dataartsstudio_01_0092__en-us_topic_0111325168_fig261294344916>`.

   The expressions for the **y**, **ym**, and **ymd** fields are as follows:

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyy")**

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyyMM")**

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyyMMdd")**

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_fig261294344916:

   .. figure:: /_static/images/en-us_image_0000001321928760.png
      :alt: **Figure 6** Configuring the expression

      **Figure 6** Configuring the expression

   .. note::

      The expressions in CDM support field conversion of common character strings, dates, and values.

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: To configure scheduled jobs, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. Retain the default value **1**.
   -  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link. Retain the default value **No** so that dirty data is not recorded.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.

.. |image1| image:: /_static/images/en-us_image_0000001373408489.png
