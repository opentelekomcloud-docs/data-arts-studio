:original_name: dataartsstudio_01_0511.html

.. _dataartsstudio_01_0511:

Instance Monitoring
===================

Each time a job is executed, a job instance record is generated. In the navigation pane of the DataArts Factory console, choose **Monitoring**. On the Monitor Instance page, you can view the job instance information and perform more operations on instances as required.

You can search for instances by **Job Name**, **Created By**, **Owner**, **CDM Job**, **Node Type**, and **Job Tag**. Search by CDM job is to search for job instances by node. In addition, you can filter job instances by status or scheduling mode.

Performing Job Instance Operations
----------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. You can stop, rerun, or continue to execute instances or make instances succeed. For details, see :ref:`Table 1 <dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576>`.

   When multiple instances are rerun in batches, the sequence is as follows:

   -  If a job does not depend on the previous schedule cycle, multiple instances run concurrently.
   -  If jobs are dependent on their own, multiple instances are executed in serial mode. The instance that first finishes running in the previous schedule cycle is the first one to rerun.

#. :ref:`Table 1 <dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576>` describes the operations that can be performed on the instance.

   .. _dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576:

   .. table:: **Table 1** Instance monitoring operations

      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                                                        | Description                                                                                                                                                                                                                                  |
      +==================================================================+==============================================================================================================================================================================================================================================+
      | Searching for jobs by **Job Name**, **Created By**, or **Owner** | If you select **Exact search**, exact search by job name is supported.                                                                                                                                                                       |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | If you do not select **Exact search**, fuzzy search by job name is supported.                                                                                                                                                                |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filtering jobs by **CDM Job**, **Job Tag**, or **Node Type**     | N/A                                                                                                                                                                                                                                          |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Stop                                                             | Stop an instance that is in the **Waiting**, **Running**, or **Abnormal** state.                                                                                                                                                             |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun                                                            | Rerun a subjob instance that is in the **Succeed** or **Canceled** state.                                                                                                                                                                    |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | For details, see :ref:`Rerunning Job Instances <dataartsstudio_01_0511__en-us_topic_0118654558_section2112927164718>`.                                                                                                                       |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | .. note::                                                                                                                                                                                                                                    |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  |    -  Manually scheduled jobs cannot be rerun.                                                                                                                                                                                               |
      |                                                                  |    -  In enterprise mode, developers cannot rerun job instances.                                                                                                                                                                             |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | If instances need manual confirmation before they are executed, they are in waiting confirmation state when they are being rerun. When you click **Execute**, the instances are in waiting execution state.                                  |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Manual Retry                                                     | Retry abnormal instances.                                                                                                                                                                                                                    |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Continue                                                         | Continue to run subsequent nodes in instances which are in abnormal state.                                                                                                                                                                   |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Succeed                                                          | Change the statuses of instances in **Abnormal**, **Canceled**, or **Failed** state to **Forcibly successful**.                                                                                                                              |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Execution                                                | Confirm executing instances in pending confirmation state.                                                                                                                                                                                   |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execute Job Without Dependency                                   | Select job instances that have dependency relationships and execute them.                                                                                                                                                                    |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Manual Retry                                              | Retry abnormal instances.                                                                                                                                                                                                                    |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > View Waiting Job Instance                                 | When the instance is in the waiting state, you can view the waiting job instance. Click **Remove Dependency** in the **Operation** column to remove dependency on an upstream instance.                                                      |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Confirm Execution                                         | Confirm executing instances in pending confirmation state.                                                                                                                                                                                   |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Continue                                                  | If an instance is in the **Abnormal** state, you can click **Continue** to begin running the subsequent nodes in the instance.                                                                                                               |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | .. note::                                                                                                                                                                                                                                    |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Succeed                                                   | Forcibly change the status of an instance from **Abnormal**, **Canceled**, or **Failed** to **Succeed**.                                                                                                                                     |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Execute Job Without Dependency                            | Execute job instances that have dependency relationships.                                                                                                                                                                                    |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > View                                                      | Go to the job development page and view job information.                                                                                                                                                                                     |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > History performance                                       | You can view the historical performance of a job instance.                                                                                                                                                                                   |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > View Rerun History                                        | You can view the job instance rerun records.                                                                                                                                                                                                 |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | This is possible only if the job instance has rerun at least once.                                                                                                                                                                           |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Execute Preferentially                                    | Preferentially execute job instances.                                                                                                                                                                                                        |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DAG                                                              | Display the DAG so that you can view the dependency between job instances and perform O&M operations on the DAG.                                                                                                                             |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | For details, see :ref:`Viewing the DAG <dataartsstudio_01_0511__section105331346184319>`.                                                                                                                                                    |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Export All Data                                                  | Click **Export All Data**. In the displayed **Export All Data** dialog box, click **OK**. After the export is complete, go to the **Download Center** page to view the exported data.                                                        |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | If the default storage path is not configured, you can set a storage path and select **Set as default OBS path** in the **Export to OBS** dialog box.                                                                                        |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | A maximum of 30 MB data can be exported. If there are more than 30 MB data, the data will be automatically truncated.                                                                                                                        |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | The exported job instances map job nodes. You cannot export data by selecting job names. Instead, you can select the data to be exported by setting filter criteria.                                                                         |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click |image1| in front of an instance. The running records of all nodes in the instance are displayed.

#. :ref:`Table 2 <dataartsstudio_01_0511__en-us_topic_0159100548_table181913016117>` describes the operations that can be performed on the node.

   .. _dataartsstudio_01_0511__en-us_topic_0159100548_table181913016117:

   .. table:: **Table 2** Operations (node)

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================+
      | View Log                          | View the log information of a node.                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | You can control access to the test run logs. For example, after user A performs a test, user A can view the test run logs on the **Monitor Instance** page, but user B cannot.                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Manual Retry                      | Retry a failed node.                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | Retry an abnormal node.                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Succeed                           | Change the status of a node from **Failed** to **Succeed**.                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Skip                       | To skip a node that is to be run or that has been paused, click **Skip**.                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    Instance with only one node cannot be skipped. Only instances with multiple nodes can be skipped.                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Pause                      | When a job instance is in running state and a node is in waiting execution state, you can pause the node. Subsequent nodes will be blocked.                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Resume                     | To resume a paused node, click **Resume**.                                                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > History performance        | You can view the historical performance of a job node.                                                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0511__en-us_topic_0118654558_section2112927164718:

Rerunning Job Instances
-----------------------

.. note::

   In enterprise mode, developers cannot rerun job instances.

You can rerun a job instance that is successfully executed or fails to be executed by setting its rerun position.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. Locate a job and click **Rerun** in the **Operation** column to rerun a job instance. Alternatively, select the check boxes to the left of job names and click **Rerun** above the job list to rerun multiple job instances.


   .. figure:: /_static/images/en-us_image_0000002234239808.png
      :alt: **Figure 1** Rerunning a job instance

      **Figure 1** Rerunning a job instance


   .. figure:: /_static/images/en-us_image_0000002234079932.png
      :alt: **Figure 2** Rerunning job instances

      **Figure 2** Rerunning job instances

   .. note::

      When rerunning multiple job instances, you only need to set **Rerun From**, **Parameters to Use**, and **Ignore OBS Listening**.

   .. table:: **Table 3** Parameters for rerunning a job

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Rerun Type                        | Type of the instance that you want to rerun.                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  Rerun selected instance                                                                                                                                                                              |
      |                                   | -  Rerun instances of selected job and its upstream and downstream jobs                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start Time                        | This parameter is required only when **Rerun Type** is set to **Rerun instances of selected job and its upstream and downstream jobs**.                                                                 |
      |                                   |                                                                                                                                                                                                         |
      |                                   | After you set the start time and end time, the system will rerun all the job instances in the specified period.                                                                                         |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    If no job instance can be rerun in the specified period, error message "Job xxx have no instances to rerun" will be displayed.                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | List of Rerun Job Instances       | This parameter is required only when **Rerun Type** is set to **Rerun instances of selected job and its upstream and downstream jobs**.                                                                 |
      |                                   |                                                                                                                                                                                                         |
      |                                   | You can select **Display the current job and its directly connected jobs** or **Display complete dependency graphs** in the **Scheduling-State Job Dependency View** dialog box.                        |
      |                                   |                                                                                                                                                                                                         |
      |                                   | The job dependency view is displayed. You can enter a job name to query the job dependency.                                                                                                             |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. _dataartsstudio_01_0511__fig4165165110213:                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. figure:: /_static/images/en-us_image_0000002234079996.png                                                                                                                                            |
      |                                   |    :alt: **Figure 3** Job Dependency page                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    **Figure 3** Job Dependency page                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                         |
      |                                   | Select the job to rerun and its upstream and downstream jobs. You can select multiple jobs at a time.                                                                                                   |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    If you hover over the question mark on the right of **Scheduling-State Job Dependency View**, the following information is displayed:                                                                |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  When you hover your cursor on a job, its upstream and downstream jobs will be marked blue and yellow, respectively.                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  Drag the blank area to view the complete relationship graph.                                                                                                                                      |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  Click a job in the relationship graph to select all the instances within the duration of the job.                                                                                                 |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       .. _dataartsstudio_01_0511__fig19631512831:                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       **Figure 4** Rerunning all instances                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  Right-click the job to view its instances, and select and run them again.                                                                                                                         |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       .. _dataartsstudio_01_0511__fig162926351338:                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       .. figure:: /_static/images/en-us_image_0000002269199241.png                                                                                                                                      |
      |                                   |          :alt: **Figure 5** Rerunning some instances                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                         |
      |                                   |          **Figure 5** Rerunning some instances                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  If no job instance is selected, **No instance selected** is displayed.                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       .. _dataartsstudio_01_0511__fig179241150532:                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       .. figure:: /_static/images/en-us_image_0000002269119177.png                                                                                                                                      |
      |                                   |          :alt: **Figure 6** No instance selected                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                         |
      |                                   |          **Figure 6** No instance selected                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                         |
      |                                   | For detailed operations on the job dependency graph, see :ref:`Batch Job Monitoring: Viewing a Job Dependency Graph <dataartsstudio_01_0508__section1913992715419>`.                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun From                        | Start position from which the job instance reruns.                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Error node**: When a job instance fails to be run, it reruns since the error node of the job instance.                                                                                             |
      |                                   | -  **The first node**: When a job instance fails to be run, it reruns since the first node of the job instance.                                                                                         |
      |                                   | -  **Specified node**: When a job instance fails to run, it reruns since the node specified in the job instance. This option is available only if **Rerun Type** is set to **Rerun selected instance**. |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    A job instance reruns from its first node if either of the following cases occurs:                                                                                                                   |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    -  The quantity or name of a node in the job changes.                                                                                                                                                |
      |                                   |    -  The job instance has been successfully run.                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameters to Use                 | -  Parameters of the original job                                                                                                                                                                       |
      |                                   | -  Parameters of the latest job                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Concurrent Instances              | This parameter is required only when **Rerun Type** is set to **Rerun instances of selected job and its upstream and downstream jobs**.                                                                 |
      |                                   |                                                                                                                                                                                                         |
      |                                   | It indicates the number of job instances that can be concurrently processed. The value cannot be less than 1. The default value is **1**.                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Ignore OBS Listening              | The default value is **Yes**.                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Yes**: The system does not listen to the OBS path when rerunning the job instance.                                                                                                                 |
      |                                   | -  **No**: The system listens to the OBS path when rerunning the job instance.                                                                                                                          |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    .. note::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       If this parameter is not used, ignore it.                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0511__section105331346184319:

Viewing the DAG
---------------

You can view the dependency between job instances and perform O&M operations on the DAG.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. Locate the row that contains a job and click **DAG** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002234079976.png
      :alt: **Figure 7** DAG

      **Figure 7** DAG

   By default, the DAG displays the current job instance and its upstream and downstream job instances. It supports the following operations:

   -  Click |image2| in the upper right corner of the DAG to restore the DAG to the initial state, and click |image3| to close the DAG. Drag |image4| in the upper left corner of the DAG to change its width.

   -  Click a job instance to select it.


      .. figure:: /_static/images/en-us_image_0000002234080000.png
         :alt: **Figure 8** Selecting a job instance

         **Figure 8** Selecting a job instance

      -  When a job instance is selected, the background colors of the job instance and its upstream and downstream instances are darkened.
      -  Brief information about the instance is displayed in the lower right corner of the DAG. The instance name and ID can be directly copied.
      -  Click **Show Details** to open the details panel, which displays information such as the instance attributes, job parameters, node list, and historical instances. You can adjust the height of the panel or close it.
      -  Click the blank area to deselect the job instance.

   -  Right-click a job instance to expand its upstream and downstream job instances. You can stop, rerun, continue to execute instances, forcibly make instances succeed, analyze the upstream node, and edit the job.


      .. figure:: /_static/images/en-us_image_0000002234239816.png
         :alt: **Figure 9** Performing operations on job instances

         **Figure 9** Performing operations on job instances

Job Instance Statuses
---------------------

.. table:: **Table 4** Job instance statuses

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Status                            | Description                                                                                                                                                                                                                                                              |
   +===================================+==========================================================================================================================================================================================================================================================================+
   | Waiting                           | A job instance is in waiting state if the execution of its dependent job instances is not complete, for example, no instance has been generated, instances are waiting to be executed, or instances fail to be executed.                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Running                           | A job is running. All of its dependent jobs have been executed successfully.                                                                                                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Successful                        | The service logic of a job is successfully executed (including the success of retry upon failure).                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | Successful execution statuses include **Successful**, **Forcibly successful**, and **Failure ignored**.                                                                                                                                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Forcibly successful               | A job instance in failed or canceled state is made successful.                                                                                                                                                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure ignored                   | As shown in the following figure, a failure handling policy is configured to skip node B and continue to execute node C if node B fails. When the job is executed successfully, the job instance is in **Failure ignored** state.                                        |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. _dataartsstudio_01_0511__fig236915517534:                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. figure:: /_static/images/en-us_image_0000002234239792.png                                                                                                                                                                                                             |
   |                                   |    :alt: **Figure 10** Failure handling policy - Go to the next node                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   |    **Figure 10** Failure handling policy - Go to the next node                                                                                                                                                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Abnormal                          | There are few scenarios where this status is displayed. As shown in the following figure, a failure handling policy is configured to suspend the job instance immediately without continuing to execute node C. In this case, the job instance is in **Abnormal** state. |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. _dataartsstudio_01_0511__fig821712369536:                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. figure:: /_static/images/en-us_image_0000002269119161.png                                                                                                                                                                                                             |
   |                                   |    :alt: **Figure 11** Failure handling policy - Suspend current job execution plan                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   |    **Figure 11** Failure handling policy - Suspend current job execution plan                                                                                                                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Paused                            | There are few scenarios where this status is displayed. When a running job instance is suspended by the test personnel, the instance is in **Paused** state.                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Canceled                          | -  If you manually stop a job instance in **Waiting** state, the job instance status becomes **Canceled**.                                                                                                                                                               |
   |                                   | -  If you stop scheduling the upstream job on which a job instance depends, the job instance status becomes **Canceled**. For example, job A depends on job B. If you stop scheduling job B, the instance generated for job A is automatically canceled.                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Frozen                            | If a job instance is expected to be generated in the future, the job instance is in frozen state after being frozen.                                                                                                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failed                            | A job fails to be executed. If a job fails to be executed, you can view the failure cause, for example, a node of the job fails to be executed.                                                                                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002234239844.png
.. |image2| image:: /_static/images/en-us_image_0000002269119133.png
.. |image3| image:: /_static/images/en-us_image_0000002234079984.png
.. |image4| image:: /_static/images/en-us_image_0000002234080008.png
