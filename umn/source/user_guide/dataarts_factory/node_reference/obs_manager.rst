:original_name: dataartsstudio_01_0464.html

.. _dataartsstudio_01_0464:

OBS Manager
===========

Constraints
-----------

This function depends on OBS.

Function
--------

The OBS Manager node is used to move or copy files from an OBS bucket to a specified directory.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0464__en-us_topic_0156398631_table3764823994826>`, :ref:`Table 2 <dataartsstudio_01_0464__en-us_topic_0156398631_table58040457102411>`, and :ref:`Table 3 <dataartsstudio_01_0464__en-us_topic_0114569494_table987664914213>` describe the parameters of the OBS Managernode node.

.. _dataartsstudio_01_0464__en-us_topic_0156398631_table3764823994826:

.. table:: **Table 1** Parameters of OBS Manager nodes

   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory             | Description                                                                                                                                                                                                                                                        |
   +==========================+=======================+====================================================================================================================================================================================================================================================================+
   | Node Name                | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>).                                                                            |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation Type           | Yes                   | Operations that can be performed on the node.                                                                                                                                                                                                                      |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Move File**: moves a source file or directory to a new directory.                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Copy File**: copies the source file or directory.                                                                                                                                                                                                             |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Rename File**: renames the last level of the directory or file.                                                                                                                                                                                               |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       |    For example, you can rename the directory **obs://test/a/b/c/** as **obs://test/a/b/d/**, and rename the file **obs://test/a/b/hello.txt** as **obs://test/a/b/bye.txt**.                                                                                       |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       | -  **Monitor File**: checks whether a file or directory exists. If the file or directory exists, the node is executed successfully. Otherwise, the node fails to be executed.                                                                                      |
   |                          |                       |                                                                                                                                                                                                                                                                    |
   |                          |                       |    If you want the job to be handled in different ways based on whether the file or directory exists, you can set an IF condition based on the execution status of the node. For details, see :ref:`IF Statements <dataartsstudio_01_0583>`.                       |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Source File or Directory | Yes                   | OBS file or directory to be managed in the OBS bucket.                                                                                                                                                                                                             |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Target Directory         | Yes                   | Directory for storing OBS files to be moved or copied from the OBS bucket.                                                                                                                                                                                         |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | File Filter              | No                    | Wildcard for file filtering. Only the files that meet the filtering condition can be moved or copied. If this parameter is not specified, all source files are moved by default. For example, when you enter \*.csv, files in this format will be moved or copied. |
   +--------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0464__en-us_topic_0156398631_table58040457102411:

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

.. _dataartsstudio_01_0464__en-us_topic_0114569494_table987664914213:

.. table:: **Table 3** Lineage

   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Description                                                                                                                                                 |
   +==============+=============================================================================================================================================================+
   | **Input**    |                                                                                                                                                             |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add          | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK           | Click **OK** to save the parameter settings.                                                                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel       | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify       | Click |image7| to modify the parameter settings. After the modification, save the settings.                                                                 |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete       | Click |image8| to delete the parameter settings.                                                                                                            |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details | Click |image9| to view details about the table created based on the input lineage.                                                                          |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Output**   |                                                                                                                                                             |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add          | Click **Add**. In the **Type** drop-down list, select the type to be created. The value can be **DWS**, **OBS**, **CSS**, **HIVE**, **DLI**, or **CUSTOM**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OK           | Click **OK** to save the parameter settings.                                                                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cancel       | Click **Cancel** to cancel the parameter settings.                                                                                                          |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify       | Click |image10| to modify the parameter settings. After the modification, save the settings.                                                                |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete       | Click |image11| to delete the parameter settings.                                                                                                           |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View Details | Click |image12| to view details about the table created based on the output lineage.                                                                        |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002269198773.png
.. |image2| image:: /_static/images/en-us_image_0000002269198765.png
.. |image3| image:: /_static/images/en-us_image_0000002234079480.png
.. |image4| image:: /_static/images/en-us_image_0000002269118737.png
.. |image5| image:: /_static/images/en-us_image_0000002269198821.png
.. |image6| image:: /_static/images/en-us_image_0000002269118733.png
.. |image7| image:: /_static/images/en-us_image_0000002269198773.png
.. |image8| image:: /_static/images/en-us_image_0000002269198765.png
.. |image9| image:: /_static/images/en-us_image_0000002234079480.png
.. |image10| image:: /_static/images/en-us_image_0000002269118737.png
.. |image11| image:: /_static/images/en-us_image_0000002269198821.png
.. |image12| image:: /_static/images/en-us_image_0000002269118733.png
