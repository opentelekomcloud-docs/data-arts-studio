:original_name: dataartsstudio_01_0459.html

.. _dataartsstudio_01_0459:

Shell
=====

Functions
---------

The Shell node is used to execute a shell script.

.. note::

   With EL expression **#{Job.getNodeOutput()}**, you can obtain the desired content (4000 characters at most and counted backwards) in the output of the shell script run by the Shell node.

   Example:

   To obtain **<name>jack<name1>** from a shell script (script name: shell_job1) output, enter the following EL expression:

   .. code-block::

      #{StringUtil.substringBetween(Job.getNodeOutput("shell_job1"),"<name>","<name1>")}

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0459__en-us_topic_0113842761_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0459__en-us_topic_0113842761_table58040457102411>` describe the parameters of the Shell node.

.. _dataartsstudio_01_0459__en-us_topic_0113842761_table3764823994826:

.. table:: **Table 1** Parameters of Shell nodes

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================================================================================+
   | Shell or Script       | Yes                   | You can select **Shell statement** or **Shell script**.                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       | -  Shell statement                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       |    In the **Shell statement** text box, enter the Shell statement to be executed.                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       | -  Shell script                                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       |    Select a script to be executed. If no script is available, create and develop a script by referring to :ref:`Creating a Script <dataartsstudio_01_0423>` and :ref:`Developing an SQL Script <dataartsstudio_01_0424>`.                               |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       |    .. note::                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                         |
   |                       |                       |       If you select **Shell statement**, the DataArts Factory module cannot parse the parameters contained in the Shell statement.                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host Connection       | Yes                   | Selects the host where a shell script is to be executed.                                                                                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Script Parameter      | No                    | Parameter transferred to the script when the shell script is executed. Parameters are separated by spaces. For example: **a b c**. The parameter must be referenced by the shell script. Otherwise, the parameter is invalid.                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Interactive Input     | No                    | Interactive information (passwords for example) provided during shell script execution. Interactive parameters are separated by carriage return characters. The shell script reads parameter values in sequence according to the interaction situation. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name             | Yes                   | Name of the node. It contains a maximum of 128 characters, including letters, digits, hyphens (-), underscores (_), slashes (/), angle brackets (<>), and periods (.).                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0459__en-us_topic_0113842761_table58040457102411:

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
