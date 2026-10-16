:original_name: ShowLineage.html

.. _ShowLineage:

Querying Lineages
=================

Function
--------

Lineage query.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/entities/{guid}/lineage

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                      |
   +============+===========+========+==================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`.      |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | guid       | Yes       | String | Asset GUID. For details about how to obtain the asset GUID, see :ref:`Data Asset GUID <dataartsstudio_02_0351>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                    |
   +===========+===========+=========+================================================================================================+
   | direction | No        | String  | Query direction. The value can be **BOTH**, **IN**, or **OUT**. The default value is **BOTH**. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------+
   | depth     | No        | Integer | Lineage link length. The default value is 5.                                                   |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------+

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

   +-------------------+---------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type                                                                            | Description                                                                                                                          |
   +===================+=================================================================================+======================================================================================================================================+
   | base_entity_guid  | String                                                                          | GUID of the current asset.                                                                                                           |
   +-------------------+---------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | guid_entity_map   | Object                                                                          | Entity set, which is Map (String, OpenEntityHeader). The key is the asset GUID, and value is the asset information OpenEntityHeader. |
   +-------------------+---------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | relations         | Array of :ref:`LineageRelation <showlineage__response_lineagerelation>` objects | Lineage.                                                                                                                             |
   +-------------------+---------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | referred_entities | Object                                                                          | Related entity set, which is Map(String, OpenEntity). The key is the asset GUID, and value is the asset information OpenEntity.      |
   +-------------------+---------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _showlineage__response_lineagerelation:

.. table:: **Table 5** LineageRelation

   =============== ====== ================================
   Parameter       Type   Description
   =============== ====== ================================
   from_entity_id  String Lineage source asset GUID.
   relationship_id String Relationship ID.
   to_entity_id    String Lineage flows to the asset guid.
   =============== ====== ================================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 9** Response body parameters

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

OK.

.. code-block::

   {
     "base_entity_guid" : "c1cba918-24d3-4dc4-a65c-178e57b14458",
     "guid_entity_map" : {
       "c1cba918-24d3-4dc4-a65c-178e57b14458" : {
         "attributes" : {
           "owner" : "userName",
           "create_time" : 0,
           "qualified_name" : "MRS_Flink_Job_001.flink_01@FLINK.f9a70740-6a5e-492a-a369-9779fd952f85.0833a5737480d53b2f25c010dc1a7b88-workspace              -b88c445407b24283aa949f9833a38fd8",
           "name" : "flink_01",
           "description" : "This temp entity was generated from DLF lineage service",
           "security_level" : null
         },
         "classification_names" : [ ],
         "connection" : null,
         "display_text" : "flink_01",
         "guid" : "c1cba918-24d3-4dc4-a65c-178e57b14458",
         "tags" : [ ],
         "type_name" : "flink_table"
       },
       "223d0579-cf6f-4439-950b-7372a0f1a5a2" : {
         "attributes" : {
           "owner" : "userName",
           "create_time" : 0,
           "qualified_name" : "MRS_Flink_Job_001.flink_02@FLINK.f9a70740-6a5e-492a-a369-9779fd952f85.0833a5737480d53b2f25c010dc1a7b88-workspace              -b88c445407b24283aa949f9833a38fd8",
           "name" : "flink_02",
           "description" : "This temp entity was generated from DLF lineage service",
           "security_level" : null
         },
         "classification_names" : [ ],
         "connection" : null,
         "display_text" : "flink_02",
         "guid" : "223d0579-cf6f-4439-950b-7372a0f1a5a2",
         "tags" : [ ],
         "type_name" : "flink_table"
       },
       "e2f63e6a-206d-4090-a032-7e038d507269" : {
         "attributes" : {
           "owner" : "userName",
           "outputs" : [ {
             "uniqueAttributes" : {
               "qualifiedName" : "MRS_Flink_Job_001.flink_01@FLINK.f9a70740-6a5e-492a-a369-9779fd952f85.0833a5737480d53b2f25c010dc1a7b88-workspace              -b88c445407b24283aa949f9833a38fd8"
             },
             "typeName" : "flink_table",
             "name" : "flink_01",
             "guid" : "c1cba918-24d3-4dc4-a65c-178e57b14458"
           } ],
           "create_time" : null,
           "qualified_name" : "509207.42419233-b3f5-42b3-a314-336132c23328@dlf_job.0833a5737480d53b2f25c010dc1a7b88-workspace              -1b59d3c777ad4d619b89eeac4f3cce87",
           "inputs" : [ {
             "uniqueAttributes" : {
               "qualifiedName" : "MRS_Flink_Job_001.flink_02@FLINK.f9a70740-6a5e-492a-a369-9779fd952f85.0833a5737480d53b2f25c010dc1a7b88-workspace              -b88c445407b24283aa949f9833a38fd8"
             },
             "typeName" : "flink_table",
             "name" : "flink_02",
             "guid" : "223d0579-cf6f-4439-950b-7372a0f1a5a2"
           } ],
           "name" : "MRS_Flink_Job_001",
           "description" : "Workspace: kw_test",
           "security_level" : "l1"
         },
         "classification_names" : [ ],
         "connection" : null,
         "display_text" : "MRS_Flink_Job_001",
         "guid" : "e2f63e6a-206d-4090-a032-7e038d507269",
         "tags" : [ ],
         "type_name" : "flink_node"
       }
     },
     "referred_entities" : { },
     "relations" : [ {
       "from_entity_id" : "e2f63e6a-206d-4090-a032-7e038d507269",
       "relationship_id" : "b5ec94b0-e779-49a8-adef-f6bbf46bf63c",
       "to_entity_id" : "c1cba918-24d3-4dc4-a65c-178e57b14458"
     }, {
       "from_entity_id" : "223d0579-cf6f-4439-950b-7372a0f1a5a2",
       "relationship_id" : "7a1b8777-3bd9-460a-b729-70d3d3bf3744",
       "to_entity_id" : "e2f63e6a-206d-4090-a032-7e038d507269"
     } ]
   }

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         OK.
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
=========== =============
