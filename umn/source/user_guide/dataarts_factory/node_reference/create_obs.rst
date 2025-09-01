:original_name: dataartsstudio_01_0462.html

.. _dataartsstudio_01_0462:

Create OBS
==========

.. note::

   The OBS path cannot be a log path starting with **s3a://**.

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

   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                      | Mandatory             | Description                                                                                                                                                                                                                                                  |
   +================================================================+=======================+==============================================================================================================================================================================================================================================================+
   | Max. Node Execution Duration                                   | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will be executed again.                                                                                              |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure                                             | Yes                   | Whether to re-execute a node if it fails to be executed. Possible values:                                                                                                                                                                                    |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       | -  **Yes**: The node will be re-executed, and the following parameters must be configured:                                                                                                                                                                   |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       |    -  **Retry upon Timeout**                                                                                                                                                                                                                                 |
   |                                                                |                       |    -  **Maximum Retries**                                                                                                                                                                                                                                    |
   |                                                                |                       |    -  **Retry Interval (seconds)**                                                                                                                                                                                                                           |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       | -  **No**: The node will not be re-executed. This is the default setting.                                                                                                                                                                                    |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       |    .. note::                                                                                                                                                                                                                                                 |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       |       If retry is configured for a job node and the timeout duration is configured, the system allows you to retry a node when the node execution times out.                                                                                                 |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       |       If a node is not re-executed when it fails upon timeout, you can go to the **Default Configuration** page to modify this policy.                                                                                                                       |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       |       **Retry upon Timeout** is displayed only when **Retry upon Failure** is set to **Yes**.                                                                                                                                                                |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Policy for Handling Subsequent Nodes If the Current Node Fails | Yes                   | Operation that will be performed if the node fails to be executed. Possible values:                                                                                                                                                                          |
   |                                                                |                       |                                                                                                                                                                                                                                                              |
   |                                                                |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                                                                                               |
   |                                                                |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                                                                                             |
   |                                                                |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                                                                                               |
   |                                                                |                       | -  **Suspend the current job execution plan**: If the current job instance is in abnormal state, the subsequent nodes of this node and the subsequent job instances that depend on the current job are in waiting state.                                     |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Enable Dry Run                                                 | No                    | If you select this option, the node will not be executed, and a success message will be returned.                                                                                                                                                            |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Task Groups                                                    | No                    | Select a task group. If you select a task group, you can control the maximum number of concurrent nodes in the task group in a fine-grained manner in scenarios where a job contains multiple nodes, a data patching task is ongoing, or a job is rerunning. |
   +----------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
