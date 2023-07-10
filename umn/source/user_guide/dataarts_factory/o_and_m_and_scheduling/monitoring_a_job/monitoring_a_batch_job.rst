:original_name: dataartsstudio_01_0508.html

.. _dataartsstudio_01_0508:

Monitoring a Batch Job
======================

In the batch processing mode, data is processed periodically in batches based on the job-level scheduling plan, which is used in scenarios with low real-time requirements. This type of job is a pipeline that consists of one or more nodes and is scheduled as a whole. It cannot run for an unlimited period of time, that is, it must end after running for a certain period of time.

You can choose **Monitor Job** and click the **Batch Job Monitoring** tab to view the scheduling status, frequency, and start time of a batch job, and perform the operations listed in :ref:`Table 1 <dataartsstudio_01_0508__en-us_topic_0159098544_table958254318576>`.


.. figure:: /_static/images/en-us_image_0000001373408505.png
   :alt: **Figure 1** Monitoring a Batch Job

   **Figure 1** Monitoring a Batch Job

.. _dataartsstudio_01_0508__en-us_topic_0159098544_table958254318576:

.. table:: **Table 1** Operations supported by batch job monitoring

   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No. | Operation                                                                                                     | Description                                                                                                                                                                                                                                                              |
   +=====+===============================================================================================================+==========================================================================================================================================================================================================================================================================+
   | 1   | Searching for a job based on the job name or owner                                                            | ``-``                                                                                                                                                                                                                                                                    |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2   | Filtering jobs by whether notifications have been configured, scheduling status, job label, or next plan time | ``-``                                                                                                                                                                                                                                                                    |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3   | Perform operations on jobs in a batch                                                                         | Select multiple jobs and perform operations on them.                                                                                                                                                                                                                     |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4   | Viewing job instance status                                                                                   | Click |image2| in front of the job name. The **Last Instance** page is displayed. You can view information about the last instance of the job.                                                                                                                           |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 5   | Viewing node information of the job                                                                           | Click a job name. On the displayed page, click the job node and view its associated jobs/scripts and monitoring information.                                                                                                                                             |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 6   | Job scheduling operations                                                                                     | In the **Operation** column of a job, you can run, pause, recover, stop, and configure scheduling. For details, see :ref:`Batch Job Monitoring: Scheduling a Job <dataartsstudio_01_0508__en-us_topic_0159100548_section1617819411343>`.                                 |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 7   | Configuring notifications                                                                                     | In the **Operation** column of a job, choose **More** > **Set Notification**. In the displayed dialog box, configure notification parameters. :ref:`Table 1 <dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217>` describes the notification parameters. |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 8   | Monitoring instances                                                                                          | In the **Operation** column of a job, choose **More** > **Monitor Instance** to view the running records of all instances of the job.                                                                                                                                    |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 9   | PatchData                                                                                                     | In the **Operation** column of a job, choose **More** > **PatchData**. For details, see :ref:`Batch Job Monitoring: PatchData <dataartsstudio_01_0508__en-us_topic_0159100548_section1819004120344>`.                                                                    |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 10  | Adding a job label                                                                                            | In the **Operation** column of a job, choose **More** > **Add Job Label**. For details, see :ref:`Batch Job Monitoring: Adding a Job Label <dataartsstudio_01_0508__en-us_topic_0159100548_section12186114111347>`.                                                      |
   +-----+---------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0508__en-us_topic_0159100548_section1617819411343:

Batch Job Monitoring: Scheduling a Job
--------------------------------------

After developing a job, you can manage job scheduling tasks on the **Monitor Job** page. Specific operations include to run, pause, restore, or stop scheduling.


.. figure:: /_static/images/en-us_image_0000001373088293.png
   :alt: **Figure 2** Scheduling a job

   **Figure 2** Scheduling a job

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 3** DataArts Factory

      **Figure 3** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. Click the **Batch Job Monitoring** tab.

#. In the **Operation** column of the job, click **Submit**, **Pause**, **Restore**, or **Stop**.

If a dependent job has been configured for a batch job, you can select either **Start Current Job Only** or **Start Current and Depended Jobs** when submitting the batch job. For details about how to configure dependent jobs, see :ref:`Setting Up Scheduling for a Job Using the Batch Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section1590152794714>`.


.. figure:: /_static/images/en-us_image_0000001321928780.png
   :alt: **Figure 4** Starting a job

   **Figure 4** Starting a job

.. _dataartsstudio_01_0508__en-us_topic_0159100548_section1819004120344:

Batch Job Monitoring: PatchData
-------------------------------

A job executes a scheduling task to generate a series of instances in a certain period of time. This series of instances are called PatchData. PatchData can be used to fix the job instances that have data errors in the historical records or to build job records for debugging programs.

Only the periodically scheduled jobs support PatchData. For details about the execution records of PatchData, see :ref:`Monitoring PatchData <dataartsstudio_01_0512>`.

.. note::

   Do not modify the job configuration when PatchData is being performed. Otherwise, job instances generated during PatchData will be affected.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. Click the **Batch Job Monitoring** tab.

#. In the **Operation** column of the job, choose **More** > **Configure PatchData**.

#. Configure PatchData parameters based on :ref:`Table 2 <dataartsstudio_01_0508__en-us_topic_0159100548_table15019455411>`.


   .. figure:: /_static/images/en-us_image_0000001373288825.jpg
      :alt: **Figure 6** PatchData parameters

      **Figure 6** PatchData parameters

   .. _dataartsstudio_01_0508__en-us_topic_0159100548_table15019455411:

   .. table:: **Table 2** Parameters

      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                          | Description                                                                                                                                                                                           |
      +====================================+=======================================================================================================================================================================================================+
      | PatchData Name                     | Name of the automatically generated PatchData task. The value can be modified.                                                                                                                        |
      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Name                           | Name of the job that requires PatchData.                                                                                                                                                              |
      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Date                               | Period of time when PatchData is required.                                                                                                                                                            |
      |                                    |                                                                                                                                                                                                       |
      |                                    | .. note::                                                                                                                                                                                             |
      |                                    |                                                                                                                                                                                                       |
      |                                    |    PatchData can be configured for a job multiple times. However, avoid configuring PatchData multiple times on the same date to prevent data duplication or disorder.                                |
      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parallel Instances                 | Number of instances to be executed at the same time. A maximum of five instances can be executed at the same time.                                                                                    |
      |                                    |                                                                                                                                                                                                       |
      |                                    | .. note::                                                                                                                                                                                             |
      |                                    |                                                                                                                                                                                                       |
      |                                    |    Set this parameter based on the site requirements. For example, if a CDM job instance is used, data cannot be supplemented at the same time. The value of this parameter can only be set to **1**. |
      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Downstream Job Requiring PatchData | Select the downstream jobs (jobs that depend on the current job) that require PatchData. You can select multiple jobs.                                                                                |
      +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The system starts to perform PatchData and the **PatchData Monitoring** page is displayed.

.. _dataartsstudio_01_0508__en-us_topic_0159100548_section12186114111347:

Batch Job Monitoring: Adding a Job Label
----------------------------------------

Labels can be added to jobs to facilitate job instance filtering.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 7** DataArts Factory

      **Figure 7** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. Click the **Batch Job Monitoring** tab.

#. In the **Operation** column of the job, choose **More** > **Add Job Label**.

#. In the **Add Job Label** dialog box displayed, set the job label parameters.


   .. figure:: /_static/images/en-us_image_0000001322408364.png
      :alt: **Figure 8** Parameters for adding a job label

      **Figure 8** Parameters for adding a job label

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001322248388.png
.. |image2| image:: /_static/images/en-us_image_0000001322248388.png
