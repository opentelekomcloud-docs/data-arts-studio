:original_name: dataartsstudio_01_0085.html

.. _dataartsstudio_01_0085:

Managing Jobs in Batches
========================

Scenario
--------

This section describes how to manage CDM table/file migration jobs in batches. The following operations are involved:

-  Manage jobs by group.
-  Run jobs in batches.
-  Delete jobs in batches.
-  Export jobs in batches.
-  Import jobs in batches.

You can export and import jobs in batches in the following scenarios:

-  Job migration between CDM clusters: You can migrate jobs from a cluster of an earlier version to a new version.
-  Job backup: You can stop or delete CDM clusters to reduce costs. In this case, you can export the job scripts in batches and save them, and create a cluster and import the job scripts if necessary.
-  Batch job creation: You can manually create a job and export the job configuration file in JSON format. Copy the content in the JSON file to the same file or new files, and then import the file/files to CDM to create jobs in batches.

Procedure
---------

#. Log in to the management console and choose **Service List** > **Cloud Data Migration**. In the left navigation pane, choose **Cluster Management**. Locate the target cluster and click **Job Management**.
#. Click **Table/File Migration**. The job list is displayed. You can perform the following batch operations:

   -  **Manage jobs by group.**

      CDM allows users to add, modify, search for, and delete job groups. When a group is deleted, all jobs in the group are deleted.

      In the third step of creating a job, if jobs have been assigned to different groups, you can display, start, or export jobs by group.

   -  **Run jobs in batches.**

      After selecting one or more jobs, click **Run** to start these jobs in batches.

   -  **Delete jobs in batches.**

      After selecting one or more jobs, click **Delete** to delete these jobs in batches.

   -  **Export jobs in batches.**

      Click **Export**.


      .. figure:: /_static/images/en-us_image_0000001373288565.png
         :alt: **Figure 1** Export

         **Figure 1** Export

      -  **All jobs and links**: Export all jobs and links at a time.
      -  **All jobs**: Export all jobs at a time.
      -  **All links**: Export all links at a time.
      -  **Jobs by name**: Select the jobs to export and click **OK**.
      -  **All jobs by groups**: Select the group to export and click **OK**.

      Exported jobs are stored in JSON files, which can be used as backups or imported to other clusters.

      .. note::

         For security purposes, no link password is exported when jobs are exported. All passwords are replaced by *Add password here*.

   -  **Import jobs in batches.**

      Click **Import** and select the import format (text file or JSON).

      -  **By JSON string**: Job files to be imported must be in JSON format and the file size cannot exceed 1 MB. If the job files to be imported are exported from CDM, edit the JSON files before importing them to CDM. Replace *Add password here* with the correct link passwords.
      -  **By text file**: This mode can be used when the local JSON files cannot be uploaded properly. Paste the JSON strings for the jobs into the text box.
