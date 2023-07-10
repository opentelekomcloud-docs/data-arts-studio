:original_name: dataartsstudio_01_0101.html

.. _dataartsstudio_01_0101:

Migrating Data from MySQL to DWS
================================

Scenario
--------

CDM supports table-to-table data migration. This section describes how to migrate data from MySQL to DWS. The process is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0101__en-us_topic_0284710798_section1596917553011>`
#. :ref:`Creating a MySQL Link <dataartsstudio_01_0101__en-us_topic_0284710798_section4972205516016>`
#. :ref:`Creating a DWS Link <dataartsstudio_01_0101__en-us_topic_0284710798_section5774720191611>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0101__en-us_topic_0284710798_section119151411712>`

Prerequisites
-------------

-  You have obtained the IP address, port number, database name, username, and password for connecting to DWS. In addition, you must have the read, write, and delete permissions on the DWS database.
-  You have obtained the IP address, port, database name, username, and password for connecting to the MySQL database. In addition, the user must have the read and write permissions on the MySQL database.
-  You have uploaded a MySQL database driver by following the instructions provided in :ref:`Managing Drivers <dataartsstudio_01_0132>`.

.. _dataartsstudio_01_0101__en-us_topic_0284710798_section1596917553011:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The VPC, subnet, and security group of the CDM cluster must be the same as those of the DWS cluster.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access MySQL.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0101__en-us_topic_0284710798_section4972205516016:

Creating a MySQL Link
---------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.

#. Select **MySQL** and click **Next**. On the page that is displayed, configure MySQL link parameters.

   Click **Show Advanced Attributes** and set optional parameters. For details, see :ref:`Link to a Common Relational Database <dataartsstudio_01_0044>`. Retain the default values of the optional parameters and configure the mandatory parameters according to :ref:`Table 1 <dataartsstudio_01_0101__en-us_topic_0284710798_en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490>`.

   .. _dataartsstudio_01_0101__en-us_topic_0284710798_en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490:

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

.. _dataartsstudio_01_0101__en-us_topic_0284710798_section5774720191611:

Creating a DWS Link
-------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.

#. Select **Data Warehouse Service** and click **Next** to configure the DWS link parameters. Set the mandatory parameters listed in :ref:`Table 2 <dataartsstudio_01_0101__en-us_topic_0284710798_en-us_topic_0108275326_en-us_topic_0108275298_table385644710314>` and retain the default values for the optional parameters.

   .. _dataartsstudio_01_0101__en-us_topic_0284710798_en-us_topic_0108275326_en-us_topic_0108275298_table385644710314:

   .. table:: **Table 2** DWS link parameters

      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter       | Description                                                                                                                                                                  | Example Value |
      +=================+==============================================================================================================================================================================+===============+
      | Name            | Enter a unique link name.                                                                                                                                                    | dwslink       |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Server | IP address or domain name of the DWS database                                                                                                                                | 192.168.0.3   |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Port            | DWS database port                                                                                                                                                            | 8000          |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Name   | Name of the DWS database                                                                                                                                                     | db_demo       |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Username        | User who has the read, write, and delete permissions on the DWS database                                                                                                     | dbadmin       |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Password        | Password of the user                                                                                                                                                         | ``-``         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Agent       | Whether to extract data from the data source through an agent                                                                                                                | Yes           |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Agent           | Click **Select** and select the agent created in :ref:`Connecting to an Agent <dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_section1072083564713>`. | ``-``         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Import Mode     | **COPY**: Migrate the source data to the DWS management node and then copy the data to DataNodes. To access DWS through the Internet, select **COPY**.                       | COPY          |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Save**.

.. _dataartsstudio_01_0101__en-us_topic_0284710798_section119151411712:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from the MySQL database to DWS.


   .. figure:: /_static/images/en-us_image_0000001373408537.jpg
      :alt: **Figure 1** Creating a job for migrating data from MySQL to DWS

      **Figure 1** Creating a job for migrating data from MySQL to DWS

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **mysqllink** created in :ref:`Creating a MySQL Link <dataartsstudio_01_0101__en-us_topic_0284710798_section4972205516016>`.
      -  **Use SQL Statement**: Select **No**.
      -  **Schema/Tablespace**: name of the schema or tablespace from which data is to be extracted
      -  **Table Name**: name of the table from which data is to be extracted
      -  Retain the default values of other optional parameters. For details, see :ref:`From a Common Relational Database <dataartsstudio_01_0054>`.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **dwslink** created in :ref:`Creating a DWS Link <dataartsstudio_01_0101__en-us_topic_0284710798_section5774720191611>`.
      -  **Schema/Tablespace**: Select the DWS database to which data is to be written.
      -  **Auto Table Creation**: This parameter is displayed only when both the migration source and destination are relational databases.
      -  **Table Name**: Name of the table to which data is to be written. You can enter a table name that does not exist. CDM automatically creates the table in DWS.
      -  **isCompress**: whether to compress data. If you select **Yes**, high-level compression will be performed. CDM applies to compression scenarios where the I/O read/write volume is large and the CPU is sufficient (the computing load is relatively low).
      -  **Orientation**: You can create row- or column-store tables as needed. Generally, if a table contains many columns (called a wide table) and its query involves only a few columns, column storage is recommended. If a table contains only a few columns and a query includes most of the fields, row storage is recommended.
      -  **Extend char length**: If the data encoding formats of the migration source and destination are different, the character length of the automatic table creation may be insufficient. If you select **Yes** for this parameter, the character length will be increased by three times during automatic table creation.
      -  **Clear Data Before Import**: whether to clear data in the destination table before the migration task starts.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields, as shown in :ref:`Figure 2 <dataartsstudio_01_0101__en-us_topic_0284710798_fig1534811262293>`.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  You can map fields in batches.
   -  The expressions in CDM support field conversion of common character strings, dates, and values.

   .. _dataartsstudio_01_0101__en-us_topic_0284710798_fig1534811262293:

   .. figure:: /_static/images/en-us_image_0000001321928808.png
      :alt: **Figure 2** Table-to-table field mapping

      **Figure 2** Table-to-table field mapping

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: To configure scheduled jobs, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. You can increase the value of this parameter to improve migration efficiency.
   -  **Write Dirty Data**: Dirty data may be generated during data migration between tables. You are advised to select **Yes**.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.
