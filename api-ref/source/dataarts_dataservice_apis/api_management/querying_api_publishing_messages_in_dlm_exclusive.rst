:original_name: SearchPublishInfo.html

.. _SearchPublishInfo:

Querying API Publishing Messages in DLM Exclusive
=================================================

Function
--------

This API is used to query the API publishing messages in different clusters.

After an API operation (such as debugging and registration) is performed in a cluster, API publishing messages are generated.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/apis/{api_id}/publish-info

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | api_id     | Yes       | String | API ID                                                                                                                  |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                           |
   +===========+===========+=========+=======================================================================================================================================================================================+
   | limit     | No        | Integer | Maximum number of records that can be queried                                                                                                                                         |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset    | No        | Integer | Query offset, that is, X data records are skipped. The value must be **0** or an integer multiple of **limit**. If the value does not meet the requirements, it will be rounded down. |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------+-----------------------------------------------------------------------------------+---------------------------+
   | Parameter        | Type                                                                              | Description               |
   +==================+===================================================================================+===========================+
   | total            | Integer                                                                           | Total number.             |
   +------------------+-----------------------------------------------------------------------------------+---------------------------+
   | publish_messages | Array of :ref:`ApiPublishDTO <searchpublishinfo__response_apipublishdto>` objects | Release information list. |
   +------------------+-----------------------------------------------------------------------------------+---------------------------+

.. _searchpublishinfo__response_apipublishdto:

.. table:: **Table 5** ApiPublishDTO

   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                  |
   +=======================+=======================+==============================================================================+
   | id                    | String                | Release ID.                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | api_id                | String                | API ID                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | instance_id           | String                | Cluster ID                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | instance_name         | String                | Cluster Name                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | api_status            | String                | API status (DataArts DataService Shared)                                     |
   |                       |                       |                                                                              |
   |                       |                       | Enumerated values:                                                           |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_CREATED**: created                                           |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_PUBLISH_WAIT_REVIEW**: waiting for review                    |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_PUBLISH_REJECT**: rejected                                   |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_PUBLISHED**: published                                       |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_WAITING_STOP**: waiting to be stopped                        |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_STOPPED**: stopped                                           |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_RECOVER_WAIT_REVIEW**: waiting to be recovered               |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_WAITING_OFFLINE**: waiting to be suspended                   |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_OFFLINE**: suspended                                         |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_STATUS_OFFLINE_WAIT_REVIEW**: waiting to be reviewed for suspension |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | api_debug             | String                | API debugging status (DataArts DataService Shared)                           |
   |                       |                       |                                                                              |
   |                       |                       | Enumerated values:                                                           |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_DEBUG_WAITING**: waiting to be debugged                             |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_DEBUG_FAILED**: debugging failed                                    |
   |                       |                       |                                                                              |
   |                       |                       | -  **API_DEBUG_SUCCESS**: debugging successful                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query the API publishing information in different clusters.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/publish-info

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total" : 1,
     "publish_messages" : [ {
       "id" : "343a6d4c0ad108376ebd060c9c33cc33",
       "api_id" : "47046fe7830c1be77cb0dc23bd86afa5",
       "instance_id" : "c2e27497562ed193583378e052248003",
       "instance_name" : "cluster_test_001",
       "api_status" : "API_STATUS_CREATED",
       "api_debug" : "API_DEBUG_WAITING"
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Success
400         Bad request
=========== ===========
