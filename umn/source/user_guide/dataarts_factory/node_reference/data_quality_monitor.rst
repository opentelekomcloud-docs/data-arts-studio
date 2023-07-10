:original_name: dataartsstudio_01_0472.html

.. _dataartsstudio_01_0472:

Data Quality Monitor
====================

Functions
---------

The Data Quality Monitor node is used to monitor the quality of running data.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0472__en-us_topic_0163991448_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0472__en-us_topic_0163991448_table47796360238>` describe the parameters of the Data Quality Monitor node.

.. _dataartsstudio_01_0472__en-us_topic_0163991448_table3764823994826:

.. table:: **Table 1** Parameters of Data Quality Monitor nodes

   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory             | Description                                                                                                                                                                             |
   +=============================+=======================+=========================================================================================================================================================================================+
   | Node Name                   | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Job Type                    | Yes                   | Data quality job. The following options are available:                                                                                                                                  |
   |                             |                       |                                                                                                                                                                                         |
   |                             |                       | -  Quality job                                                                                                                                                                          |
   |                             |                       | -  Comparison job                                                                                                                                                                       |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Quality Job Name            | Yes                   | Name of a quality job created in DataArts Quality. This parameter is mandatory when **Job Type** is **Quality Job**.                                                                    |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ignore Quality Job Alarm    | Yes                   | This parameter is mandatory when **Job Type** is **Quality Job**.                                                                                                                       |
   |                             |                       |                                                                                                                                                                                         |
   |                             |                       | -  **Yes**: If the quality job is in the alarm state, the status of the current node is set to successful and the subsequent nodes continue to be executed.                             |
   |                             |                       | -  **No**: If the quality job is in the alarm state, the status of the current node is set to failed.                                                                                   |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Comparison Job Name         | Yes                   | Name of a comparison job created in DataArts Quality. This parameter is mandatory when **Job Type** is **Comparison Job**.                                                              |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ignore Comparison Job Alarm | Yes                   | This parameter is mandatory when **Job Type** is **Comparison Job**.                                                                                                                    |
   |                             |                       |                                                                                                                                                                                         |
   |                             |                       | -  **Yes**: If the comparison job is in the alarm state, the status of the current node is set to successful and the subsequent nodes continue to be executed.                          |
   |                             |                       | -  **No**: If the comparison job is in the alarm state, the status of the current node is set to failed.                                                                                |
   +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0472__en-us_topic_0163991448_table47796360238:

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
