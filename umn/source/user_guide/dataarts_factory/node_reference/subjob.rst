:original_name: dataartsstudio_01_0467.html

.. _dataartsstudio_01_0467:

Subjob
======

Function
--------

The Subjob node is used to call the batch job that does not contain the subjob node.

Parameter
---------

:ref:`Table 1 <dataartsstudio_01_0467__en-us_topic_0157404961_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0467__en-us_topic_0157404961_table58040457102411>` describe the parameters of the Subjob node.

.. _dataartsstudio_01_0467__en-us_topic_0157404961_table3764823994826:

.. table:: **Table 1** Parameters of subjob nodes

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================================================================================================================================================================+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                                                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subjob Name           | Yes                   | Select the name of the subjob to be called.                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                               |
   |                       |                       | .. note::                                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                               |
   |                       |                       |    You can only select the name of an existing batch job that does not contain the Subjob node.                                                                                                                                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subjob Parameter      | Yes/No                | -  If the subjob parameters are left unspecified, the subjob is executed with its own parameter variables. The **Subjob Parameter Name** of the parent job is not displayed.                                                                                                                                                  |
   |                       |                       | -  If the subjob parameters are specified, the subjob is executed with the configured parameter values. In this case, the **Subjob Parameter Name** of the parent job is displayed, and the data or EL expression configured for the subjob is accessed and replaced according to the environment variable of the parent job. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0467__en-us_topic_0157404961_table58040457102411:

.. table:: **Table 2** Advanced parameters

   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                        | Mandatory             | Description                                                                                                                                                                                 |
   +==================================+=======================+=============================================================================================================================================================================================+
   | Node Status Polling Interval (s) | Yes                   | Specifies how often the system check completeness of the node task. The value ranges from 1 to 60 seconds.                                                                                  |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. Node Execution Duration     | Yes                   | Execution timeout interval for the node. If retry is configured and the execution is not complete within the timeout interval, the node will not be retried and is set to the failed state. |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Retry upon Failure               | Yes                   | Indicates whether to re-execute a node task if its execution fails. Possible values:                                                                                                        |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **Yes**: The node task will be re-executed, and the following parameters must be configured:                                                                                             |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       |    -  **Maximum Retries**                                                                                                                                                                   |
   |                                  |                       |    -  **Retry Interval (seconds)**                                                                                                                                                          |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **No**: The node task will not be re-executed. This is the default setting.                                                                                                              |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | .. note::                                                                                                                                                                                   |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       |    If **Timeout Interval** is configured for the node, the node will not be executed again after the execution times out. Instead, the node is set to the failure state.                    |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Failure Policy                   | Yes                   | Operation that will be performed if the node task fails to be executed. Possible values:                                                                                                    |
   |                                  |                       |                                                                                                                                                                                             |
   |                                  |                       | -  **End the current job execution plan**: stops running the current job. The job instance status is **Failed**.                                                                            |
   |                                  |                       | -  **Go to the next node**: ignores the execution failure of the current node. The job instance status is **Failure ignored**.                                                              |
   |                                  |                       | -  **Suspend current job execution plan**: suspends running the current job. The job instance status is **Waiting**.                                                                        |
   |                                  |                       | -  **Suspend execution plans of the subsequent nodes**: stops running subsequent nodes. The job instance status is **Failed**.                                                              |
   +----------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
