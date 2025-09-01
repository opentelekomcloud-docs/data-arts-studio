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

.. figure:: /_static/images/en-us_image_0000002234085224.png
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
-  You have uploaded the MySQL database driver on the **Job Management** > **Links** > **Driver Management** page.

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

#. The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The CDM and MRS clusters must be in the same VPC, subnet, and security group.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access MySQL.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section459563891734:

Creating a MySQL Link
---------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.

#. Select **RDS for MySQL** and click **Next** to set the link parameters.


   .. figure:: /_static/images/en-us_image_0000002234245040.png
      :alt: **Figure 2** Creating a MySQL Link

      **Figure 2** Creating a MySQL Link

   Click **Show Advanced Attributes** to view more optional parameters. For details, see :ref:`RDS for MySQL/MySQL Database Link Parameters <dataartsstudio_01_1211>`. Retain the default values for the optional parameters and configure the mandatory parameters described in :ref:`Table 1 <dataartsstudio_01_0092__en-us_topic_0108275298_table5321744015490>`.

   .. _dataartsstudio_01_0092__en-us_topic_0108275298_table5321744015490:

   .. table:: **Table 1** MySQL link parameters

      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter                  | Description                                                                                                                                                                                                                                                      | Example Value |
      +============================+==================================================================================================================================================================================================================================================================+===============+
      | Name                       | Enter a unique link name.                                                                                                                                                                                                                                        | mysqllink     |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Server            | IP address or domain name of the MySQL database                                                                                                                                                                                                                  | N/A           |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Port                       | MySQL database port                                                                                                                                                                                                                                              | 3306          |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Name              | Name of the MySQL database                                                                                                                                                                                                                                       | sqoop         |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Username                   | User who has the read, write, and delete permissions on the MySQL database                                                                                                                                                                                       | admin         |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Password                   | Password of the user                                                                                                                                                                                                                                             | N/A           |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Local API              | Whether to use the local API of the database for acceleration. (The system attempts to enable the **local_infile** system variable of the MySQL database.)                                                                                                       | Yes           |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Agent                  | Whether to extract data from the data source through an agent                                                                                                                                                                                                    | No            |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | local_infile Character Set | When using local_infile to import data to MySQL, you can configure the encoding format.                                                                                                                                                                          | utf8          |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Driver Version             | Before connecting CDM to a relational database, you need to upload the JDK 8 .jar driver of the relational database. Download the MySQL driver 5.1.48 from https://downloads.mysql.com/archives/c-j/, obtain **mysql-connector-java-5.1.48.jar**, and upload it. | N/A           |
      +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Save**. The **Link Management** page is displayed.

   .. note::

      If an error occurs during the saving, the security settings of the MySQL database are incorrect. In this case, you need to enable the EIP of the CDM cluster to access the MySQL database.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section209397834812:

Creating a Hive Link
--------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002234235252.png
      :alt: **Figure 3** Selecting a connector type

      **Figure 3** Selecting a connector type

#. Select **MRS Hive** and click **Next** to configure parameters for the MRS Hive link.

   :ref:`Table 2 <dataartsstudio_01_0092__en-us_topic_0111325168_table6441152003419>` lists the parameters. Configure these parameters based on your actual situation.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_table6441152003419:

   .. table:: **Table 2** MRS Hive link parameters

      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                | Example Value         |
      +==============================+============================================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Name                         | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                                                                                                                                                                                                                                                                         | hivelink              |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Manager IP                   | Floating IP address of MRS Manager. Click **Select** next to the **Manager IP** text box to select an MRS cluster. CDM automatically fills in the authentication information.                                                                                                                                                                                                                                                              | 127.0.0.1             |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    DataArts Studio does not support MRS clusters whose Kerberos encryption type is **aes256-sha2,aes128-sha2**, and only supports MRS clusters whose Kerberos encryption type is **aes256-sha1,aes128-sha1**.                                                                                                                                                                                                                              |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Authentication Method        | Authentication method used for accessing MRS                                                                                                                                                                                                                                                                                                                                                                                               | SIMPLE                |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | -  **SIMPLE**: Select this for non-security mode.                                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                              | -  **KERBEROS**: Select this for security mode.                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | HIVE Version                 | Set this to the Hive version on the server.                                                                                                                                                                                                                                                                                                                                                                                                | HIVE_3_X              |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Username                     | If **Authentication Method** is set to **KERBEROS**, you must provide the username and password used for logging in to MRS Manager. If you need to create a snapshot when exporting a directory from HDFS, the user configured here must have the administrator permission on HDFS.                                                                                                                                                        | cdm                   |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | To create a data connection for an MRS security cluster, do not use user **admin**. The **admin** user is the default management page user and cannot be used as the authentication user of the security cluster. You can create an MRS user and set **Username** and **Password** to the username and password of the created MRS user when creating an MRS data connection.                                                              |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    -  If the CDM cluster version is 2.9.0 or later and the MRS cluster version is 3.1.0 or later, the created user must have the permissions of the **Manager_viewer** role to create links on CDM. To perform operations on databases, tables, and columns of an MRS component, you also need to add the database, table, and column permissions of the MRS component to the user by following the instructions in the MRS documentation. |                       |
      |                              |    -  If the CDM cluster version is earlier than 2.9.0 or the MRS cluster version is earlier than 3.1.0, the created user must have the permissions of **Manager_administrator** or **System_administrator** to create links on CDM.                                                                                                                                                                                                       |                       |
      |                              |    -  A user with only the **Manager_tenant** or **Manager_auditor** permission cannot create connections.                                                                                                                                                                                                                                                                                                                                 |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Password                     | Password used for logging in to MRS Manager                                                                                                                                                                                                                                                                                                                                                                                                | ``-``                 |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enable ldap                  | This parameter is available when **Proxy connection** is selected for **Connection Type**.                                                                                                                                                                                                                                                                                                                                                 | No                    |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | If LDAP authentication is enabled for an external LDAP server connected to MRS Hive, the LDAP username and password are required for authenticating the connection to MRS Hive. In this case, this option must be enabled. Otherwise, the connection will fail.                                                                                                                                                                            |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | ldapUsername                 | This parameter is mandatory when **Enable ldap** is enabled.                                                                                                                                                                                                                                                                                                                                                                               | ``-``                 |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | Enter the username configured when LDAP authentication was enabled for MRS Hive.                                                                                                                                                                                                                                                                                                                                                           |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | ldapPassword                 | This parameter is mandatory when **Enable ldap** is enabled.                                                                                                                                                                                                                                                                                                                                                                               | ``-``                 |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | Enter the password configured when LDAP authentication was enabled for MRS Hive.                                                                                                                                                                                                                                                                                                                                                           |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS storage support          | The server must support OBS storage. When creating a Hive table, you can store the table in OBS.                                                                                                                                                                                                                                                                                                                                           | No                    |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | AK                           | This parameter is mandatory when **OBS storage support** is enabled. The account corresponding to the AK/SK pair must have the OBS Buckets Viewer permission. Otherwise, OBS cannot be accessed and the "403 AccessDenied" error is reported.                                                                                                                                                                                              | ``-``                 |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | You need to create an access key for the current account and obtain an AK/SK pair.                                                                                                                                                                                                                                                                                                                                                         |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | a. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.                                                                                                                                                                                                                                                                                     |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | b. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 4 <dataartsstudio_01_0092__en-us_topic_0108618545_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.                                                                                                                                                                                                     |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    .. _dataartsstudio_01_0092__en-us_topic_0108618545_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:                                                                                                                                                                                                                                                                                                                |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    .. figure:: /_static/images/en-us_image_0000002269194761.png                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |       :alt: **Figure 4** Clicking Create Access Key                                                                                                                                                                                                                                                                                                                                                                                        |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |       **Figure 4** Clicking Create Access Key                                                                                                                                                                                                                                                                                                                                                                                              |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | c. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.                                                                                                                                                                                                         |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    .. note::                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |       -  Only two access keys can be added for each user.                                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                              |       -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.                                                                                                                                                                                                                              |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | SK                           |                                                                                                                                                                                                                                                                                                                                                                                                                                            | ``-``                 |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Run Mode                     | This parameter is used only when the Hive version is **HIVE_3_X**. Possible values are:                                                                                                                                                                                                                                                                                                                                                    | EMBEDDED              |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | -  **EMBEDDED**: The link instance runs with CDM. This mode delivers better performance.                                                                                                                                                                                                                                                                                                                                                   |                       |
      |                              | -  **Standalone**: The link instance runs in an independent process. If CDM needs to connect to multiple Hadoop data sources (MRS, Hadoop, or CloudTable) with both Kerberos and Simple authentication modes, **Standalone** prevails.                                                                                                                                                                                                     |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |    .. note::                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              |       The **STANDALONE** mode is used to solve the version conflict problem. If the connector versions of the source and destination ends of the same link are different, a JAR file conflict occurs. In this case, you need to place the source or destination end in the STANDALONE process to prevent the migration failure caused by the conflict.                                                                                     |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Check Hive JDBC Connectivity | Whether to check the Hive JDBC connectivity                                                                                                                                                                                                                                                                                                                                                                                                | No                    |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Use Cluster Config           | You can use the cluster configuration to simplify parameter settings for the Hadoop connection.                                                                                                                                                                                                                                                                                                                                            | No                    |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Cluster Config Name          | This parameter is valid only when **Use Cluster Config** is set to **Yes**. Select a cluster configuration that has been created.                                                                                                                                                                                                                                                                                                          | hive_01               |
      |                              |                                                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                              | For details about how to configure a cluster, see "DataArts Migration" > "Managing Links" > "Managing Cluster Configurations" in *User Guide*.                                                                                                                                                                                                                                                                                             |                       |
      +------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0092__en-us_topic_0111325168_section1821596484:

Creating a Migration Job
------------------------

#. Click the **Table/File Migration** tab and then **Create Job**.

   .. note::

      Set **Clear Data Before Import** to **Yes**, so that the data in the Hive table will be cleared before data import.

#. After configuring the parameters, click **Next** to go to the **Map Field** page shown in :ref:`Figure 5 <dataartsstudio_01_0092__en-us_topic_0111325168_fig1461204384916>`.

   Map the fields of the MySQL table and Hive table. The Hive table has three more fields **y**, **ym**, and **ymd** than the MySQL table, which are the Hive partition fields. Because the fields of the source table cannot be directly mapped to the destination table, you need to configure an expression to extract data from the **StartDate** field in the source table.

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_fig1461204384916:

   .. figure:: /_static/images/en-us_image_0000002269204489.png
      :alt: **Figure 5** Hive field mapping

      **Figure 5** Hive field mapping

#. Click |image1| to display the **Converter List** dialog box, and then choose **Create Converter** > **Expression conversion**. See :ref:`Figure 6 <dataartsstudio_01_0092__en-us_topic_0111325168_fig261294344916>`.

   The expressions for the **y**, **ym**, and **ymd** fields are as follows:

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyy")**

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyyMM")**

   **DateUtils.format(DateUtils.parseDate(row[2],"yyyy-MM-dd HH:mm:ss.SSS"),"yyyyMMdd")**

   .. _dataartsstudio_01_0092__en-us_topic_0111325168_fig261294344916:

   .. figure:: /_static/images/en-us_image_0000002234245052.png
      :alt: **Figure 6** Configuring the expression

      **Figure 6** Configuring the expression

   .. note::

      The expressions in CDM support field conversion of common character strings, dates, and values.

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry If Failed**: Determine whether to automatically retry the job if it fails. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: Determine whether to automatically execute the job at a scheduled time. Retain the default value **No** in this example.
   -  **Concurrent Extractors**: Enter the number of concurrent extractors. An appropriate value improves migration efficiency. Retain the default value **1**.
   -  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link on the CDM console. Retain the default value **No** so that dirty data is not recorded.


   .. figure:: /_static/images/en-us_image_0000002269114701.png
      :alt: **Figure 7** Configuring the task

      **Figure 7** Configuring the task

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.

.. |image1| image:: /_static/images/en-us_image_0000002269204497.png
