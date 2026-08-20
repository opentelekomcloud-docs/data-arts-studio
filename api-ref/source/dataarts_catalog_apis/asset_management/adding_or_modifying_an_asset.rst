:original_name: CreateOrUpdateAsset.html

.. _CreateOrUpdateAsset:

Adding or Modifying an Asset
============================

Function
--------

Add or modify an asset.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/asset

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------+-----------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type                                                                           | Description                                                                                              |
   +===================+===========+================================================================================+==========================================================================================================+
   | entity            | Yes       | :ref:`AtlasAssetEntity <createorupdateasset__request_atlasassetentity>` object | Asset information.                                                                                       |
   +-------------------+-----------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | referred_entities | No        | Object                                                                         | Associated asset map Map(String, AtlasAssetEntity). The key is guid, and the value is asset information. |
   +-------------------+-----------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

.. _createorupdateasset__request_atlasassetentity:

.. table:: **Table 4** AtlasAssetEntity

   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type                                                                                                   | Description                                                                                                      |
   +==========================+===========+========================================================================================================+==================================================================================================================+
   | type_name                | Yes       | String                                                                                                 | Type name.                                                                                                       |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | guid                     | No        | String                                                                                                 | Asset GUID.                                                                                                      |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | version                  | No        | Integer                                                                                                | Version                                                                                                          |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | update_time              | No        | Number                                                                                                 | Modification time.                                                                                               |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | update_user              | No        | String                                                                                                 | User who makes a modification.                                                                                   |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | create_time              | No        | Number                                                                                                 | Creation time.                                                                                                   |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | create_user              | No        | String                                                                                                 | Creator                                                                                                          |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | display_text             | No        | String                                                                                                 | recommendation                                                                                                   |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | status                   | No        | String                                                                                                 | Status                                                                                                           |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | classifications          | No        | Array of :ref:`AtlasClassificationInfo <createorupdateasset__request_atlasclassificationinfo>` objects | Category information.                                                                                            |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | meanings                 | No        | Array of :ref:`TermAssignmentHeader <createorupdateasset__request_termassignmentheader>` objects       | Associate a task.                                                                                                |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | relation_ship_attributes | No        | Object                                                                                                 | Entity map Map(String, Object). key: association relationship type. value: association relationship information. |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | attributes               | Yes       | Object                                                                                                 | Entity map Map(String, Object). key: attribute name; value: attribute value.                                     |
   +--------------------------+-----------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+

.. _createorupdateasset__request_atlasclassificationinfo:

.. table:: **Table 5** AtlasClassificationInfo

   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type                                                                             | Description                                                                  |
   +==================+===========+==================================================================================+==============================================================================+
   | entity_guid      | No        | String                                                                           | Asset GUID.                                                                  |
   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | propagate        | No        | Boolean                                                                          | Indicates whether to propagate.                                              |
   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | validity_periods | No        | Array of :ref:`TimeBoundary <createorupdateasset__request_timeboundary>` objects | Time information.                                                            |
   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | type_name        | No        | String                                                                           | Type name.                                                                   |
   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | attributes       | No        | Object                                                                           | Entity map Map(String, Object). key: attribute name; value: attribute value. |
   +------------------+-----------+----------------------------------------------------------------------------------+------------------------------------------------------------------------------+

.. _createorupdateasset__request_timeboundary:

.. table:: **Table 6** TimeBoundary

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   start_time No        String Start time.
   end_time   No        String End time.
   time_zone  No        String Time zone.
   ========== ========= ====== ===========

.. _createorupdateasset__request_termassignmentheader:

.. table:: **Table 7** TermAssignmentHeader

   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type    | Description                                                                                   |
   +===============+===========+=========+===============================================================================================+
   | confidence    | No        | Integer | Trust ID.                                                                                     |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | steward       | No        | String  | Administrator                                                                                 |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | source        | No        | String  | Source.                                                                                       |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | status        | No        | String  | Enumerated values: DISCOVERED, PROPOSED, IMPORTED, VALIDATED, DEPRECATED, OBSOLETE and OTHER. |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | create_user   | No        | String  | Creator                                                                                       |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | expression    | No        | String  | Expression.                                                                                   |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | display_text  | No        | String  | Display information                                                                           |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | term_guid     | No        | String  | Tag GUID                                                                                      |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+
   | relation_guid | No        | String  | Associated GUID                                                                               |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 10** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 11** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 500**

.. table:: **Table 12** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

.. code-block::

   {
     "entity" : {
       "attributes" : {
         "owner" : null,
         "comments" : null,
         "qualifiedName" : "postgres.dm_autotest.test.dqc_create_timestamp@dws.dws-4autotest-nomodify.dws-dws_4autotest_nomodify.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87",
         "isPartitionColumn" : false,
         "description" : null,
         "isPrimaryKey" : false,
         "type" : "bigint",
         "ordinalPosition" : 6,
         "connectionType" : "dws",
         "securityLevel" : null,
         "connectionQName" : "dws@dws-4autotest-nomodify.dws-dws_4autotest_nomodify.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87",
         "isNullable" : "true",
         "name" : "dqc_create_timestamp",
         "connectionId" : "null:8a94806e79e693a30179e972c4aa000c",
         "alias" : null,
         "table" : {
           "uniqueAttributes" : {
             "qualifiedName" : "postgres.dm_autotest.test@dws.dws-4autotest-nomodify.dws-dws_4autotest_nomodify.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87"
           },
           "typeName" : "dws_table",
           "name" : "test",
           "guid" : "bc9af691-3401-4a7e-959f-413359dafeb6"
         }
       },
       "classifications" : null,
       "create_time" : 1662567796444,
       "create_user" : "user_demo",
       "display_text" : "dqc_create_timestamp",
       "guid" : "266b1194-1713-47c9-94be-fdac82023f2f",
       "meanings" : null,
       "relation_ship_attributes" : {
         "inputToProcesses" : [ ],
         "meanings" : [ ],
         "table" : {
           "relationshipAttributes" : {
             "typeName" : "dws_table_column"
           },
           "displayText" : "test",
           "relationshipGuid" : "f78811cb-0dd8-4459-8fda-54ca44d66005",
           "typeName" : "dws_table",
           "guid" : "bc9af691-3401-4a7e-959f-413359dafeb6",
           "relationshipStatus" : "ACTIVE"
         },
         "outputFromProcesses" : [ ]
       },
       "status" : "ACTIVE",
       "type_name" : "dws_column",
       "update_time" : 1662567796444,
       "update_user" : "user_demo",
       "version" : 0
     },
     "referred_entities" : {
       "dws@dws-4autotest-nomodify.dws-dws_4autotest_nomodify.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87" : {
         "attributes" : {
           "owner" : "user_demo",
           "securityLevel" : null,
           "createTime" : 0,
           "port" : 8000,
           "qualifiedName" : "dws@dws-4autotest-nomodify.dws-dws_4autotest_nomodify.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87",
           "name" : "dws_test",
           "host" : null,
           "description" : null,
           "id" : "8a94806e79e693a30179e972c4aa000c",
           "connectionType" : "dws"
         },
         "classifications" : null,
         "create_time" : 1665641601524,
         "create_user" : "user_demo",
         "display_text" : "dws_test",
         "guid" : "46bdc502-7912-460f-9d67-15141e9ab096",
         "meanings" : null,
         "relation_ship_attributes" : {
           "meanings" : [ ]
         },
         "status" : "ACTIVE",
         "type_name" : "Connection",
         "update_time" : 1669914264150,
         "update_user" : "user_demo",
         "version" : 0
       }
     }
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ====================
Status Code Description
=========== ====================
200         OK.
400         Bad Request:
401         Unauthorized:
403         Forbidden.
404         Not found.
500         InternalServerError.
=========== ====================
