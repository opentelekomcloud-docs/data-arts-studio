:original_name: dataartsstudio_01_0463.html

.. _dataartsstudio_01_0463:

Delete OBS
==========

Constraints
-----------

This function depends on OBS.

Functions
---------

The Delete OBS node is used to delete a bucket or directory on OBS.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0463__en-us_topic_0102588985_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0463__en-us_topic_0102588985_table58040457102411>` describe the parameters of the Delete OBS node.

.. _dataartsstudio_01_0463__en-us_topic_0102588985_table3764823994826:

.. table:: **Table 1** Parameters of Delete OBS nodes

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================================================+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS Path              | Yes                   | Path to the OBS bucket or directory.                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                               |
   |                       |                       | .. note::                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                               |
   |                       |                       |    If you delete an OBS bucket or directory, files stored in it are also deleted and cannot be restored. Before you delete a bucket or directory, back up the files stored in it if they need to be retained. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0463__en-us_topic_0102588985_table58040457102411:

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
