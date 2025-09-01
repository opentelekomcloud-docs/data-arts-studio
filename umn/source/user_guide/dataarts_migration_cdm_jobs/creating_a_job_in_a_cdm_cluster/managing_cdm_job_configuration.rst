:original_name: dataartsstudio_01_0083.html

.. _dataartsstudio_01_0083:

Managing CDM Job Configuration
==============================

On the **Settings** tab page, you can perform the following operations:

-  :ref:`Maximum Concurrent Extractors <dataartsstudio_01_0083__en-us_topic_0173586861_section19611105617510>`
-  :ref:`Scheduled Backup/Restoration <dataartsstudio_01_0083__en-us_topic_0173586861_section11184152932110>`
-  :ref:`Environment Variables of Job Parameters <dataartsstudio_01_0083__en-us_topic_0173586861_section10589151615203>`

.. _dataartsstudio_01_0083__en-us_topic_0173586861_section19611105617510:

Maximum Concurrent Extractors
-----------------------------

Maximum number of concurrent extraction tasks in a cluster

.. note::

   This parameter is also available on the **Cluster Configuration** page. You can change its value either on this page or the **Cluster Configuration** page.

CDM migrates data through data migration jobs. It works in the following way:

#. When data migration jobs are submitted, CDM splits each job into multiple tasks based on the **Concurrent Extractors** parameter in the job configuration.

   .. note::

      Jobs for different data sources may be split based on different dimensions. Some jobs may not be split based on the **Concurrent Extractors** parameter.

#. CDM submits the tasks to the running pool in sequence. Tasks (defined by **Maximum Concurrent Extractors**) run concurrently. Excess tasks are queued.

By setting appropriate values for the **Concurrent Extractors** and **Maximum Concurrent Extractors** parameters, you can accelerate migration.

#. You are advised to set **Maximum Concurrent Extractors** to twice the number of vCPUs. For details, see :ref:`Table 1 <dataartsstudio_01_0083__en-us_topic_0173586861_en-us_topic_0000001287646722_table1992816477328>`.

   .. _dataartsstudio_01_0083__en-us_topic_0173586861_en-us_topic_0000001287646722_table1992816477328:

   .. table:: **Table 1** Recommended maximum number of concurrent extractors for a CDM cluster

      =========== ================ =========================================
      Flavor      vCPUs/Memory     Recommended Maximum Concurrent Extractors
      =========== ================ =========================================
      cdm.large   8 vCPUs, 16 GB   16
      cdm.xlarge  16 vCPUs, 32 GB  32
      cdm.4xlarge 64 vCPUs, 128 GB 128
      =========== ================ =========================================

#. Configure the number of concurrent extractors based on the following rules:

   a. When data is to be migrated to files, CDM does not support multiple concurrent tasks. In this case, set a single process to extract data.
   b. If each row of the table contains less than or equal to 1 MB data, data can be extracted concurrently. If each row contains more than 1 MB data, it is recommended that data be extracted in a single thread.
   c. Set **Concurrent Extractors** for a job based on **Maximum Concurrent Extractors** for the cluster. It is recommended that the value of **Concurrent Extractors** is less than that of **Maximum Concurrent Extractors**.
   d. If the migration source is Hive and JDBC is used to read data, CDM does not support multi-concurrency. In this case, set the number of concurrent extractors to 1.
   e. If the destination is DLI, you are advised to set the number of concurrent extractors to 1. Otherwise, data may fail to be written.

.. _dataartsstudio_01_0083__en-us_topic_0173586861_section11184152932110:

Scheduled Backup/Restoration
----------------------------

This function depends on the OBS service. Backup files cannot be automatically aged. You need to manually delete backup files on a regular basis.

-  Prerequisites

   An OBS link has been created. For details, see :ref:`OBS Link Parameters <dataartsstudio_01_0045>`.

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

Environment Variables of Job Parameters
---------------------------------------

When creating a migration job on CDM, the parameter (such as the OBS bucket name or file path) that can be manually configured, a field in a parameter, or a character in a field can be configured as a global variable, so that you can change parameter values in batches, or batch replace certain characters after jobs are exported or imported.
