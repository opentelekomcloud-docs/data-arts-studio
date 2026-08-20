:original_name: DebugApi.html

.. _DebugApi:

Debugging an API
================

Function
--------

Debug the API.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apis/{api_id}/instances/{instance_id}/test

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

   +-----------+-----------+-------------------------------------------------------------+--------------------------+
   | Parameter | Mandatory | Type                                                        | Description              |
   +===========+===========+=============================================================+==========================+
   | body      | No        | String                                                      | Request body             |
   +-----------+-----------+-------------------------------------------------------------+--------------------------+
   | paras     | No        | :ref:`ApiTestParas <debugapi__request_apitestparas>` object | Indicates the parameter. |
   +-----------+-----------+-------------------------------------------------------------+--------------------------+

.. _debugapi__request_apitestparas:

.. table:: **Table 4** ApiTestParas

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   page_size No        String page size.
   page_num  No        String page num.
   ========= ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | Parameter       | Type                                                                           | Description                                    |
   +=================+================================================================================+================================================+
   | request_id      | String                                                                         | Request ID.                                    |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | url             | String                                                                         | Request URL.                                   |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | result          | String                                                                         | Indicates the debugging result.                |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | timeout         | Long                                                                           | Indicates the debugging duration.              |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | success         | Boolean                                                                        | Indicates whether the debugging is successful. |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | request_header  | :ref:`ApiTestRequestHeader <debugapi__response_apitestrequestheader>` object   | Request header                                 |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+
   | response_header | :ref:`ApiTestResponseHeader <debugapi__response_apitestresponseheader>` object | Response header.                               |
   +-----------------+--------------------------------------------------------------------------------+------------------------------------------------+

.. _debugapi__response_apitestrequestheader:

.. table:: **Table 6** ApiTestRequestHeader

   ============== ======= ====================================
   Parameter      Type    Description
   ============== ======= ====================================
   path           String  Request path
   user_agent     String  Proxy (fixed value).
   x_apig_mode    String  Request mode (fixed value).
   x_app_identity Integer Identification number (fixed value).
   ============== ======= ====================================

.. _debugapi__response_apitestresponseheader:

.. table:: **Table 7** ApiTestResponseHeader

   ============== ======= ==================================
   Parameter      Type    Description
   ============== ======= ==================================
   result_status  String  Whether the request is successful.
   content_length Integer Content size.
   connection     String  Connection status.
   cache_control  String  Cache control (fixed value).
   content_type   String  Content type (fixed value).
   date           String  Date.
   x_request_id   String  Request ID.
   ============== ======= ==================================

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Debug an API.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/instances/51159105c7838353d2834181d978af50/test

   {
     "body" : "b",
     "paras" : {
       "page_size" : "10",
       "page_num" : "1"
     }
   }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "request_header" : {
       "path" : "GET /testApi/1 HTTP",
       "user_agent" : "DLMDebugClient/1.0",
       "x_apig_mode" : "DEBUG",
       "x_app_identity" : 1
     },
     "request_id" : "704742365000242752",
     "response_header" : {
       "cache_control" : "private",
       "connection" : "keep-alive",
       "content_length" : 2,
       "content_type" : "application/json;charset=UTF-8",
       "date" : "Tue Apr 28 17:14:37 GMT+08:00 2020",
       "result_status" : "HTTP 200 Success",
       "x_request_id" : "704742365000242752"
     },
     "result" : "[]",
     "success" : true,
     "timeout" : 3826,
     "url" : "/testApi/1"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Success
400         Bad request
=========== ===========
