:original_name: PostQualityResourceExport.html

.. _PostQualityResourceExport:

Export Resources
================

Function
--------

This API is used to export resources from DataArts Quality, such as quality jobs and comparison jobs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/quality/resource/export

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

.. table:: **Table 3** Request body parameters

   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type           | Description                                                                                                                                                                                                                             |
   +==================+===========+================+=========================================================================================================================================================================================================================================+
   | type             | Yes       | String         | Type of the resources to be exported in batches. **rule-template** indicates quality rule templates, **quality-task** indicates quality jobs, **consistency-task** indicates comparison jobs, and **report** indicates quality reports. |
   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_select_all    | No        | Boolean        | Whether to export all jobs in the current workspace. Value **true** indicates that all jobs are to be exported, and value **false** indicates that not all jobs are to be exported. The default value is **false**.                     |
   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resources        | No        | Array of longs | Resource ID array                                                                                                                                                                                                                       |
   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | export_mode      | No        | String         | Export mode. **null** indicates that data is to be exported to a local file system, and **obs** indicates that data is to be exported to OBS. This parameter is available only for exporting quality reports.                           |
   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_service_type | No        | String         | Service type. Value **technology** indicates a technical report, and value **business** indicates a business report. This parameter is available only for exporting quality reports.                                                    |
   +------------------+-----------+----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   =========== ====== =======================
   Parameter   Type   Description
   =========== ====== =======================
   resource_id String Returned export task ID
   =========== ====== =======================

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

None

Example Responses
-----------------

None

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Success
500         INTERNAL SERVER ERROR
=========== =====================
