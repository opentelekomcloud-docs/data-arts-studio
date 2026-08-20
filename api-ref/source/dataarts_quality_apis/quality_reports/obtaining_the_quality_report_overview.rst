:original_name: GetQualityReportOverview.html

.. _GetQualityReportOverview:

Obtaining the Quality Report Overview
=====================================

Function
--------

This API is used to obtain the quality report overview.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/quality/report/overview

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

   +-----------+----------------------------------------------------------------------------------------+---------------------------+
   | Parameter | Type                                                                                   | Description               |
   +===========+========================================================================================+===========================+
   | score     | Double                                                                                 | Total score               |
   +-----------+----------------------------------------------------------------------------------------+---------------------------+
   | ranges    | Array of :ref:`ScoreRangeVO <getqualityreportoverview__response_scorerangevo>` objects | List and number of ranges |
   +-----------+----------------------------------------------------------------------------------------+---------------------------+

.. _getqualityreportoverview__response_scorerangevo:

.. table:: **Table 5** ScoreRangeVO

   ========= ======= ===========
   Parameter Type    Description
   ========= ======= ===========
   count     Integer Quantity
   name      String  Range name
   ========= ======= ===========

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

   GET /v2/0833a5737480d53b2f25c010dc1a7b88/quality/report/overview?data_connection_id=2d9dcb2076b34bbab1c675f070d6af9d&quality_score_dimension=technology

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "score" : 56.75,
     "ranges" : [ {
       "count" : 9,
       "name" : "80-100"
     }, {
       "count" : 2,
       "name" : "60-80"
     }, {
       "count" : 2,
       "name" : "40-60"
     }, {
       "count" : 6,
       "name" : "0-20"
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
