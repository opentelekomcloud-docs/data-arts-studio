:original_name: ListApiCatalogList.html

.. _ListApiCatalogList:

Obtaining the List of APIs in a Catalog
=======================================

Function
--------

This API is used to obtain the list of APIs in a catalog.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/servicecatalogs/{catalog_id}/apis

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | catalog_id | Yes       | String | Catalog ID                                                                                                              |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+----------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                    |
   +===========+===========+=========+================================================================+
   | offset    | No        | Integer | Query start coordinate, that is, skipping the first X records. |
   +-----------+-----------+---------+----------------------------------------------------------------+
   | limit     | No        | Integer | Maximum number of records that can be queried                  |
   +-----------+-----------+---------+----------------------------------------------------------------+

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

   +-----------+--------------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                           | Description           |
   +===========+================================================================================+=======================+
   | total     | Integer                                                                        | Total number of APIs. |
   +-----------+--------------------------------------------------------------------------------+-----------------------+
   | apis      | Array of :ref:`ApiOverview <listapicataloglist__response_apioverview>` objects | API list.             |
   +-----------+--------------------------------------------------------------------------------+-----------------------+

.. _listapicataloglist__response_apioverview:

.. table:: **Table 5** ApiOverview

   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                                                                               | Description                                                                  |
   +=======================+====================================================================================+==============================================================================+
   | id                    | String                                                                             | API ID.                                                                      |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | name                  | String                                                                             | API name                                                                     |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | group_id              | String                                                                             | API group ID (shared version).                                               |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | description           | String                                                                             | API description,                                                             |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | status                | String                                                                             | API status (DataArts DataService Shared)                                     |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | Enumerated values:                                                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_CREATED**: created                                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_PUBLISH_WAIT_REVIEW**: waiting for review                    |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_PUBLISH_REJECT**: rejected                                   |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_PUBLISHED**: published                                       |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_WAITING_STOP**: waiting to be stopped                        |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_STOPPED**: stopped                                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_RECOVER_WAIT_REVIEW**: waiting to be recovered               |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_WAITING_OFFLINE**: waiting to be suspended                   |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_OFFLINE**: suspended                                         |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_STATUS_OFFLINE_WAIT_REVIEW**: waiting to be reviewed for suspension |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | debug_status          | String                                                                             | API debugging status (DataArts DataService Shared)                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | Enumerated values:                                                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_DEBUG_WAITING**: waiting to be debugged                             |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_DEBUG_FAILED**: debugging failed                                    |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **API_DEBUG_SUCCESS**: debugging successful                               |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | publish_messages      | Array of :ref:`ApiPublishDTO <listapicataloglist__response_apipublishdto>` objects | Release information list (exclusive edition).                                |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | type                  | String                                                                             | API type.                                                                    |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | manager               | String                                                                             | API reviewer.                                                                |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | create_user           | String                                                                             | API creator.                                                                 |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | create_time           | Long                                                                               | API creation time                                                            |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | authorization_status  | String                                                                             | Authorization status.                                                        |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | Enumerated values:                                                           |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **NO_AUTHORIZATION_REQUIRED**: no authorization required                  |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **UNAUTHORIZED**: unauthorized                                            |
   |                       |                                                                                    |                                                                              |
   |                       |                                                                                    | -  **AUTHORIZED**: authorized                                                |
   +-----------------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------+

.. _listapicataloglist__response_apipublishdto:

.. table:: **Table 6** ApiPublishDTO

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

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain the list of APIs in the catalog whose ID is 51159105c7838353d2834181d978af50.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/servicecatalogs/51159105c7838353d2834181d978af50/apis

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total" : 1,
     "apis" : [ {
       "id" : "fd0beac79418d65e3b3ed24a6e33b24b",
       "name" : "testApi",
       "create_time" : 1579162215000,
       "status" : "API_STATUS_CREATED",
       "manager" : "admin",
       "type" : null,
       "debug_status" : "API_DEBUG_WAITING"
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
