:original_name: dataartsstudio_01_0083.html

.. _dataartsstudio_01_0083:

Job Configuration Management
============================

On the **Settings** tab page, you can perform the following operations:

-  :ref:`Maximum Concurrent Extractors of Jobs <dataartsstudio_01_0083__en-us_topic_0173586861_section19611105617510>`
-  :ref:`Scheduled Backup and Restoration of CDM Jobs <dataartsstudio_01_0083__en-us_topic_0173586861_section11184152932110>`
-  :ref:`Environment Variables of CDM Job Parameters <dataartsstudio_01_0083__en-us_topic_0173586861_section10589151615203>`

.. _dataartsstudio_01_0083__en-us_topic_0173586861_section19611105617510:

Maximum Concurrent Extractors of Jobs
-------------------------------------

The value of this parameter ranges from 1 to 300. If the total number of extractors exceeds the value of this parameter, the excess extractors are queued. Determine the maximum number of concurrent extractors based on the number of concurrent extractors of each job.

Configure the number of concurrent extractors of a job based on the following rules:

The number of concurrent extractors in a CDM migration job is related to the cluster specifications and table size. The value range is 1 to 300. If the value is too large, the extractors are queued.

You are advised to set 4 concurrent extractors for each 1 CU (1 CU = 1 vCPU and 4 GB), as listed in :ref:`Table 1 <dataartsstudio_01_0083__en-us_topic_0173586861_en-us_topic_0000001225868959_table17343144375319>`. You can also adjust the value as needed. If each row of the table contains less than or equal to 1 MB data, you can extract data concurrently. If each row contains more than 1 MB data, you are advised to extract data in a single thread.

.. note::

   -  When data is to be migrated to files, CDM does not support multiple concurrent tasks. In this case, set a single process to extract data.
   -  The number of concurrent extractors of a job is affected by **Maximum Concurrent Extractors** configured on the **Settings** page. The **Maximum Concurrent Extractors** parameter specifies the total number of concurrent extractions.

.. _dataartsstudio_01_0083__en-us_topic_0173586861_en-us_topic_0000001225868959_table17343144375319:

.. table:: **Table 1** Reference configurations of concurrent extractors

   ================== ================ =====================
   CDM Cluster Flavor vCPUs/Memory     Concurrent Extractors
   ================== ================ =====================
   cdm.large          8 vCPUs, 16 GB   16
   cdm.xlarge         16 vCPUs, 32 GB  32
   cdm.4xlarge        64 vCPUs, 128 GB 128
   ================== ================ =====================

.. _dataartsstudio_01_0083__en-us_topic_0173586861_section11184152932110:

Scheduled Backup and Restoration of CDM Jobs
--------------------------------------------

This function depends on the OBS service.

-  Prerequisites

   You have created the :ref:`Link to OBS <dataartsstudio_01_0045>`.

-  Scheduled backup

   On the **Job Management** page, click **Settings** and configure **Scheduled Backup** and its related parameters.

   .. table:: **Table 2** Scheduled backup parameters

      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                    | Description                                                                                                                                                          | Example Value         |
      +==============================+======================================================================================================================================================================+=======================+
      | Scheduled Backup             | Whether to enable automatic backup. This function is used to back up jobs but not links.                                                                             | Enable                |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Backup Policy                | -  **All jobs**: CDM backs up all table/file migration jobs and entire DB migration jobs regardless of the job statuses. However, historical jobs are not backed up. | All jobs              |
      |                              | -  **All jobs by groups**: You select one or more job groups to back up.                                                                                             |                       |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Backup Cycle                 | Select the backup cycle.                                                                                                                                             | Day                   |
      |                              |                                                                                                                                                                      |                       |
      |                              | -  **Day**: The backup is performed daily at 00:00:00.                                                                                                               |                       |
      |                              | -  **Week**: The backup is performed at 00:00:00 every Monday.                                                                                                       |                       |
      |                              | -  **Month**: The backup is performed at 00:00:00 on the first day of each month.                                                                                    |                       |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS Link for Writing Backups | Link used to back up jobs to OBS buckets. Select a link you have created on the **Links** page.                                                                      | obslink               |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS Bucket                   | OBS bucket where backup files are stored                                                                                                                             | cdm                   |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Backup Data Directory        | Directory where backup files are stored                                                                                                                              | /cdm-bk/              |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

-  Restoring jobs

   If automatic backup has been performed, the backup list is displayed on the **Configuration Management** tab page. The OBS buckets where the backup files reside, backup paths, and backup time are displayed.

   You can click **Restore Backup** in the **Operation** column of the backup list to restore the CDM jobs.

.. _dataartsstudio_01_0083__en-us_topic_0173586861_section10589151615203:

Environment Variables of CDM Job Parameters
-------------------------------------------

When creating a migration job on CDM, the parameter (such as the OBS bucket name or file path) that can be manually configured, a field in a parameter, or a character in a field can be configured as a global variable, so that you can change parameter values in batches, or batch replace certain characters after jobs are exported or imported.

The following describes how to batch replace the OBS bucket name in a migration job.

#. On the **Job Management** page, click the **Configuration Management** tab and configure environment variables.

   .. code-block::

      bucket_1=A
      bucket_2=B

   Variable **bucket_1** indicates bucket A, and variable **bucket_2** indicates bucket B.

#. On the page for creating a CDM migration job, migrate data from bucket A to bucket B.

   Set the source bucket name to **${bucket_1}** and destination bucket name to **${bucket_2}**.


   .. figure:: /_static/images/en-us_image_0000001373288793.png
      :alt: **Figure 1** Setting the bucket names to environment variables

      **Figure 1** Setting the bucket names to environment variables

#. If you want to migrate data from bucket C to bucket D, you do not need to change the job parameters. You only need to change the environment variables on the **Configuration Management** tab page as follows:

   .. code-block::

      bucket_1=C
      bucket_2=D
