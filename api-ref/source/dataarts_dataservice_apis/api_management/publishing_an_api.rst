:original_name: PublishApiToInstance.html

.. _PublishApiToInstance:

Publishing an API
=================

Function
--------

Publish the API Only published APIs can be called. You can choose to publish an API to a specified gateway.

-  Shared version, which must be sent to the shared version of API Gateway.

-  Exclusive: You can choose to send APIs to API Gateway Exclusive, ROMA-APIC, or not to publish the gateway as required.

   If the initiator of the release request is not the reviewer, the API reviewer needs to review the application.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apis/{api_id}/instances/{instance_id}/publish

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

   +------------------+-----------------+-----------------+-------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                     |
   +==================+=================+=================+=================================================+
   | apig_type        | No              | String          | Gateway type                                    |
   |                  |                 |                 |                                                 |
   |                  |                 |                 | Enumerated values:                              |
   |                  |                 |                 |                                                 |
   |                  |                 |                 | -  **APIG**                                     |
   |                  |                 |                 |                                                 |
   |                  |                 |                 | -  **APIGW**                                    |
   |                  |                 |                 |                                                 |
   |                  |                 |                 | -  **ROMA_APIC**                                |
   +------------------+-----------------+-----------------+-------------------------------------------------+
   | apig_instance_id | No              | String          | Specifies the gateway instance ID.              |
   +------------------+-----------------+-----------------+-------------------------------------------------+
   | group_id_in_apig | No              | String          | Gateway group ID.                               |
   +------------------+-----------------+-----------------+-------------------------------------------------+
   | roma_app_id      | No              | String          | ID of the ROMA gateway integration application. |
   +------------------+-----------------+-----------------+-------------------------------------------------+

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

Publish the API whose ID is **760715eb1bfce0c575abab3be3bd41e6** to a cluster.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/instances/21398ikjdsjd9087122d4e/publish

   {
     "apig_type" : "APIG",
     "apig_instance_id" : "APIG",
     "group_id_in_apig" : "c4ba07ad2ae14015921c36aa4136e14c"
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
