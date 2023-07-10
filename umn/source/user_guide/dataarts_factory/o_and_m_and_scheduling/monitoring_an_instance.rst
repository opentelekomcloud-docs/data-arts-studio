:original_name: dataartsstudio_01_0511.html

.. _dataartsstudio_01_0511:

Monitoring an Instance
======================

Each time a job is executed, a job instance record is generated. In the navigation pane of the DataArts Factory console, choose **Monitoring**. On the Monitor Instance page, you can view the job instance information and perform more operations on instances as required.

You can search for instances by **Job Name**, **Created By**, **CDM Job**, and **Node Type**. Search by CDM job is to search for job instances by node.

Performing Job Instance Operations
----------------------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the navigation tree on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. You can stop, rerun, continue to run, or forcibly run jobs in batches. For details, see :ref:`Table 1 <dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576>`.

   When multiple instances are rerun in batches, the sequence is as follows:

   -  If a job does not depend on the previous schedule cycle, multiple instances run concurrently.
   -  If jobs are dependent on their own, multiple instances are executed in serial mode. The instance that first finishes running in the previous schedule cycle is the first one to rerun.

#. :ref:`Table 1 <dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576>` describes the operations that can be performed on the instance.

   .. _dataartsstudio_01_0511__en-us_topic_0159100548_table958254318576:

   .. table:: **Table 1** Instance monitoring operations

      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                                            | Description                                                                                                                                                                                                                                  |
      +======================================================+==============================================================================================================================================================================================================================================+
      | Searching for a job based on the job name or creator | If you select **Exact search**, exact search by job name is supported.                                                                                                                                                                       |
      |                                                      |                                                                                                                                                                                                                                              |
      |                                                      | If you do not select **Exact search**, fuzzy search by job name is supported.                                                                                                                                                                |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filtering jobs by CDM job or node type               | ``-``                                                                                                                                                                                                                                        |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Stop                                                 | Stop an instance that is in the **Waiting**, **Running**, or **Abnormal** state.                                                                                                                                                             |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun                                                | Rerun a subjob instance that is in the **Succeed** or **Canceled** state.                                                                                                                                                                    |
      |                                                      |                                                                                                                                                                                                                                              |
      |                                                      | For details, see :ref:`Rerunning Job Instances <dataartsstudio_01_0511__en-us_topic_0118654558_section2112927164718>`.                                                                                                                       |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | View Waiting Job Instance                            | When the instance is in the waiting state, you can view the waiting job instance.                                                                                                                                                            |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Continue                                      | If an instance is in the **Abnormal** state, you can click **Continue** to begin running the subsequent nodes in the instance.                                                                                                               |
      |                                                      |                                                                                                                                                                                                                                              |
      |                                                      | .. note::                                                                                                                                                                                                                                    |
      |                                                      |                                                                                                                                                                                                                                              |
      |                                                      |    This operation can be performed only when **Failure Policy** is set to **Suspend the current job execution plan**. To view the current failure policy, click a node and then click **Advanced Settings** on the **Node Properties** page. |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > Succeed                                       | Forcibly change the status of an instance from **Abnormal**, **Canceled**, or **Failed** to **Succeed**.                                                                                                                                     |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | More > View                                          | Go to the job development page and view job information.                                                                                                                                                                                     |
      +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click |image1| in front of an instance. The running records of all nodes in the instance are displayed.

#. :ref:`Table 2 <dataartsstudio_01_0511__en-us_topic_0159100548_table181913016117>` describes the actions that can be performed on the node.

   .. _dataartsstudio_01_0511__en-us_topic_0159100548_table181913016117:

   .. table:: **Table 2** Operations (node)

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

.. _dataartsstudio_01_0511__en-us_topic_0118654558_section2112927164718:

Rerunning Job Instances
-----------------------

You can rerun a job instance that is successfully executed or fails to be executed by setting its rerun position.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the navigation tree on the left of the DataArts Factory page, choose **Monitoring** > **Monitor Instance**

#. In the **Operation** column of a job, click **Rerun** to rerun the job instance. Alternatively, click the check box on the left of a job, and then click the **Rerun** button to rerun the job instance.


   .. figure:: /_static/images/en-us_image_0000001322088524.png
      :alt: **Figure 3** Setting the rerunning position

      **Figure 3** Setting the rerunning position

   .. table:: **Table 3** Parameters for rerunning a job

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Rerun Type                        | Type of the instance that you want to rerun.                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  Rerun selected instance                                                                                                                                                                              |
      |                                   | -  Rerun instances of selected job and its upstream and downstream jobs                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start Time                        | Time range in which instances have been run                                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | List of Rerun Job Instances       | Upstream and downstream jobs to rerun. You can select multiple jobs at a time.                                                                                                                          |
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
      | Concurrent Instances              | Number of job instances that can be concurrently processed.                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001373408569.png
