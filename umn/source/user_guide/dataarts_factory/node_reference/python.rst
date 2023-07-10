:original_name: dataartsstudio_01_4504.html

.. _dataartsstudio_01_4504:

Python
======

Functions
---------

The Python node is used to execute Python statements.

Before using a Python node, ensure that the host connected to the node has an environment for executing Python scripts.

.. note::

   Python nodes do not support script parameters or job parameters.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_4504__en-us_topic_0113842761_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_4504__table1396374719116>` describe the parameters of the Python node.

.. _dataartsstudio_01_4504__en-us_topic_0113842761_table3764823994826:

.. table:: **Table 1** Parameters of the Python node

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================================================================================================================+
   | Python or Script      | Yes                   | You can select **Python statement** or **Python script**.                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       | -  Python statement                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       |    In the **Python statement** text box, enter the Python statement to be executed.                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       | -  Python script                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       |    Select a script to be executed for **Script Path**. If no script is available, create and develop a script by referring to :ref:`Creating a Script <dataartsstudio_01_0423>` and :ref:`Developing a Python Script <dataartsstudio_01_4503>`. |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       |    .. note::                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                 |
   |                       |                       |       If you select **Python statement**, the DataArts Factory module cannot parse the parameters contained in the Python statement.                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host Connection       | Yes                   | Select the host where the Python statement is to be executed. Ensure that the host has an environment for executing Python scripts.                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name             | Yes                   | Name of the node. The value must consist of 1 to 128 characters and contain only letters, digits, and the following special characters: \_-/<>.                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_4504__table1396374719116:

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
