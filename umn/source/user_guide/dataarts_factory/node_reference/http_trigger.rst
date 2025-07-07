:original_name: dataartsstudio_01_0489.html

.. _dataartsstudio_01_0489:

Http Trigger
============

Functions
---------

Http Trigger is a cross-platform scheduling trigger node of DataArts Studio. If you want to trigger a job on DataArts Studio after a job on another scheduling system is complete, you can use the Http Trigger node.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0489__en-us_topic_0118184397_table3764823994826>` describes the parameter of the Http Trigger node.

.. _dataartsstudio_01_0489__en-us_topic_0118184397_table3764823994826:

.. table:: **Table 1** Parameter of the Http Trigger node

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================+
   | Node ID               | No                    | ID of the Http Trigger node. When you add an Http Trigger node, the system automatically generates a node ID, which is unique in the workspace and cannot be changed.                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Maximum Wait Time     | Yes                   | Maximum wait time for HTTP messages. If no message is received within this time, the node and its subsequent nodes are canceled and the job is stopped.                                 |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | The value ranges from 1 to 24 hours. The default value is 24 hours.                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
