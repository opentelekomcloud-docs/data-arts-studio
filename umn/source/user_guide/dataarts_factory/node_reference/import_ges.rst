:original_name: dataartsstudio_01_0448.html

.. _dataartsstudio_01_0448:

Import GES
==========

Function
--------

The Import GES node is used to import files from an OBS bucket to a GES graph.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0448__en-us_topic_0156398630_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0448__en-us_topic_0156398630_table58040457102411>` describe the parameters of the Import GES node.

.. _dataartsstudio_01_0448__en-us_topic_0156398630_table3764823994826:

.. table:: **Table 1** Parameters of Import GES nodes

   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Mandatory             | Description                                                                                                                                                                             |
   +===================================+=======================+=========================================================================================================================================================================================+
   | Node Name                         | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Graph Name                        | Yes                   | You can directly select the graph to import or manually enter the graph name.                                                                                                           |
   |                                   |                       |                                                                                                                                                                                         |
   |                                   |                       | To create a GES graph, go to the GES console.                                                                                                                                           |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metadata                          | Yes                   | You can directly select the corresponding metadata or manually enter the OBS path of the metadata.                                                                                      |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Edge Data Set                     | Yes                   | You can directly select the corresponding edge data set or manually enter the OBS path of the edge data set.                                                                            |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Vertex Data Set                   | No                    | You can directly select the corresponding Vertex data set or manually enter the OBS path of the Vertex data set.                                                                        |
   |                                   |                       |                                                                                                                                                                                         |
   |                                   |                       | If it is not selected, the vertices in the edge dataset are used as the source of the vertex dataset.                                                                                   |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Edge Processing                   | Yes                   | The edge processing supports the following modes:                                                                                                                                       |
   |                                   |                       |                                                                                                                                                                                         |
   |                                   |                       | -  Allow repetitive edges                                                                                                                                                               |
   |                                   |                       | -  Ignore subsequent repetitive edges                                                                                                                                                   |
   |                                   |                       | -  Overwrite previous repetitive edges                                                                                                                                                  |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Offline                           | No                    | Whether offline import is used. The value is **Yes** or **No**, and the default value is **No**.                                                                                        |
   |                                   |                       |                                                                                                                                                                                         |
   |                                   |                       | -  **true**: Offline import is selected. The import speed is high, but the graph is locked and cannot be read or written during the import.                                             |
   |                                   |                       | -  **false**: Online import is selected. Online import is slower than offline import. However, during online import, the graph can be read (but cannot be written).                     |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ignore Labels on Repetitive Edges | No                    | Indicates whether to ignore labels on repetitive edges. The value is **Yes**\ or **No**, and the default value is **Yes**.                                                              |
   |                                   |                       |                                                                                                                                                                                         |
   |                                   |                       | -  **Yes**: Indicates that the repetitive edge definition does not contain the label. That is, the <source vertex, target vertex> indicates an edge, excluding the label information.   |
   |                                   |                       | -  **No**: Indicates that the repetitive edge definition contains the label. That is, the <source vertex, target vertex, label> indicates an edge.                                      |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log Storage Path                  | No                    | Stores vertex and edge datasets that do not comply with the metadata definition, as well as detailed logs generated during graph import.                                                |
   +-----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0448__en-us_topic_0156398630_table58040457102411:

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
