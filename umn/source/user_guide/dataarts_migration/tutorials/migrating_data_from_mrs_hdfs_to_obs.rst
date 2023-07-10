:original_name: dataartsstudio_01_0103.html

.. _dataartsstudio_01_0103:

Migrating Data from MRS HDFS to OBS
===================================

Scenario
--------

CDM supports file-to-file data migration. This section describes how to migrate data from MRS HDFS to OBS. The process is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0103__en-us_topic_0284710797_section1596917553011>`
#. :ref:`Creating an MRS HDFS Link <dataartsstudio_01_0103__en-us_topic_0284710797_section136013511582>`
#. :ref:`Creating an OBS Link <dataartsstudio_01_0103__en-us_topic_0284710797_section5774720191611>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0103__en-us_topic_0284710797_section119151411712>`

Prerequisites
-------------

-  You have obtained the domain name, port number, AK, and SK for accessing OBS.
-  MRS is available.
-  Your EIP quota is sufficient.

.. _dataartsstudio_01_0103__en-us_topic_0284710797_section1596917553011:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The VPC, subnet, and security group of the CDM cluster must be the same as those of the MRS cluster.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access MRS HDFS.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0103__en-us_topic_0284710797_section136013511582:

Creating an MRS HDFS Link
-------------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.
#. Select **MRS HDFS** and click **Next** to configure parameters for the MRS HDFS link.

   -  **Name**: Enter a custom link name, for example, **mrs_hdfs_link**.

   -  **Manager IP**: IP address of MRS Manager. Click **Select** next to the **Manager IP** text box to select a created MRS cluster. CDM automatically fills in the authentication information.

   -  **Username**: If **Authentication Method** is set to **KERBEROS**, set the username and password for logging in to MRS Manager.

      If you need to create a snapshot when exporting a directory from HDFS, the user configured here must have the administrator permission on HDFS.

   -  **Password**: password for logging in to MRS Manager

   -  **Authentication Method**: authentication method for accessing MRS

   -  **Run Mode**: Select the running mode of the HDFS link.

.. _dataartsstudio_01_0103__en-us_topic_0284710797_section5774720191611:

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

.. _dataartsstudio_01_0103__en-us_topic_0284710797_section119151411712:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from the MRS HDFS database to OBS.


   .. figure:: /_static/images/en-us_image_0000001373087857.jpg
      :alt: **Figure 2** Creating a job for migrating data from MRS HDFS to OBS

      **Figure 2** Creating a job for migrating data from MRS HDFS to OBS

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **hdfs_llink** created in :ref:`Creating an MRS HDFS Link <dataartsstudio_01_0103__en-us_topic_0284710797_section136013511582>`.
      -  **Source Directory/File**: Enter the directory or file path of the data to be migrated.
      -  **File Format**: Select the file format used for data transmission. Select **Binary**. If files are transferred without being parsed, the file format does not have to be **Binary**. This applies to file copy.
      -  Retain the default values of other optional parameters. For details, see :ref:`From HDFS <dataartsstudio_01_0049>`.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **obs_link** created in :ref:`Creating an OBS Link <dataartsstudio_01_0103__en-us_topic_0284710797_section5774720191611>`.
      -  **Bucket Name**: Select the bucket from which the data will be migrated.
      -  **Write Directory**: Enter the directory to which data is to be written on the OBS server.
      -  **File Format**: Select **Binary**.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**. For details, see :ref:`To OBS <dataartsstudio_01_0062>`.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  The expressions in CDM support field conversion of common character strings, dates, and values.

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: To configure scheduled jobs, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. CDM supports concurrent extraction of multiple files. Increasing the value of this parameter can improve migration efficiency.
   -  **Write Dirty Data**: Select **No**. The file-to-file migration is binary, and no dirty data will be generated.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**. You can also set this parameter to **Delete** to prevent an accumulation of too many migration jobs.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.
