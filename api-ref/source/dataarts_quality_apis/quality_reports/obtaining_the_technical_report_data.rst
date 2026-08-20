:original_name: GetQualityReportTechnologyScores.html

.. _GetQualityReportTechnologyScores:

Obtaining the Technical Report Data
===================================

Function
--------

This API is used to obtain a technical report.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/quality/report/technology/scores

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory | Type   | Description                                                                                                                                                                                     |
   +=============================+===========+========+=================================================================================================================================================================================================+
   | data_connection_id          | No        | String | Data connection ID, which is obtained from the management center.                                                                                                                               |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database_name               | No        | String | Specifies the database name.                                                                                                                                                                    |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | table_name                  | No        | String | Specifies the name of the table.                                                                                                                                                                |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_connection_score_order | No        | String | Sorting order for data connections. Value **0** indicates the ascending order, and value **1** indicates the descending order. This order is mutually exclusive with other sorting conditions.  |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database_score_order        | No        | String | Sorting order for database scores. Value **0** indicates the ascending order, and value **1** indicates the descending order. This order is mutually exclusive with other sorting conditions.   |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | table_score_order           | No        | String | Sorting order for data table scores. Value **0** indicates the ascending order, and value **1** indicates the descending order. This order is mutually exclusive with other sorting conditions. |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_timestamp             | No        | Long   | Start timestamp.                                                                                                                                                                                |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_timestamp               | No        | Long   | End timestamp.                                                                                                                                                                                  |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                       | No        | Long   | Number of records on each page. The value range is [0,100].                                                                                                                                     |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset                      | No        | Long   | Pagination offset. The minimum value is 0.                                                                                                                                                      |
   +-----------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                       |
   +==============+===========+========+===================================================================================================================================================+
   | workspace    | Yes       | String | DataArts Studio workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | IAM token. For details about how to obtain the token, see :ref:`Authentication <dataartsstudio_02_0010>`.                                         |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                                         | Description            |
   +===========+==============================================================================================+========================+
   | count     | Integer                                                                                      | Number of data records |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | scores    | Array of :ref:`TechScoreVo <getqualityreporttechnologyscores__response_techscorevo>` objects | Returned score list    |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+

.. _getqualityreporttechnologyscores__response_techscorevo:

.. table:: **Table 5** TechScoreVo

   ===================== ====== =====================
   Parameter             Type   Description
   ===================== ====== =====================
   data_connection_id    String Data connection ID
   data_connection_name  String Data connection name
   database_name         String Database name
   table_name            String Table name
   data_connection_score Double Data connection score
   database_score        Double Database score
   table_score           Double Table score
   ===================== ====== =====================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | error_code | String | Error code, for example, **DQC.0000** which indicates that the request was successfully processed |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                                     |
   +------------+--------+---------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | error_code | String | Error code, for example, **DQC.0000** which indicates that the request was successfully processed |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                                     |
   +------------+--------+---------------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET /v2/0833a5737480d53b2f25c010dc1a7b88/quality/report/technology/scores

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "count" : 1,
     "scores" : [ {
       "data_connection_id" : "2d9dcb2076b34bbab1c675f070d6af9d",
       "data_connection_name" : "dws",
       "data_connection_score" : 65.0,
       "database_name" : "postgres",
       "database_score" : 65.0,
       "table_name" : "public.test",
       "table_score" : 0.0
     } ]
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Success
400         BadRequest
500         INTERNAL SERVER ERROR
=========== =====================
