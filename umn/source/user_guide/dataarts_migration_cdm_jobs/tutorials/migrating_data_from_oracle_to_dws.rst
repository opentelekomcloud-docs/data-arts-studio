:original_name: dataartsstudio_01_0133.html

.. _dataartsstudio_01_0133:

Migrating Data from Oracle to DWS
=================================

Scenario
--------

CDM supports table-to-table migration. This section describes how to use CDM to migrate data from Oracle to Data Warehouse Service (DWS). The procedure is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0133__en-us_topic_0000001193296031_section3548195211>`
#. :ref:`Creating an Oracle Link <dataartsstudio_01_0133__en-us_topic_0000001193296031_section1136440015>`
#. :ref:`Creating a DWS Link <dataartsstudio_01_0133__en-us_topic_0000001193296031_section796691518119>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0133__en-us_topic_0000001193296031_section383292919118>`

Prerequisites
-------------

-  You have obtained a DWS cluster and the IP address, port number, database name, username, and password for connecting to the DWS database. In addition, you must have the read, write, and delete permissions on the DWS database.
-  You have obtained the IP address, name, username, and password of the Oracle database.
-  If the Oracle database is deployed on an on-premises data center or a third-party cloud, ensure that an IP address that can be accessed from the public network has been configured for the Oracle database, or the VPN or Direct Connect between the on-premises data center and cloud has been established.
-  You have uploaded the Oracle database driver on the **Job Management** > **Links** > **Driver Management** page.

.. _dataartsstudio_01_0133__en-us_topic_0000001193296031_section3548195211:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The VPC, subnet, and security group of the CDM cluster must be the same as those of the DWS cluster.
   -  If the same subnet and security group cannot be used, for security reasons, ensure that a security group rule has been configured to allow the CDM cluster to access the CSS cluster.

#. After the CDM cluster is created, locate the row that contains the cluster and click **Bind EIP** in the **Operation** column. (CDM uses an EIP to access the Oracle data source.)

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0133__en-us_topic_0000001193296031_section1136440015:

Creating an Oracle Link
-----------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.

#. Select **Oracle** and click **Next** to configure parameters for the link.


   .. figure:: /_static/images/en-us_image_0000002269203933.png
      :alt: **Figure 1** Creating an Oracle link

      **Figure 1** Creating an Oracle link

   .. table:: **Table 1** Oracle link parameters

      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Parameter       | Description                                                                                                | Example Value       |
      +=================+============================================================================================================+=====================+
      | Name            | Enter a unique link name.                                                                                  | oracle_link         |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Server | Database server domain name or IP address                                                                  | 192.168.0.1         |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Port            | Oracle database port                                                                                       | 3306                |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Connection Type | Type of the Oracle database link                                                                           | Service Name        |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Name   | Name of the database to be connected                                                                       | db_user             |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Username        | User who has the read permission of the Oracle database                                                    | admin               |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Password        | Password used for logging in to the Oracle database                                                        | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Use Agent       | The agent function will be unavailable soon and does not need to be configured.                            | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Agent           | The agent function will be unavailable soon and does not need to be configured.                            | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Oracle Version  | The latest version is used by default. If the version is incompatible, select another version.             | Later than 12.1     |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Driver Version  | A driver version that adapts to the Oracle database                                                        | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Fetch Size      | Number of rows obtained by each request                                                                    | 1000                |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Link Attributes | Custom attributes of the link                                                                              | useCompression=true |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+
      | Reference Sign  | Delimiter used to separate referenced table names or column names This parameter is left blank by default. | '                   |
      +-----------------+------------------------------------------------------------------------------------------------------------+---------------------+

#. Click **Save**. The **Links** page is displayed.

.. _dataartsstudio_01_0133__en-us_topic_0000001193296031_section796691518119:

Creating a DWS Link
-------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.

#. Select **Data Warehouse Service** and click **Next** to configure the DWS link parameters. Set the mandatory parameters listed in :ref:`Table 2 <dataartsstudio_01_0133__en-us_topic_0000001193296031_en-us_topic_0108275326_en-us_topic_0108275298_table385644710314>` and retain the default values for the optional parameters.

   .. _dataartsstudio_01_0133__en-us_topic_0000001193296031_en-us_topic_0108275326_en-us_topic_0108275298_table385644710314:

   .. table:: **Table 2** DWS link parameters

      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter       | Description                                                                                                                                            | Example Value |
      +=================+========================================================================================================================================================+===============+
      | Name            | Enter a unique link name.                                                                                                                              | dwslink       |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Server | IP address or domain name of the DWS database                                                                                                          | 192.168.0.3   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Port            | DWS database port                                                                                                                                      | 8000          |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Name   | Name of the DWS database                                                                                                                               | db_demo       |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Username        | User who has the read, write, and delete permissions on the DWS database                                                                               | dbadmin       |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Password        | Password of the user                                                                                                                                   | ``-``         |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Agent       | The agent function will be unavailable soon and does not need to be configured.                                                                        | ``-``         |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Agent           | The agent function will be unavailable soon and does not need to be configured.                                                                        | ``-``         |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Import Mode     | **COPY**: Migrate the source data to the DWS management node and then copy the data to DataNodes. To access DWS through the Internet, select **COPY**. | COPY          |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Save**.

.. _dataartsstudio_01_0133__en-us_topic_0000001193296031_section383292919118:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from the Oracle database to DWS.


   .. figure:: /_static/images/en-us_image_0000002269203941.jpg
      :alt: **Figure 2** Creating a job for migrating data from Oracle to DWS

      **Figure 2** Creating a job for migrating data from Oracle to DWS

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **oracle_link** created in :ref:`Creating an Oracle Link <dataartsstudio_01_0133__en-us_topic_0000001193296031_section1136440015>`.
      -  **Schema/Tablespace**: Enter the name of the database whose data is to be migrated.
      -  **Table Name**: Enter the name of the table whose data is to be migrated.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **dwslink** created in :ref:`Creating a DWS Link <dataartsstudio_01_0133__en-us_topic_0000001193296031_section796691518119>`.
      -  **Schema/Tablespace**: Select the DWS database to which data is to be written.
      -  **Auto Table Creation**: This parameter is displayed only when both the migration source and destination are relational databases.
      -  **Table Name**: Name of the table to which data is to be written. You can enter a table name that does not exist. CDM automatically creates the table in DWS.
      -  **Orientation**: You can create row- or column-store tables as needed. Generally, if a table contains many columns (called a wide table) and its query involves only a few columns, column storage is recommended. If a table contains only a few columns and a query includes most of the fields, row storage is recommended.
      -  **Extend char length**: If the data encoding formats of the migration source and destination are different, the character length of the automatic table creation may be insufficient. If you select **Yes** for this parameter, the character length will be increased by three times during automatic table creation.
      -  **Clear Data Before Import**: whether to clear data in the destination table before the migration task starts.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields, as shown in :ref:`Figure 3 <dataartsstudio_01_0133__en-us_topic_0000001193296031_fig1534811262293>`.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  The expressions in CDM support field conversion of common character strings, dates, and values.

   .. _dataartsstudio_01_0133__en-us_topic_0000001193296031_fig1534811262293:

   .. figure:: /_static/images/en-us_image_0000002234244496.png
      :alt: **Figure 3** Table-to-table field mapping

      **Figure 3** Table-to-table field mapping

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: Enable it if you need to configure scheduled jobs. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. You can increase the value of this parameter to improve migration efficiency.
   -  **Write Dirty Data**: Dirty data may be generated during data migration between tables. You are advised to select **Yes**.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.

.. note::

   If the migration times out because writing data to the destination costs a long time, reduce the value of the **Fetch Size** parameter.
