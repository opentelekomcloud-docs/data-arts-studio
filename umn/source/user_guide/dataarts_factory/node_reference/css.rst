:original_name: dataartsstudio_01_0458.html

.. _dataartsstudio_01_0458:

CSS
===

Functions
---------

The CSS node is used to process CSS requests and enable online distributed searching.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0458__en-us_topic_0101095233_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0458__en-us_topic_0101095233_table58040457102411>` describe the parameters of the CSS node.

.. _dataartsstudio_01_0458__en-us_topic_0101095233_table3764823994826:

.. table:: **Table 1** Parameters of CSS nodes

   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory             | Description                                                                                                                                                                             |
   +=========================+=======================+=========================================================================================================================================================================================+
   | Node Name               | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CloudSearch Cluster     | Yes                   | Connection to CloudSearch. A CloudSearch cluster has been created in CloudService. Currently, only clusters of version 5.5.1 is supported.                                              |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CDM Cluster Name        | Yes                   | Name of the selected CDM cluster. The CDM cluster functions as a proxy to forward requests.                                                                                             |
   |                         |                       |                                                                                                                                                                                         |
   |                         |                       | If there are no CDM clusters available in the drop-down list, create one on the CDM console.                                                                                            |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Request Type            | Yes                   | Possible values:                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                         |
   |                         |                       | -  **GET**                                                                                                                                                                              |
   |                         |                       | -  **POST**                                                                                                                                                                             |
   |                         |                       | -  **PUT**                                                                                                                                                                              |
   |                         |                       | -  **HEAD**                                                                                                                                                                             |
   |                         |                       | -  **DELETE**                                                                                                                                                                           |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Request Parameter       | No                    | Parameter of the request.                                                                                                                                                               |
   |                         |                       |                                                                                                                                                                                         |
   |                         |                       | For example, to query the dlfdata mapping type in the dlf_search index, set this parameter to:                                                                                          |
   |                         |                       |                                                                                                                                                                                         |
   |                         |                       | **/dlf_search/dlfdata/_search**                                                                                                                                                         |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Request Body            | No                    | The request body is in JSON format.                                                                                                                                                     |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CloudSearch Output Path | No                    | Path where output data is to be stored.                                                                                                                                                 |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0458__en-us_topic_0101095233_table58040457102411:

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
