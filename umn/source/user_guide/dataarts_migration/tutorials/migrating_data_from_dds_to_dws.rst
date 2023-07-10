:original_name: dataartsstudio_01_0087.html

.. _dataartsstudio_01_0087:

Migrating Data from DDS to DWS
==============================

Scenario
--------

CDM allows you to migrate data from DDS to other data sources. This section describes how to use CDM to migrate data from DDS to DWS. The procedure includes four steps:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0087__en-us_topic_0108275326_section459563891734>`
#. :ref:`Creating a DDS Link <dataartsstudio_01_0087__en-us_topic_0108275326_section1241410274356>`
#. :ref:`Creating a DWS Link <dataartsstudio_01_0087__en-us_topic_0108275326_section6526141353915>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0087__en-us_topic_0108275326_section18225563716>`

Prerequisites
-------------

-  DWS/DDS is available.
-  You have obtained the IP address, port number, database name, username, and password for connecting to the DWS and DDS databases. In addition, you must have the read, write, and delete permissions for the DDS and DWS databases.

.. _dataartsstudio_01_0087__en-us_topic_0108275326_section459563891734:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  If DDS and DWS are deployed in the same VPC, the newly created CDM cluster also needs to be deployed in that VPC, with no EIP bound. The CDM cluster's subnet and security group can be the same as those of the DDS or DWS cluster. You can also configure a security group rule to enable the CDM cluster to access the cluster of another service (DWS or DDS).
   -  If DDS and DWS are not deployed in the same VPC, the newly created CDM cluster needs to be in the same VPC as DDS and :ref:`an EIP must be bound <dataartsstudio_01_0020>` for the CDM cluster to access the DWS cluster.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access DWS. If DDS and DWS are in the same VPC, do not bind an EIP to the CDM cluster.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0087__en-us_topic_0108275326_section1241410274356:

Creating a DDS Link
-------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.
#. Select **Document Database Service** and click **Next** to configure parameters for the DDS link.

   .. table:: **Table 1** DDS link parameters

      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter     | Description                                                                                                                                                        | Example Value                     |
      +===============+====================================================================================================================================================================+===================================+
      | Name          | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                 | mongo_link                        |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Server List   | Address list of the DDS cluster. The format is **IP address or domain name of the database server:port number**. Separate multiple server lists by semicolons (;). | 192.168.0.1:7300;192.168.0.2:7301 |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Database Name | Name of the DDS database to be connected                                                                                                                           | DB_mongodb                        |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Username      | Username used for logging in to the DDS database                                                                                                                   | cdm                               |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Password      | Password used for logging in to the DDS database                                                                                                                   | ``-``                             |
      +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0087__en-us_topic_0108275326_section6526141353915:

Creating a DWS Link
-------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.

#. Select **Data Warehouse Service** and click **Next** to configure the DWS link parameters. Set the mandatory parameters listed in :ref:`Table 2 <dataartsstudio_01_0087__en-us_topic_0108275326_en-us_topic_0108275298_table385644710314>` and retain the default values for the optional parameters.

   .. _dataartsstudio_01_0087__en-us_topic_0108275326_en-us_topic_0108275298_table385644710314:

   .. table:: **Table 2** DWS link parameters

      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Parameter       | Description                                                                                                                                                                 | Example Value |
      +=================+=============================================================================================================================================================================+===============+
      | Name            | Unique link name                                                                                                                                                            | dwslink       |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Server | IP address or domain name of the DWS database server                                                                                                                        | 192.168.0.3   |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Port            | DWS database port                                                                                                                                                           | 8000          |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Database Name   | Name of the DWS database                                                                                                                                                    | db_demo       |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Username        | User who has the read, write, and delete permissions on the DWS database                                                                                                    | dbadmin       |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Password        | Password of the user                                                                                                                                                        | ``-``         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Use Agent       | Whether to extract data from the data source through an agent                                                                                                               | Yes           |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+
      | Agent           | Click **Select** to select the agent created in :ref:`Connecting to an Agent <dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_section1072083564713>`. | ``-``         |
      +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+

#. Click **Save**.

.. _dataartsstudio_01_0087__en-us_topic_0108275326_section18225563716:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a data migration job.

#. Configure the required job information:

   -  **Job Name**: Enter a unique job name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **mongo_link** link created in :ref:`Creating a DDS Link <dataartsstudio_01_0087__en-us_topic_0108275326_section1241410274356>`.
      -  **Database Name**: Select the database whose data is to be migrated.
      -  **Collection Name**: Enter the name of the MongoDB collection on DDS, which is similar to the table name in a relational database.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **dwslink** link created in :ref:`Creating a DWS Link <dataartsstudio_01_0087__en-us_topic_0108275326_section6526141353915>`.
      -  **Schema/Tablespace**: Select the DWS database to which data is to be written.
      -  **Table Name**: Name of the table to which data is to be written. You can manually enter a table name that does not exist. CDM automatically creates the table on DWS.
      -  **Clear Data Before Import**: Choose whether to clear data in the destination table before data import.

#. Click **Next**. The **Map Field** tab page is displayed. CDM automatically maps table fields at the migration source and destination. Check whether the field mapping is correct.

   -  If the field mapping is incorrect, click the row where the field is located and drag the field to adjust the mapping.
   -  When importing data to DWS, you need to manually select the distribution columns of DWS. You are advised to select the distribution columns according to the following principles:

      a. Use the primary key as the distribution column.
      b. If multiple data segments are combined as primary keys, specify all primary keys as the distribution column.
      c. In the scenario where no primary key is available, if no distribution column is selected, DWS uses the first column as the distribution column by default. As a result, data skew risks exist.

   -  If you want to convert the content of the source fields, perform the operations in this step. In this example, field conversion is not required.

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
