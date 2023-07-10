:original_name: dataartsstudio_01_0462.html

.. _dataartsstudio_01_0462:

Create OBS
==========

Constraints
-----------

This function depends on OBS.

Functions
---------

The Create OBS node is used to create buckets and directories on OBS.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0462__en-us_topic_0102588984_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0462__en-us_topic_0102588984_table58040457102411>` describe the parameters of the Create OBS node.

.. _dataartsstudio_01_0462__en-us_topic_0102588984_table3764823994826:

.. table:: **Table 1** Parameters of Create OBS nodes

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS Path              | Yes                   | Path to the OBS bucket or directory.                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  To create a bucket, enter **//**\ *OBS bucket name*. The OBS bucket name must be unique                                                                                              |
   |                       |                       | -  To create an OBS directory, select the path to the OBS directory to be created, and enter the /*Directory name* following the path. The directory name must be unique.               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0462__en-us_topic_0102588984_table58040457102411:

.. table:: **Table 2** Advanced parameters

   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory             | Description                                                                                                                                                                                 |
   +==============================+=======================+=============================================================================================================================================================================================+
   | Max. Node Execution Duration | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will not be retried and is set to the failed state. |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure           | Yes                   | Indicates whether to re-execute a node task if its execution fails. Possible values:                                                                                                        |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **Yes**: The node task will be re-executed, and the following parameters must be configured:                                                                                             |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       |    -  **Maximum Retries**                                                                                                                                                                   |
   |                              |                       |    -  **Retry Interval (seconds)**                                                                                                                                                          |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **No**: The node task will not be re-executed. This is the default setting.                                                                                                              |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | .. note::                                                                                                                                                                                   |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       |    If **Timeout Interval** is configured for the node, the node will not be executed again after the execution times out. Instead, the node is set to the failure state.                    |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Policy               | Yes                   | Operation that will be performed if the node task fails to be executed. Possible values:                                                                                                    |
   |                              |                       |                                                                                                                                                                                             |
   |                              |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                            |
   |                              |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                              |
   |                              |                       | -  **Suspend current job execution plan**: suspends running the current job. The job instance status is **Waiting**.                                                                        |
   |                              |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                              |
   +------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
