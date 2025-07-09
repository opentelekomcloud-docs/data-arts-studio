:original_name: dataartsstudio_01_0084.html

.. _dataartsstudio_01_0084:

Managing a Single Job
=====================

Existing CDM jobs can be viewed, modified, deleted, started, and stopped. This section describes how to view and modify a job.

Viewing a Job
-------------

-  **Viewing job status**

   The job status can be **New**, **Pending**, **Booting**, **Running**, **Failed**, **Succeeded**, or **Stopped**.

   **Pending** indicates that the job is waiting to be scheduled by the system, and **Booting** indicates that the data to be migrated is being analyzed.

-  **Viewing the historical records**

   On the **Historical Record** page, you can view job execution records, read/write statistics, and job execution logs.

-  **Viewing job logs**

   On the **Historical Record** page, you can view all logs of a job.

   Alternatively, in the **Operation** column, choose **More** > **Log** to view the latest logs of the job.

-  **Viewing the JSON file of a job**

   You can directly edit the JSON file of a job, which is equivalent to modifying the parameter settings of the job.

-  **Querying the job statistics**

   You can open the preview window of a configured database job and view up to 1,000 pieces of data. By comparing the number of data records of the migration source and destination, you can check whether the migration was successful and whether data was lost.

Modifying a Job
---------------

-  **Modifying the job parameters**

   You can reconfigure job parameters, but you cannot reselect source and destination links.

-  **Editing the JSON file of a job**

   You can directly edit the JSON file of a job, which is equivalent to modifying the parameter settings of the job.

Procedure
---------

#. Log in to the management console and choose **Service List** > **Cloud Data Migration**. In the left navigation pane, choose **Cluster Management**. Locate the target cluster and click **Job Management**.

#. Click **Historical Jobs** to view all historical jobs executed in the latest month.

   CDM stores the jobs executed in the last month, including one-time jobs (jobs that are automatically deleted after execution) and jobs that are executed periodically. You can view and re-execute the jobs on the **Historical Jobs** tab page.

   For a job that is executed periodically, a historical job is generated on the **Historical Jobs** tab page each time when the job is executed, regardless of whether the job is executed successfully. The names of historical jobs will be the same as the original job but with a random character string appended.

#. Click **Table/File Migration**. The job list is displayed. You can perform the following operations on a single job:

   -  Modify the job parameters: Click **Edit** in the **Operation** column to modify the job parameters.

   -  Run the job: Click **Run** in the **Operation** column to manually start the job.

   -  View the historical records: Click **Historical Record** in the **Operation** column. On the **Historical Record** page that is displayed, view the job's historical execution records and read/write statistics. Click **Log** to view the job logs.

   -  Delete the job: Choose **More** > **Delete** in the **Operation** column to delete the job.

   -  Stop the job: Choose **More** > **Stop** in the **Operation** column to stop the job.

   -  View the job JSON: Choose **More** > **View Job JSON** in the **Operation** column to view the job JSON.

   -  Edit the job JSON: Choose **More** > **Edit Job JSON** in the **Operation** column to edit the job JSON files, which is similar to modify the job parameters.

   -  Configure a scheduled job: Locate a job and choose **More** > **Configure Scheduled Execution**. You can set the cycle for periodically executing the job. For details, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`.

   -  View logs: Locate a job, click **More** in the **Operation** column, and select **Log** to view the latest log of the job.

      You can also view all logs of the job on the **Historical Record** page.

   -  Retry the job: Locate a failed job, click **More** in the **Operation** column, and select **Retry**. The job will be automatically retried three times.

#. After the modification, click **Save** or **Save and Run**.
