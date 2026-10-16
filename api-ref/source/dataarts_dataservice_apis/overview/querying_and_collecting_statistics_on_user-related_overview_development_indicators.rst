:original_name: ShowApisOverview.html

.. _ShowApisOverview:

Querying and Collecting Statistics on User-related Overview Development Indicators
==================================================================================

Function
--------

This API is used to query and collect statistics on user-related overview development metrics.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/statistic/apis-overview

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                      |
   +=================+=================+=================+==================================+
   | start_time      | Yes             | Long            | Start time (13-digit timestamp). |
   +-----------------+-----------------+-----------------+----------------------------------+
   | end_time        | Yes             | Long            | End time (13-digit timestamp).   |
   +-----------------+-----------------+-----------------+----------------------------------+
   | time_unit       | Yes             | String          | Time unit                        |
   |                 |                 |                 |                                  |
   |                 |                 |                 | Enumerated values:               |
   |                 |                 |                 |                                  |
   |                 |                 |                 | -  **HOUR**: hour                |
   |                 |                 |                 |                                  |
   |                 |                 |                 | -  **DAY**: day                  |
   +-----------------+-----------------+-----------------+----------------------------------+

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

   +----------------+---------+---------------------------------------------------------------+
   | Parameter      | Type    | Description                                                   |
   +================+=========+===============================================================+
   | publish_num    | Integer | Number of released APIs.                                      |
   +----------------+---------+---------------------------------------------------------------+
   | developing_num | Integer | Number of APIs being developed.                               |
   +----------------+---------+---------------------------------------------------------------+
   | apply_num      | Integer | Number of applications.                                       |
   +----------------+---------+---------------------------------------------------------------+
   | call_num       | Integer | Total number of invoking times.                               |
   +----------------+---------+---------------------------------------------------------------+
   | success_num    | Integer | Number of successful invoking times (data obtaining success). |
   +----------------+---------+---------------------------------------------------------------+
   | fail_num       | Integer | Number of failed invoking times (data obtaining failure).     |
   +----------------+---------+---------------------------------------------------------------+
   | legal_num      | Integer | Number of valid invoking times (pass the verification).       |
   +----------------+---------+---------------------------------------------------------------+
   | illegal_num    | Integer | Invalid invoking volume (failed to pass the verification).    |
   +----------------+---------+---------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query and collect statistics on user-related overview development metrics.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/statistic/apis-overview

Example Responses
-----------------

**Status code: 200**

The user-related overview development indicators are successfully queried.

.. code-block::

   {
     "publish_num" : 54,
     "developing_num" : 117,
     "apply_num" : 4,
     "call_num" : 10,
     "success_num" : 9,
     "fail_num" : 1,
     "legal_num" : 10,
     "illegal_num" : 0
   }

Status Codes
------------

+-------------+----------------------------------------------------------------------------+
| Status Code | Description                                                                |
+=============+============================================================================+
| 200         | The user-related overview development indicators are successfully queried. |
+-------------+----------------------------------------------------------------------------+
| 400         | Bad request                                                                |
+-------------+----------------------------------------------------------------------------+
