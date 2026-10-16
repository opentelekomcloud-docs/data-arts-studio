:original_name: GetQualityReportScoring.html

.. _GetQualityReportScoring:

Obtaining a Quality Report Scoring System
=========================================

Function
--------

This API is used to obtain the scoring system for quality reports.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/quality/report/scoring

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameters

   ========== ======= ===========
   Parameter  Type    Description
   ========== ======= ===========
   full_score Integer Full score
   ========== ======= ===========

**Status code: 400**

.. table:: **Table 4** Response body parameters

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | error_code | String | Error code, for example, **DQC.0000** which indicates that the request was successfully processed |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                                     |
   +------------+--------+---------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 5** Response body parameters

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

   GET /v2/0833a5737480d53b2f25c010dc1a7b88/quality/report/scoring

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "full_score" : 100
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
