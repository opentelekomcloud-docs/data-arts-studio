:original_name: ShowBusinessAssetsStatistic.html

.. _ShowBusinessAssetsStatistic:

Obtaining Logical Asset Statistics
==================================

Function
--------

This API is used to obtain service asset statistics.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/asset/statistic/assets/business-assets

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                |
   +===========+===========+=========+============================================================================================================+
   | offset    | No        | Integer | Specifies the query offset. By default, all records are queried. This parameter is a pagination parameter. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+
   | limit     | No        | Integer | Specifies the number of records on each page. By default, all records are queried.                         |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------------------------+-----------------------------------------------------------------------------------------+---------------------------------------+
   | Parameter                     | Type                                                                                    | Description                           |
   +===============================+=========================================================================================+=======================================+
   | count                         | Integer                                                                                 | Total number of subject area groups.  |
   +-------------------------------+-----------------------------------------------------------------------------------------+---------------------------------------+
   | subject_area_group_statistics | Array of :ref:`L1Statistic <showbusinessassetsstatistic__response_l1statistic>` objects | Statistics about subject area groups. |
   +-------------------------------+-----------------------------------------------------------------------------------------+---------------------------------------+

.. _showbusinessassetsstatistic__response_l1statistic:

.. table:: **Table 5** L1Statistic

   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter                  | Type                                                                                    | Description                              |
   +============================+=========================================================================================+==========================================+
   | subject_area_group_name    | String                                                                                  | Name of a subject area group.            |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | subject_area_group_name_en | String                                                                                  | English name of a subject area group.    |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | subject_area_group_guid    | String                                                                                  | GUID of the subject area group.          |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | ordinal                    | Integer                                                                                 | Sequence number of a subject area group. |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | subject_area_count         | Integer                                                                                 | Total number of topics.                  |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | business_object_count      | Integer                                                                                 | Total number of service objects.         |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | logic_entity_count         | Integer                                                                                 | Total number of logical entities.        |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+
   | subject_area_statistics    | Array of :ref:`L2Statistic <showbusinessassetsstatistic__response_l2statistic>` objects | Theme statistics.                        |
   +----------------------------+-----------------------------------------------------------------------------------------+------------------------------------------+

.. _showbusinessassetsstatistic__response_l2statistic:

.. table:: **Table 6** L2Statistic

   ===================== ======= =================================
   Parameter             Type    Description
   ===================== ======= =================================
   subject_area_name     String  Topic name.
   subject_area_guid     String  GUID of the theme.
   ordinal               Integer Topic sequence number.
   business_object_count Integer Total number of service objects.
   logic_entity_count    Integer Total number of logical entities.
   ===================== ======= =================================

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Business assets statistic.

.. code-block::

   {
     "count" : 1,
     "subject_area_group_statistics" : [ {
       "subject_area_group_name" : "subject_area_group",
       "subject_area_group_name_en" : "subject_area_group",
       "subject_area_group_guid" : "ea60986c-7de3-4743-9ae3-2b3d8b030366",
       "ordinal" : 1,
       "subject_area_count" : 1,
       "business_object_count" : 1,
       "logic_entity_count" : 1,
       "subject_area_statistics" : [ {
         "subject_area_name" : "subject_area",
         "subject_area_guid" : "e80d6b75-83a9-40aa-b621-59188690d28a",
         "business_object_count" : 1,
         "logic_entity_count" : 1,
         "ordinal" : 1
       } ]
     } ]
   }

Status Codes
------------

=========== ==========================
Status Code Description
=========== ==========================
200         Business assets statistic.
400         Bad Request:
401         Unauthorized:
403         Forbidden.
404         Not Found
=========== ==========================
