:original_name: dataartsstudio_01_0538.html

.. _dataartsstudio_01_0538:

Kafka Client
============

Functions
---------

The Kafka Client node is used to send data to Kafka topics.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0538__en-us_topic_0235670394_table3764823994826>` describes the parameters of the Kafka Client node.

.. _dataartsstudio_01_0538__en-us_topic_0235670394_table3764823994826:

.. table:: **Table 1** Parameters of Kafka Client nodes

   +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Description                                                                                                                                                                             |
   +=================+===========+=========================================================================================================================================================================================+
   | Data Connection | Yes       | Select the MRS Kafka connection created in the management center.                                                                                                                       |
   +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Topic Name      | Yes       | Select the topic to which data is to be uploaded. If there are multiple partitions, data is sent to partition 0 by default.                                                             |
   +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name       | Yes       | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Text            | Yes       | Text content sent to Kafka. You can directly enter text or click |image2| to use the EL expression.                                                                                     |
   +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. |image1| image:: /_static/images/en-us_image_0000001321928488.png
.. |image2| image:: /_static/images/en-us_image_0000001321928488.png
