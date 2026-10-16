:original_name: ListInstanceList.html

.. _ListInstanceList:

Querying Instances for API Operations in DLM Exclusive
======================================================

Function
--------

This API is used to query instances for API operations (Exclusive Edition).

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/apis/{api_id}/instances

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | api_id     | Yes       | String | API ID                                                                                                                  |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================+
   | action          | Yes             | String          | API operation                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | Enumerated values include:                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **PUBLISH**: publishing an API                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **UNPUBLISH**: unpublishing an API                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **STOP**: stopping an API                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **RECOVER**: recovering an API                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **WHITELIST**: whitelist-related operations                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  \**AUTHORIZE: authorization                                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | show_all        | No              | Boolean         | All instances (including instances on which the current operation cannot be performed) are displayed.                                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | check_status    | No              | Boolean         | Verify the API status.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | check_debug     | No              | Boolean         | API debugging status check                                                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_id          | No              | String          | App ID, which is used to determine the optional instance of the authorized app                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records that can be queried                                                                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Query offset, that is, X data records are skipped. The value must be **0** or an integer multiple of **limit**. If the value does not meet the requirements, it will be rounded down. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | Parameter | Type                                                                                                 | Description                                                     |
   +===========+======================================================================================================+=================================================================+
   | instances | Array of :ref:`InstanceForApiActionDTO <listinstancelist__response_instanceforapiactiondto>` objects | Indicates the instance list corresponding to the API operation. |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+

.. _listinstancelist__response_instanceforapiactiondto:

.. table:: **Table 5** InstanceForApiActionDTO

   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                        |
   +=======================+=======================+====================================================================+
   | instance_id           | String                | Cluster ID                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | instance_type         | String                | Cluster type                                                       |
   |                       |                       |                                                                    |
   |                       |                       | Enumerated values:                                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **DLM**: DataArts DataService cluster                           |
   |                       |                       |                                                                    |
   |                       |                       | -  **APIG**: APIG cluster                                          |
   |                       |                       |                                                                    |
   |                       |                       | -  **APIGW**: APIGW cluster                                        |
   |                       |                       |                                                                    |
   |                       |                       | -  **ROMA_APIC**: ROMA cluster                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | name                  | String                | Cluster name                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | action                | String                | API operation                                                      |
   |                       |                       |                                                                    |
   |                       |                       | Enumerated values:                                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **PUBLISH**: publishing an API                                  |
   |                       |                       |                                                                    |
   |                       |                       | -  **UNPUBLISH**: unpublishing an API                              |
   |                       |                       |                                                                    |
   |                       |                       | -  **STOP**: stopping an API                                       |
   |                       |                       |                                                                    |
   |                       |                       | -  **RECOVER**: recovering an API                                  |
   |                       |                       |                                                                    |
   |                       |                       | -  **WHITELIST**: whitelist-related operations                     |
   |                       |                       |                                                                    |
   |                       |                       | -  \**AUTHORIZE: authorization                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | result                | Boolean               | Indicates the verification result.                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | cause                 | String                | Cause of the verification failure                                  |
   |                       |                       |                                                                    |
   |                       |                       | Enumerated values:                                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_ERROR**: API status error                          |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_DEBUG_ERROR**: API debugging status error                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **TYPE_MISMATCH**: The app type and instance type do not match. |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | api_status            | String                | API status (DataArts DataService Shared)                           |
   |                       |                       |                                                                    |
   |                       |                       | Enumerated values:                                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_CREATED**: created                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_PUBLISH_WAIT_REVIEW**: waiting for review          |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_PUBLISH_REJECT**: rejected                         |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_PUBLISHED**: published                             |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_WAITING_STOP**: waiting to be stopped              |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_STOPPED**: stopped                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_RECOVER_WAIT_REVIEW**: waiting to be recovered     |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_WAITING_OFFLINE**: waiting to be suspended         |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_STATUS_OFFLINE**: suspended                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | api_debug             | String                | API debugging status (DataArts DataService Shared)                 |
   |                       |                       |                                                                    |
   |                       |                       | Enumerated values:                                                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_DEBUG_WAITING**: waiting to be debugged                   |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_DEBUG_FAILED**: debugging failed                          |
   |                       |                       |                                                                    |
   |                       |                       | -  **API_DEBUG_SUCCESS**: debugging successful                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------+

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

Query instances for API operations in DataArts DataService Exclusive.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/instances

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "instances" : [ {
       "instance_id" : "c2e27497562ed193583378e052248003",
       "instance_type" : "DLM",
       "name" : "cluster_test_001",
       "action" : "PUBLISH",
       "result" : false,
       "cause" : "API_STATUS_ERROR",
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
