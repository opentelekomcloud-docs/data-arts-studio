:original_name: dataartsstudio_01_0100.html

.. _dataartsstudio_01_0100:

Migrating Data from MySQL to OBS
================================

Scenario
--------

CDM supports table-to-OBS data migration. This section describes how to migrate tables from a MySQL database to OBS. The process is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0100__en-us_topic_0284710796_section1596917553011>`
#. :ref:`Creating a MySQL Link <dataartsstudio_01_0100__en-us_topic_0284710796_section4972205516016>`
#. :ref:`Creating an OBS Link <dataartsstudio_01_0100__en-us_topic_0284710796_section5774720191611>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0100__en-us_topic_0284710796_section119151411712>`

Prerequisites
-------------

-  You have obtained the domain name, port number, AK, and SK for accessing OBS.
-  You have obtained the IP address, port, database name, username, and password for connecting to the MySQL database. In addition, the user must have the read and write permissions on the MySQL database.
-  You have uploaded a MySQL database driver by following the instructions provided in :ref:`Managing Drivers <dataartsstudio_01_0132>`.

.. _dataartsstudio_01_0100__en-us_topic_0284710796_section1596917553011:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access MySQL.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0100__en-us_topic_0284710796_section4972205516016:

Creating a MySQL Link
---------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.

#. Select **MySQL** and click **Next**. On the page that is displayed, configure MySQL link parameters.

   Click **Show Advanced Attributes** and set optional parameters. For details, see :ref:`Link to a Common Relational Database <dataartsstudio_01_0044>`. Retain the default values of the optional parameters and configure the mandatory parameters according to :ref:`Table 1 <dataartsstudio_01_0100__en-us_topic_0284710796_en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490>`.

   .. _dataartsstudio_01_0100__en-us_topic_0284710796_en-us_topic_0111325168_en-us_topic_0108275298_table5321744015490:

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

.. _dataartsstudio_01_0100__en-us_topic_0284710796_section5774720191611:

Creating an OBS Link
--------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001373288365.png
      :alt: **Figure 1** Selecting a connector type

      **Figure 1** Selecting a connector type

#. Select **Object Storage Service (OBS)** and click **Next** to configure parameters for the OBS link.

   -  **Name**: Enter a custom link name, for example, **obslink**.
   -  **OBS Server** and **Port**: Enter the actual OBS address information.
   -  **AK** and **SK**: Enter the AK and SK used for logging in to OBS.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0100__en-us_topic_0284710796_section119151411712:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from the MySQL database to OBS.


   .. figure:: /_static/images/en-us_image_0000001322248252.jpg
      :alt: **Figure 2** Creating a job for migrating data from MySQL to OBS

      **Figure 2** Creating a job for migrating data from MySQL to OBS

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **mysqllink** created in :ref:`Creating a MySQL Link <dataartsstudio_01_0100__en-us_topic_0284710796_section4972205516016>`.
      -  **Use SQL Statement**: Select **No**.
      -  **Schema/Tablespace**: name of the schema or tablespace from which data is to be extracted
      -  **Table Name**: name of the table from which data is to be extracted
      -  Retain the default values of other optional parameters. For details, see :ref:`From a Common Relational Database <dataartsstudio_01_0054>`.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **obslink** created in :ref:`Creating an OBS Link <dataartsstudio_01_0100__en-us_topic_0284710796_section5774720191611>`.
      -  **Bucket Name**: Select the bucket from which the data will be migrated.
      -  **Write Directory**: Enter the directory to which data is to be written on the OBS server.
      -  **File Format**: Select **CSV**.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**. For details, see :ref:`To OBS <dataartsstudio_01_0062>`.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields, as shown in :ref:`Figure 3 <dataartsstudio_01_0100__en-us_topic_0284710796_fig231883016327>`.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  The expressions in CDM support field conversion of common character strings, dates, and values.

   .. _dataartsstudio_01_0100__en-us_topic_0284710796_fig231883016327:

   .. figure:: /_static/images/en-us_image_0000001321928660.jpg
      :alt: **Figure 3** Table-to-file field mapping

      **Figure 3** Table-to-file field mapping

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: To configure scheduled jobs, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. CDM supports concurrent extraction of MySQL data. If indexes are configured for the source table, you can increase the number of concurrent extractors to accelerate the migration.
   -  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link. For file-to-table data migration, you are advised to write dirty data.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**. You can also set this parameter to **Delete** to prevent an accumulation of too many migration jobs.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.
