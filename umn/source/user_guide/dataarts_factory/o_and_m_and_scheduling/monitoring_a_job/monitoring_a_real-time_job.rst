:original_name: dataartsstudio_01_0509.html

.. _dataartsstudio_01_0509:

Monitoring a Real-Time Job
==========================

In the real-time processing mode, data is processed in real time, which is used in scenarios with high real-time performance. This type of job is a pipeline that consists of one or more nodes. You can configure scheduling policies for each node, and the tasks started by operators can keep running for an unlimited period of time. In this type of job, lines with arrows represent only service relationships, rather than task execution processes or data flows.

You can choose **Monitor Job** and click the **Real-Time Job Monitoring** tab to view the job status, start time, and end time, and perform the operations listed in :ref:`Table 1 <dataartsstudio_01_0509__en-us_topic_0159098544_table958254318576>`.


.. figure:: /_static/images/en-us_image_0000001322408392.png
   :alt: **Figure 1** Real-time job monitoring page

   **Figure 1** Real-time job monitoring page

.. _dataartsstudio_01_0509__en-us_topic_0159098544_table958254318576:

.. table:: **Table 1** Operations supported by real-time job monitoring

   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No.                   | Operation                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                       |
   +=======================+=====================================================+===================================================================================================================================================================================================================================================================================================================================================================================================================+
   | 1                     | Searching for a job based on the job name or owner  | ``-``                                                                                                                                                                                                                                                                                                                                                                                                             |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2                     | Filtering jobs based on the job status or job label | ``-``                                                                                                                                                                                                                                                                                                                                                                                                             |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3                     | Perform operations on jobs in a batch               | Select multiple jobs and perform operations on them.                                                                                                                                                                                                                                                                                                                                                              |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4                     | Viewing job instance status                         | Click job in front of the |image1| name. The **Last Instance** page is displayed. You can view information about the last instance of the job.                                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 5                     | Job status-related operations                       | In the **Operation** column of the job, you can start, pause, recover, and stop job scheduling.                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 6                     | Adding a job label                                  | In the **Operation** column of a job, choose **More** > **Add Job Label**.                                                                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 7                     | Viewing node information of a job                   | Click a job name. On the displayed page, click a node to view its associated job/scripts and monitoring information.                                                                                                                                                                                                                                                                                              |
   |                       |                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                                                     | .. note::                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                       |                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                                                     |    If event-driven scheduling is configured for a node in the job, the subjob monitoring page is displayed when you click the node.                                                                                                                                                                                                                                                                               |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 8                     | Disabling and restoring a node                      | Click a job name. On the displayed page, right-click a node and select **Disable**. After the node is disabled, you can right-click it and select **Restore** to restore it on another location. For details, see :ref:`Real-Time Job Monitoring: Disabling and Restoring a Node <dataartsstudio_01_0509__en-us_topic_0159097444_section1263174611499>`.                                                          |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 9                     | Viewing the boot log                                | Click a job name. On the displayed page, right-click a node and select **View Run Log** to view logs of the node.                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 10                    | Configuring scheduling                              | Click a job name. On the displayed page, right-click the node where event-driven scheduling is configured and select **Configure Scheduling** to view and modify the scheduling information about the node. For details, see :ref:`Real-Time Job Monitoring: Configuring Scheduling for a Node Where Event-driven Scheduling Is Configured <dataartsstudio_01_0509__en-us_topic_0159097444_section112906617404>`. |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 11                    | Monitoring subjobs                                  | Click a job name. On the displayed page, click the node where event-driven scheduling is configured to go to the subjob monitoring page. For details, see :ref:`Real-Time Job Monitoring: Monitoring Subjobs <dataartsstudio_01_0509__section10136113392518>`.                                                                                                                                                    |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 12                    | Clearing stream messages                            | Click a job name. On the displayed page, right-click the node where event-driven scheduling is configured and select **Clear Stream Message**.                                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0509__en-us_topic_0159097444_section1263174611499:

Real-Time Job Monitoring: Disabling and Restoring a Node
--------------------------------------------------------

You can disable a node in a real-time job and restore it in another location.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. On the **Real-Time Job Monitoring** tab page, click a job name.

#. On the displayed page, right-click the node and select **Disable**.

#. Right-click the node and choose **Resume** from the shortcut menu. The **Resume Node Running** dialog box is displayed, as shown in :ref:`Table 2 <dataartsstudio_01_0509__en-us_topic_0159097444_table3326856465>`.

   .. _dataartsstudio_01_0509__en-us_topic_0159097444_table3326856465:

   .. table:: **Table 2** Resumption parameters

      +-----------------------------------+------------------------------------------------------------------------+
      | Parameter                         | Description                                                            |
      +===================================+========================================================================+
      | Last Paused                       | Start time when a node is suspended.                                   |
      +-----------------------------------+------------------------------------------------------------------------+
      | Tasks Not Run                     | Number of tasks that are not running during node suspension.           |
      +-----------------------------------+------------------------------------------------------------------------+
      | Run From                          | Parameters for performing the tasks generated during the pause period. |
      |                                   |                                                                        |
      |                                   | Position from which running restarts.                                  |
      |                                   |                                                                        |
      |                                   | -  Paused node                                                         |
      |                                   | -  The first node of the subjob                                        |
      +-----------------------------------+------------------------------------------------------------------------+
      | Concurrent Tasks                  | Parameters for performing the tasks generated during the pause period. |
      |                                   |                                                                        |
      |                                   | Number of tasks to be processed.                                       |
      +-----------------------------------+------------------------------------------------------------------------+
      | Task Name                         | Parameters for performing the tasks generated during the pause period. |
      |                                   |                                                                        |
      |                                   | Task to be resumed.                                                    |
      +-----------------------------------+------------------------------------------------------------------------+

.. _dataartsstudio_01_0509__en-us_topic_0159097444_section112906617404:

Real-Time Job Monitoring: Configuring Scheduling for a Node Where Event-driven Scheduling Is Configured
-------------------------------------------------------------------------------------------------------

If event-driven scheduling is configured for a node in a real-time job, right-click the node on the job monitoring details page and choose **Configure Scheduling** from the shortcut menu to view and modify the scheduling information about the node.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 3** DataArts Factory

      **Figure 3** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. On the **Real-Time Job Monitoring** tab page, click a job name.

#. On the displayed page, right-click the node where event-driven scheduling is configured, select **Configure Scheduling**, and configure the parameters shown in :ref:`Table 3 <dataartsstudio_01_0509__table9417351471>`.


   .. figure:: /_static/images/en-us_image_0000001373088321.png
      :alt: **Figure 4** Configuring scheduling

      **Figure 4** Configuring scheduling

   .. _dataartsstudio_01_0509__table9417351471:

   .. table:: **Table 3** Policy parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                       |
      +===================================+===================================================================================================+
      | Concurrent Events                 | Number of jobs that can be concurrently processed. The maximum number of concurrent events is 10. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------+
      | Event Detection Interval          | Interval for event detection. The unit of the interval can be **Second** or **Minute**.           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------+
      | Failure Policy                    | Select a policy to be performed after scheduling fails.                                           |
      |                                   |                                                                                                   |
      |                                   | -  Stop scheduling                                                                                |
      |                                   | -  Ignore failure and proceed                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0509__section10136113392518:

Real-Time Job Monitoring: Monitoring Subjobs
--------------------------------------------

When event-based scheduling is configured for a node in a job, you can click this node to query monitoring information of subjobs. On the **Subjob** page, you can stop, rerun, continue, and succeed subjobs as well as view subjob events.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Monitoring** > **Monitor Job**.

#. On the **Real-Time Job Monitoring** tab page, click a job name.

#. Click a node with event-based scheduling configured,


   .. figure:: /_static/images/en-us_image_0000001321928804.png
      :alt: **Figure 6** Subjob monitoring page

      **Figure 6** Subjob monitoring page

   :ref:`Table 4 <dataartsstudio_01_0509__table7990143352515>` describes the actions listed in the **Operation** column of each subjob.

   .. _dataartsstudio_01_0509__table7990143352515:

   .. table:: **Table 4** Subjob monitoring operations

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================+
      | Stop                              | Stops a subjob instance that is in the **Running** state.                                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun                             | Reruns a subjob instance that is in the **Succeed** or **Failed** state.                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Continue                          | If a subjob instance is in the **Abnormal** state, you can click **Continue** to begin running the subsequent nodes in the subjob instance.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Forcibly Succeed                  | Forcibly changes the status of a subjob instance from **Failed** to **Succeed**.                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | View Event                        | Displays the event content of a subjob.                                                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click |image2| in the **Status** column. The running records of the subjob node are displayed.

   :ref:`Table 5 <dataartsstudio_01_0509__en-us_topic_0159098544_table181913016117>` describes the operations that can be performed on the node.

   .. _dataartsstudio_01_0509__en-us_topic_0159098544_table181913016117:

   .. table:: **Table 5** Operations (node)

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================+
      | View Log                          | View the log information of a node.                                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Manual Retry               | To run a node again after it fails, click **Retry**.                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Succeed                    | Change the status of a node from **Failed** to **Succeed**.                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                              |
      |                                   |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Skip                       | To skip a node that is to be run or that has been paused, click **Skip**.                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Pause                      | To pause a node that is to be run, click **Pause**. Nodes queued after the paused node will be blocked.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Resume                     | To resume a paused node, click **Resume**.                                                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001322408396.png
.. |image2| image:: /_static/images/en-us_image_0000001321928800.png
