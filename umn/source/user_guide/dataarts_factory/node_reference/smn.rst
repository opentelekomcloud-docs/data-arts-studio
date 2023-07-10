:original_name: dataartsstudio_01_0468.html

.. _dataartsstudio_01_0468:

SMN
===

Functions
---------

The SMN node is used to send notifications to users.

Parameters
----------

:ref:`Table 1 <dataartsstudio_01_0468__en-us_topic_0121505665_table3764823994826>` and :ref:`Table 2 <dataartsstudio_01_0468__en-us_topic_0121505665_table58040457102411>` describe the parameters of the SMN node.

.. _dataartsstudio_01_0468__en-us_topic_0121505665_table3764823994826:

.. table:: **Table 1** Parameters of SMN nodes

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================+
   | Node Name             | Yes                   | Name of a node. The name must contain 1 to 128 characters, including only letters, numbers, underscores (_), hyphens (-), slashes (/), less-than signs (<), and greater-than signs (>). |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Topic Name            | Yes                   | Name of the topic. The topic has been created in SMN.                                                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Message Title         | No                    | Title of the message. The title cannot exceed 512 characters.                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Message Type          | Yes                   | Format of the message.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **Text**: The message is sent in text format.                                                                                                                                        |
   |                       |                       | -  **JSON**: The message is sent in JSON format. You can send different messages to types of subscribers.                                                                               |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    -  Manual: You can enter a message in **Message Content**.                                                                                                                           |
   |                       |                       |    -  Automatic: Click **Generate JSON Message**. In the displayed dialog box, enter a message and select a protocol.                                                                   |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **Template**: The message is sent in template format, that is, in fixed format. The variables can be processed by tags.                                                              |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    -  Manual: You can enter a message in **Message Content**.                                                                                                                           |
   |                       |                       |    -  Automatic: Click **Generate Template Message**. In the displayed dialog box, select a template name and set the value of **tag**.                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Message Content       | Yes                   | Message content to be provided. The requirements for entering different types of messages are as follows:                                                                               |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **Text**: The size cannot exceed 10 KB.                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **JSON**: The JSON message must contain the Default protocol and the size cannot exceed 10 KB.                                                                                       |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    Example:                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    .. code-block::                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |       {                                                                                                                                                                                 |
   |                       |                       |         "default": "Dear Sir or Madam, this is a default message.",                                                                                                                     |
   |                       |                       |         "email": "Dear Sir or Madam, this is an email message.",                                                                                                                        |
   |                       |                       |         "http": "{'message':'Dear Sir or Madam, this is an HTTP message.'}",                                                                                                            |
   |                       |                       |         "https": "{'message':'Dear Sir or Madam, this is an HTTPS message.'}",                                                                                                          |
   |                       |                       |         "sms": "This is an SMS message."                                                                                                                                                |
   |                       |                       |           }                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **Template**: The size cannot exceed 10 KB.                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    Example:                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    .. code-block::                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |       "message_template_name":"confirm_message",                                                                                                                                        |
   |                       |                       |       "tags":{                                                                                                                                                                          |
   |                       |                       |           "topic_urn":"urn:smn:regionId:xxxx:SMN_01"                                                                                                                                    |
   |                       |                       |            }                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       |    In the preceding information, **message_template_name** indicates the template name, and **tags** indicates all tags in the template.                                                |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | For details about how to configure SMN, see section the *Simple Message Notification User Guide*.                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0468__en-us_topic_0121505665_table58040457102411:

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
