:original_name: ShowBusinessAssetsTree.html

.. _ShowBusinessAssetsTree:

Querying the Logical Asset Directory Tree
=========================================

Function
--------

Queries the service asset directory tree level by level, including service objects and logical entities synchronized from data specifications.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/business-assets/tree/subnode

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                      |
   +===========+===========+========+==================================================================================================================================================================================+
   | guid      | No        | String | Asset GUID. If this parameter is not set, the LV1 service asset is queried. For details about how to obtain the asset GUID, see :ref:`Data Asset GUID <dataartsstudio_02_0351>`. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. _showbusinessassetstree__response_businesscatalogtreenode:

.. table:: **Table 4** Response body parameters

   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter                 | Type                                                                                                       | Description                                         |
   +===========================+============================================================================================================+=====================================================+
   | business_catalog_guid     | String                                                                                                     | GUID of the service asset.                          |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | business_catalog_name     | String                                                                                                     | Name of a service asset.                            |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | business_catalog_name_eng | String                                                                                                     | English name of a service asset.                    |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | level                     | String                                                                                                     | Service asset level.                                |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | qualified_name            | String                                                                                                     | Unique restriction name at the service asset level. |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | ordinal                   | Integer                                                                                                    | Indicates the ordinal number.                       |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | child_nodes               | Array of :ref:`BusinessCatalogTreeNode <showbusinessassetstree__response_businesscatalogtreenode>` objects | List of sub-service assets.                         |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | logic_entity_nodes        | Array of :ref:`LogicEntityNodes <showbusinessassetstree__response_logicentitynodes>` objects               | Logical entity list.                                |
   +---------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+

.. _showbusinessassetstree__response_logicentitynodes:

.. table:: **Table 5** LogicEntityNodes

   ================= ====== ==========================
   Parameter         Type   Description
   ================= ====== ==========================
   logic_entity_guid String GUID of the service asset.
   logic_entity_name String Name of a service asset.
   ================= ====== ==========================

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

Business assets tree.

.. code-block::

   {
     "business_catalog_name" : "ZTY",
     "business_catalog_name_eng" : "ZTY",
     "qualified_name" : "ZTY@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87",
     "logic_entity_nodes" : [ {
       "logic_entity_name" : "luojiyi",
       "logic_entity_guid" : "b8ef87fb-e190-4c10-815e-9b43dae366b2"
     } ],
     "level" : "L1",
     "child_nodes" : [ {
       "business_catalog_name" : "zty_l2",
       "business_catalog_name_eng" : "zty_l2",
       "qualified_name" : "ZTY.zty_l2@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-1b59d3c777ad4d619b89eeac4f3cce87",
       "logic_entity_nodes" : [ ],
       "level" : "L2",
       "child_nodes" : [ ],
       "business_catalog_guid" : "9b5cab1f-be30-47f9-9138-4427e808daa3",
       "ordinal" : 1
     } ],
     "business_catalog_guid" : "5ae65812-d0a6-43a7-876a-c43561e92f3b",
     "ordinal" : 470
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Business assets tree.
400         Bad request.
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== =====================
