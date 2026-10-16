:original_name: CreateLineageInfo.html

.. _CreateLineageInfo:

Creating a Lineage
==================

Function
--------

This API is used to create a lineage.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/lineage/lineage-info

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                      |
   +==============+===========+========+==================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory if :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                              |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | Parameter        | Mandatory | Type                                                                     | Description          |
   +==================+===========+==========================================================================+======================+
   | cluster_id       | No        | String                                                                   | Cluster ID           |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | data_source_type | No        | String                                                                   | Data connection type |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | connection_id    | No        | String                                                                   | Data connection ID   |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | connection_name  | No        | String                                                                   | Data connection name |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | workspace_id     | No        | String                                                                   | Workspace ID         |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | job_id           | No        | String                                                                   | Job ID               |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | node_name        | No        | String                                                                   | Operator name        |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+
   | table_lineage    | No        | :ref:`TableLineageV2 <createlineageinfo__request_tablelineagev2>` object | Lineage              |
   +------------------+-----------+--------------------------------------------------------------------------+----------------------+

.. _createlineageinfo__request_tablelineagev2:

.. table:: **Table 4** TableLineageV2

   +-----------------+-----------+--------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | Parameter       | Mandatory | Type                                                                                 | Description                                                        |
   +=================+===========+======================================================================================+====================================================================+
   | input_tables    | Yes       | Array of :ref:`TableInfoV2 <createlineageinfo__request_tableinfov2>` objects         | Upstream lineage table list. The list size ranges from 1 to 100.   |
   +-----------------+-----------+--------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | output_tables   | Yes       | Array of :ref:`TableInfoV2 <createlineageinfo__request_tableinfov2>` objects         | Downstream lineage table list. The list size ranges from 1 to 100. |
   +-----------------+-----------+--------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | column_lineages | No        | Array of :ref:`ColumnLineageV2 <createlineageinfo__request_columnlineagev2>` objects | Field lineage list. The list size ranges from 0 to 100.            |
   +-----------------+-----------+--------------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. _createlineageinfo__request_tableinfov2:

.. table:: **Table 5** TableInfoV2

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   catalog   No        String Catalog name
   database  No        String Database name
   schema    No        String Schema name
   table     No        String Table name
   ========= ========= ====== =============

.. _createlineageinfo__request_columnlineagev2:

.. table:: **Table 6** ColumnLineageV2

   +----------------+-----------+----------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | Parameter      | Mandatory | Type                                                                             | Description                                                        |
   +================+===========+==================================================================================+====================================================================+
   | input_columns  | Yes       | Array of :ref:`ColumnDetails <createlineageinfo__request_columndetails>` objects | Upstream lineage field list. The list size ranges from 1 to 100.   |
   +----------------+-----------+----------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | output_columns | Yes       | Array of :ref:`ColumnDetails <createlineageinfo__request_columndetails>` objects | Downstream lineage field list. The list size ranges from 1 to 100. |
   +----------------+-----------+----------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. _createlineageinfo__request_columndetails:

.. table:: **Table 7** ColumnDetails

   ========= ========= ====== ==========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==========================
   database  No        String Database name
   schema    No        String Schema name
   table     No        String Table name
   column    No        String Specifies the column name.
   ========= ========= ====== ==========================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 8** Response body parameters

   +-----------+---------------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                            | Description           |
   +===========+=================================================================================+=======================+
   | [items]   | Array of :ref:`ObjectIdInfo <createlineageinfo__response_objectidinfo>` objects | Lineage Import Result |
   +-----------+---------------------------------------------------------------------------------+-----------------------+

.. _createlineageinfo__response_objectidinfo:

.. table:: **Table 9** ObjectIdInfo

   ============== ====== =======================================
   Parameter      Type   Description
   ============== ====== =======================================
   name           String Name of a job operator.
   type_name      String Asset type.
   qualified_name String Uniquely qualified name of a job asset.
   ============== ====== =======================================

**Status code: 400**

.. table:: **Table 10** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 11** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 12** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 13** Response body parameters

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
     "cluster_id" : "actual_cluster_id",
     "data_source_type" : "actual_data_source_type",
     "connection_id" : "003b3ed52daf41e6829a0bc74526f5f7",
     "connection_name" : "dli_test",
     "workspace_id" : "1b59d3c777ad4d619b89eeac4f3cce87",
     "job_id" : "testJobID",
     "node_name" : "testNodeMName",
     "table_lineage" : {
       "input_tables" : [ {
         "catalog" : "spark_catalog",
         "database" : "nbbtemp",
         "schema" : "",
         "table" : "origndata_typeall"
       } ],
       "output_tables" : [ {
         "catalog" : "spark_catalog",
         "database" : "nbbtemp",
         "schema" : "",
         "table" : "lineageTable1"
       } ],
       "column_lineages" : [ {
         "input_columns" : [ {
           "database" : "nbbtemp",
           "schema" : "",
           "table" : "origndata_typeall",
           "column" : "stringf"
         } ],
         "output_columns" : [ {
           "database" : "nbbtemp",
           "schema" : "",
           "table" : "lineageTable1",
           "column" : "col1"
         } ]
       } ]
     }
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   [ {
     "name" : "test",
     "type_name" : "Node",
     "qualified_name" : "manual.a0683065-cfb6-42d3-a0ff-87b2cc5e3c79@node.0833a5737480d53b2f25c010dc1a7b88-workspace-ee119e8faee347a389e8c295b926331c"
   } ]

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
400         BadRequest
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============
