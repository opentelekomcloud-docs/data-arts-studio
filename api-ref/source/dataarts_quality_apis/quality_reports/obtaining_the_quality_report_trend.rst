:original_name: GetQualityReportTrend.html

.. _GetQualityReportTrend:

Obtaining the Quality Report Trend
==================================

Function
--------

This API is used to obtain the quality report trend.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/quality/report/trend

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-------------------------+-----------+--------+---------------------------------------------------+
   | Parameter               | Mandatory | Type   | Description                                       |
   +=========================+===========+========+===================================================+
   | quality_score_dimension | Yes       | String | Quality scoring dimension.                        |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | l1                      | No        | String | Subject area group (valid for business reports).  |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | l2                      | No        | String | Subject area (valid for business reports).        |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | l3                      | No        | String | Business object (valid for business reports).     |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | data_connection_id      | No        | String | Data connection ID (valid for technical reports). |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | database_name           | No        | String | Database name (valid for technical reports).      |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | table_name              | No        | String | Data table name (valid for technical reports).    |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | start_timestamp         | No        | Long   | Start timestamp.                                  |
   +-------------------------+-----------+--------+---------------------------------------------------+
   | end_timestamp           | No        | Long   | End timestamp.                                    |
   +-------------------------+-----------+--------+---------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter | Type                                                                                | Description                                                 |
   +===========+=====================================================================================+=============================================================+
   | trends    | Array of :ref:`ScoreTrendVO <getqualityreporttrend__response_scoretrendvo>` objects | **ScoreTrendVO**, which is the array of score change trends |
   +-----------+-------------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _getqualityreporttrend__response_scoretrendvo:

.. table:: **Table 5** ScoreTrendVO

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   score     Double Score
   timestamp String Timestamp
   ========= ====== ===========

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

   GET /v2/0833a5737480d53b2f25c010dc1a7b88/quality/report/trend?data_connection_id=2d9dcb2076b34bbab1c675f070d6af9d&quality_score_dimension=technology

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "trends" : [ {
       "score" : 57.63,
       "timestamp" : "1669132800000"
     }, {
       "score" : 56.92,
       "timestamp" : "1669219200000"
     }, {
       "score" : 60.27,
       "timestamp" : "1669305600000"
     }, {
       "score" : 59.54,
       "timestamp" : "1669392000000"
     }, {
       "score" : 65.07,
       "timestamp" : "1669478400000"
     }, {
       "score" : 57.19,
       "timestamp" : "1669564800000"
     }, {
       "score" : 56.75,
       "timestamp" : "1669651200000"
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
