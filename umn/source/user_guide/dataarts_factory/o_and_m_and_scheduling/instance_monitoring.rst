:original_name: dataartsstudio_01_0511.html

.. _dataartsstudio_01_0511:

Instance Monitoring
===================

Each time a job is executed, a job instance record is generated. In the navigation pane of the DataArts Factory console, choose **Monitoring**. On the Monitor Instance page, you can view the job instance information and perform more operations on instances as required.

You can search for instances by **Job Name**, **Created By**, **Owner**, **CDM Job**, **Node Type**, and **Job Tag**. Search by CDM job is to search for job instances by node.

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
      | Filtering jobs by **CDM Job** or **Node Type**                   | N/A                                                                                                                                                                                                                                          |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Stop                                                             | Stop an instance that is in the **Waiting**, **Running**, or **Abnormal** state.                                                                                                                                                             |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun                                                            | Rerun a subjob instance that is in the **Succeed** or **Canceled** state.                                                                                                                                                                    |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | For details, see :ref:`Rerunning Job Instances <dataartsstudio_01_0511__en-us_topic_0118654558_section2112927164718>`.                                                                                                                       |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  | .. note::                                                                                                                                                                                                                                    |
      |                                                                  |                                                                                                                                                                                                                                              |
      |                                                                  |    Manually scheduled jobs cannot be rerun.                                                                                                                                                                                                  |
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
      | More > View                                                      | Go to the job development page and view job information.                                                                                                                                                                                     |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > History performance                                       | You can view the historical performance of a job instance.                                                                                                                                                                                   |
      +------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DAG                                                              | Display the DAG so that you can view the dependency between instances and perform O&M operations on the DAG.                                                                                                                                 |
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

You can rerun a job instance that is successfully executed or fails to be executed by setting its rerun position.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. In the **Operation** column of a job, click **Rerun** to rerun the job instance. Alternatively, click the check box on the left of a job, and then click the **Rerun** button to rerun the job instance.


   .. figure:: /_static/images/en-us_image_0000002270846746.png
      :alt: **Figure 1** Setting the job rerunning

      **Figure 1** Setting the job rerunning

   .. table:: **Table 3** Parameters for rerunning a job

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================+
      | Rerun Type                        | Type of the instance that you want to rerun.                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | -  Rerun selected instance                                                                                                                                                                                                  |
      |                                   | -  Rerun instances of selected job and its upstream and downstream jobs                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start Time                        | Time range in which instances have been run                                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | List of Rerun Job Instances       | Upstream and downstream jobs to rerun. You can select multiple jobs at a time.                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | The job dependency graph is displayed. For details about how to perform operations on the job dependency graph, see :ref:`Batch Processing: Viewing a Job Dependency Graph <dataartsstudio_01_0508__section1913992715419>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun From                        | Start position from which the job instance reruns.                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | -  **Error node**: When a job instance fails to be run, it reruns since the error node of the job instance.                                                                                                                 |
      |                                   | -  **The first node**: When a job instance fails to be run, it reruns since the first node of the job instance.                                                                                                             |
      |                                   | -  **Specified node**: When a job instance fails to run, it reruns since the node specified in the job instance. This option is available only if **Rerun Type** is set to **Rerun selected instance**.                     |
      |                                   |                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                             |
      |                                   |    A job instance reruns from its first node if either of the following cases occurs:                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                             |
      |                                   |    -  The quantity or name of a node in the job changes.                                                                                                                                                                    |
      |                                   |    -  The job instance has been successfully run.                                                                                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameters to Use                 | -  Parameters of the original job                                                                                                                                                                                           |
      |                                   | -  Parameters of the latest job                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Concurrent Instances              | Number of job instances that can be concurrently processed.                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Ignore OBS Listening              | -  **Yes**: The system does not listen to the OBS path when rerunning the job instance.                                                                                                                                     |
      |                                   | -  **No**: The system listens to the OBS path when rerunning the job instance.                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0511__section105331346184319:

Viewing the DAG
---------------

You can view the dependency between instances and perform O&M operations on the DAG.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. Locate the row that contains a job and click **DAG** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002270846750.png
      :alt: **Figure 2** DAG

      **Figure 2** DAG

   By default, the DAG displays the current job instance and its upstream and downstream job instances. It supports the following operations:

   -  Click |image2| in the upper right corner of the DAG to restore the DAG to the initial state, and click |image3| to close the DAG. Drag |image4| in the upper left corner of the DAG to change its width.

   -  Click a job instance to select it.


      .. figure:: /_static/images/en-us_image_0000002270846754.png
         :alt: **Figure 3** Selecting a job instance

         **Figure 3** Selecting a job instance

      -  When a job instance is selected, the background colors of the job instance and its upstream and downstream instances are darkened.
      -  Brief information about the instance is displayed in the lower right corner of the DAG. The instance name and ID can be directly copied.
      -  Click **Show Details** to open the details panel, which displays information such as the instance attributes, job parameters, node list, and historical instances. You can adjust the height of the panel or close it.
      -  Click the blank area to deselect the job instance.

   -  Right-click a job instance to expand its upstream and downstream job instances. You can stop, rerun, continue to execute instances, forcibly make instances succeed, analyze the upstream node, and edit the job.


      .. figure:: /_static/images/en-us_image_0000002305406625.png
         :alt: **Figure 4** Performing operations on job instances

         **Figure 4** Performing operations on job instances

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
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Forcibly successful               | A job instance in failed or canceled state is made successful.                                                                                                                                                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure ignored                   | As shown in the following figure, a failure handling policy is configured to skip node B and continue to execute node C if node B fails. When the job is executed successfully, the job instance is in **Failure ignored** state.                                        |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. _dataartsstudio_01_0511__fig236915517534:                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. figure:: /_static/images/en-us_image_0000002305406641.png                                                                                                                                                                                                             |
   |                                   |    :alt: **Figure 5** Failure handling policy - Go to the next node                                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   |    **Figure 5** Failure handling policy - Go to the next node                                                                                                                                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Abnormal                          | There are few scenarios where this status is displayed. As shown in the following figure, a failure handling policy is configured to suspend the job instance immediately without continuing to execute node C. In this case, the job instance is in **Abnormal** state. |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. _dataartsstudio_01_0511__fig821712369536:                                                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   | .. figure:: /_static/images/en-us_image_0000002305406629.png                                                                                                                                                                                                             |
   |                                   |    :alt: **Figure 6** Failure handling policy - Suspend current job execution plan                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                          |
   |                                   |    **Figure 6** Failure handling policy - Suspend current job execution plan                                                                                                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Paused                            | There are few scenarios where this status is displayed. When a running job instance is suspended by the test personnel, the instance is in **Paused** state.                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Canceled                          | -  If you manually stop a job instance in **Waiting** state, the job instance status becomes **Canceled**.                                                                                                                                                               |
   |                                   | -  If you stop scheduling the upstream job on which a job instance depends, the job instance status becomes **Canceled**. For example, job A depends on job B. If you stop scheduling job B, the instance generated for job A is automatically canceled.                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Frozen                            | If a job instance is expected to be generated in the future, the job instance is in frozen state after being frozen.                                                                                                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failed                            | A job fails to be executed.                                                                                                                                                                                                                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002270789884.png
.. |image2| image:: /_static/images/en-us_image_0000002305406621.png
.. |image3| image:: /_static/images/en-us_image_0000002305406633.png
.. |image4| image:: /_static/images/en-us_image_0000002270846758.png
