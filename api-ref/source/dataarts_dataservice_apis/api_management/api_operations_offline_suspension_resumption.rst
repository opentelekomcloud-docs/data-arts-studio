:original_name: ExecuteApiToInstance.html

.. _ExecuteApiToInstance:

API operations (offline/suspension/resumption)
==============================================

Function
--------

-  Bring the API offline. Take a published API offline. After the API is unpublished, its authorization will be canceled and the API cannot be called.

-  Disable an API. Temporarily take a published API offline. After the API is suspended, its authorization will be retained. The API cannot be called during the suspension.

-  Restore the API. This API is used to resume a disabled API. After the API is restored, it can be called again.

.. note::

   -  If the initiator of the resumption request is not the reviewer, the API reviewer needs to review the application.

   -  Initiator of the request for bringing an API offline or disabling an API. The initiator must be the API reviewer.

   -  The offline/disable function requires sufficient preparation time for authorized applications. A request must be initiated at least two days in advance. If you need to unpublish or suspend an API immediately, your requested action will be taken only after all apps finish processing messages.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apis/{api_id}/instances/{instance_id}/action

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                             |
   +=============+===========+========+=========================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | api_id      | Yes       | String | API ID                                                                                                                  |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Cluster ID                                                                                                              |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                    |
   +==============+===========+========+================================================================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service.                                             |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                                              |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dlm-Type     | No        | String | Specifies the version type of the data service. The value can be SHARED or EXCLUSIVE.                                                                                                                                                                                                                          |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Type (format) of the message body. This parameter is mandatory if the message body exists. If the message body does not exist, leave this parameter blank. If the request body contains Chinese characters, use charset=utf8 to specify the Chinese character set, for example, application/json;charset=utf8. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+---------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                           |
   +=================+=================+=================+=======================================+
   | time            | No              | String          | End time.                             |
   +-----------------+-----------------+-----------------+---------------------------------------+
   | action          | No              | String          | Operation type                        |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Enumerated values:                    |
   |                 |                 |                 |                                       |
   |                 |                 |                 | -  **UNPUBLISH**: unpublishing an API |
   |                 |                 |                 |                                       |
   |                 |                 |                 | -  **STOP**: stopping an API          |
   |                 |                 |                 |                                       |
   |                 |                 |                 | -  **RECOVER**: recovering an API     |
   +-----------------+-----------------+-----------------+---------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Unpublish, suspend, or recover the API whose ID is 760715eb1bfce0c575abab3be3bd41e6 in the cluster whose ID is 51159105c7838353d2834181d978af50.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/instances/51159105c7838353d2834181d978af50/action

   {
     "action" : "UNPUBLISH",
     "time" : "2022-03-25T10:00:00.000Z"
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ================================
Status Code Description
=========== ================================
204         The API operation is successful.
400         Bad request
=========== ================================
