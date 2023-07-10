:original_name: dataartsstudio_01_0460.html

.. _dataartsstudio_01_0460:

RDS SQL
=======

Functions
---------

The RDS SQL node is used to transfer SQL statements to RDS.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0460__en-us_topic_0101095441_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0460__en-us_topic_0101095441_table58040457102411>` describe the parameters of the RDS SQL node.

.. _dataartsstudio_01_0460__en-us_topic_0101095441_table3764823994826:

.. table:: **Table 1** Parameters of RDS SQL nodes

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================================================================+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data Connection       | Yes                   | Name of the data connection.                                                                                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database              | Yes                   | Name of the database. The database has been created. You are advised not to use the default database.                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SQL or Script         | Yes                   | You can select **SQL statement** or **SQL script**.                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       | -  SQL statement                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       |    In the **Statements** text box, enter the SQL statement to be executed.                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       | -  SQL script                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       |    Select a script to be executed. If no script is available, create and develop a script by referring to :ref:`Creating a Script <dataartsstudio_01_0423>` and :ref:`Developing an SQL Script <dataartsstudio_01_0424>`. |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       |    .. note::                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                           |
   |                       |                       |       If you select the SQL statement mode, the DataArts Factory module cannot parse the parameters contained in the SQL statement.                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0460__en-us_topic_0101095441_table58040457102411:

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
