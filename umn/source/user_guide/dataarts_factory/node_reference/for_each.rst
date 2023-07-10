:original_name: dataartsstudio_01_0535.html

.. _dataartsstudio_01_0535:

For Each
========

Functions
---------

The For Each node specifies a subjob to be executed cyclically and assigns values to variables in a subjob with a dataset.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0535__en-us_topic_0226360828_table3764823994826>` describes the parameters of the For Each node.

.. _dataartsstudio_01_0535__en-us_topic_0226360828_table3764823994826:

.. table:: **Table 1** Parameters of the For Each node

   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory             | Description                                                                                                                                                                                                                                                             |
   +=============================+=======================+=========================================================================================================================================================================================================================================================================+
   | Node Name                   | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                                                                 |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subjob in a Loop            | Yes                   | Name of the subjob to be executed cyclically.                                                                                                                                                                                                                           |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dataset                     | Yes                   | The For Each node needs to define a dataset. The dataset is used to cyclically replace variables in a subjob. A row of data in the dataset corresponds to a subjob instance. The dataset may come from the following sources:                                           |
   |                             |                       |                                                                                                                                                                                                                                                                         |
   |                             |                       | -  Output from upstream nodes, such as the select statements of the Hive SQL, DLI SQL, or Spark SQL node, and echo of the shell node. The EL expression **#{Job.getNodeOutput('preNodeName')}** is used, which means the output of the previous node.                   |
   |                             |                       | -  A specified array, for example, [['001'],['002'],['003']]                                                                                                                                                                                                            |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Concurrent Subjobs          | Yes                   | Subjobs generated cyclically can be executed concurrently. You can set the number of concurrent subjobs.                                                                                                                                                                |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subjob Instance Name Suffix | No                    | Name of the subjob generated by For Each: For Each node name + underscore (_) + suffix.                                                                                                                                                                                 |
   |                             |                       |                                                                                                                                                                                                                                                                         |
   |                             |                       | The suffix is configurable. If the suffix is not configured, the suffix increases in ascending order based on the number.                                                                                                                                               |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Job Running Parameter       | No                    | This parameter is available only when you set job parameters for a subjob.                                                                                                                                                                                              |
   |                             |                       |                                                                                                                                                                                                                                                                         |
   |                             |                       | -  If the subjob parameters are left unspecified, the subjob is executed with its own parameter variables.                                                                                                                                                              |
   |                             |                       | -  If the subjob parameters are specified, the subjob is executed with the configured parameter values. The method or EL expression configured for the subjob parameter in the node attribute is read and replaced based on the environment variable of the parent job. |
   +-----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
