:original_name: ListApiTopN.html

.. _ListApiTopN:

Querying Top N APIs Called by a Specified API Application
=========================================================

Function
--------

This API is used to query top N APIs called by a specified application.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/statistic/apis-top-n/{api_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | api_id     | Yes       | String | API ID                                                                                                                  |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | instance_id     | No              | String          | Cluster ID                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | start_time      | Yes             | Long            | Start time (13-digit timestamp).                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | end_time        | Yes             | Long            | End time (13-digit timestamp).                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | time_unit       | Yes             | String          | Time unit                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Enumerated values:                                               |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **HOUR**: hour                                                |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **DAY**: day                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | top_num         | Yes             | Integer         | The first few.                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | order_by        | Yes             | String          | Sorting criteria                                                 |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Enumerated values:                                               |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **CALL_NUM**: total number of calls                           |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **SUCCESS_NUM**: number of successful calls                   |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **FAIL_NUM**: number of failed calls                          |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **LEGAL_NUM**: number of legal calls                          |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **ILLEGAL_NUM**: number of illegal calls                      |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **COST_TIME_AVG**: average time                               |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **SUCCESS_COST_TIME_AVG**: average time for a successful call |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **FAIL_COST_TIME_AVG**: average time for a failed call        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **SUCCESS_RATE**: rate of successful calls                    |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **FAIL_RATE**: rate of failed calls                           |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **LEGAL_RATE**: rate of legal calls                           |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  **ILLEGAL_RATE**: rate of illegal calls                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

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

   +------------+-----------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter  | Type                                                                                          | Description                              |
   +============+===============================================================================================+==========================================+
   | statistics | Array of :ref:`StatisticForCallDetail <listapitopn__response_statisticforcalldetail>` objects | Indicates the invoking information list. |
   +------------+-----------------------------------------------------------------------------------------------+------------------------------------------+

.. _listapitopn__response_statisticforcalldetail:

.. table:: **Table 5** StatisticForCallDetail

   +-------------+---------+---------------------------------------------------------------+
   | Parameter   | Type    | Description                                                   |
   +=============+=========+===============================================================+
   | id          | String  | ID of a statistical object.                                   |
   +-------------+---------+---------------------------------------------------------------+
   | name        | String  | Name of the statistics object.                                |
   +-------------+---------+---------------------------------------------------------------+
   | call_num    | Integer | Total number of invoking times.                               |
   +-------------+---------+---------------------------------------------------------------+
   | success_num | Integer | Number of successful invoking times (data obtaining success). |
   +-------------+---------+---------------------------------------------------------------+
   | fail_num    | Integer | Number of failed invoking times (data obtaining failure).     |
   +-------------+---------+---------------------------------------------------------------+
   | legal_num   | Integer | Number of valid invoking times (pass the verification).       |
   +-------------+---------+---------------------------------------------------------------+
   | illegal_num | Integer | Invalid invoking volume (failed to pass the verification).    |
   +-------------+---------+---------------------------------------------------------------+

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

Query top N APIs called by a specified application.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/statistic/apis-top-n/760715eb1bfce0c575abab3be3bd41e6

Example Responses
-----------------

**Status code: 200**

The top N APIs called by a specified application are queried successfully.

.. code-block::

   {
     "statistics" : [ {
       "id" : "3423634676234236674",
       "name" : "Statistical Object Name",
       "call_num" : 0,
       "success_num" : 0,
       "fail_num" : 0,
       "legal_num" : 0,
       "illegal_num" : 0
     } ]
   }

Status Codes
------------

+-------------+----------------------------------------------------------------------------+
| Status Code | Description                                                                |
+=============+============================================================================+
| 200         | The top N APIs called by a specified application are queried successfully. |
+-------------+----------------------------------------------------------------------------+
| 400         | Bad request                                                                |
+-------------+----------------------------------------------------------------------------+
