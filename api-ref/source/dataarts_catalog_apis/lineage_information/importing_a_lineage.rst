:original_name: ImportLineage.html

.. _ImportLineage:

Importing a Lineage
===================

Function
--------

Lineage query.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/lineage/import

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

   +-----------+-----------+----------------------------------------------------------------------------+---------------------------+
   | Parameter | Mandatory | Type                                                                       | Description               |
   +===========+===========+============================================================================+===========================+
   | [items]   | Yes       | Array of :ref:`TableLineage <importlineage__request_tablelineage>` objects | Lineage information list. |
   +-----------+-----------+----------------------------------------------------------------------------+---------------------------+

.. _importlineage__request_tablelineage:

.. table:: **Table 4** TableLineage

   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | Parameter            | Mandatory | Type                                                                         | Description                                                        |
   +======================+===========+==============================================================================+====================================================================+
   | name                 | Yes       | String                                                                       | Name of a job operator.                                            |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | input_tables         | Yes       | Array of :ref:`TableInfo <importlineage__request_tableinfo>` objects         | Upstream lineage table list. The list size ranges from 1 to 100.   |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | output_tables        | Yes       | Array of :ref:`TableInfo <importlineage__request_tableinfo>` objects         | Downstream lineage table list. The list size ranges from 1 to 100. |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | source_connection_id | Yes       | String                                                                       | Source data connection ID.                                         |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | target_connection_id | No        | String                                                                       | ID of the target data connection.                                  |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | column_lineages      | No        | Array of :ref:`ColumnLineage <importlineage__request_columnlineage>` objects | Field lineage list. The list size ranges from 0 to 100.            |
   +----------------------+-----------+------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. _importlineage__request_tableinfo:

.. table:: **Table 5** TableInfo

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   database  No        String Database name
   schema    No        String Schema name
   table     No        String Table name
   ========= ========= ====== =============

.. _importlineage__request_columnlineage:

.. table:: **Table 6** ColumnLineage

   +----------------+-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type                                                                         | Description                                                            |
   +================+===========+==============================================================================+========================================================================+
   | name           | Yes       | String                                                                       | Name of a job operator.                                                |
   +----------------+-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | input_columns  | Yes       | Array of :ref:`ColumnDetails <importlineage__request_columndetails>` objects | List of upstream lineage fields. The list size ranges from 1 to 100.   |
   +----------------+-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | output_columns | Yes       | Array of :ref:`ColumnDetails <importlineage__request_columndetails>` objects | List of downstream lineage fields. The list size ranges from 1 to 100. |
   +----------------+-----------+------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _importlineage__request_columndetails:

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

   +-----------+-----------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                        | Description           |
   +===========+=============================================================================+=======================+
   | [items]   | Array of :ref:`ObjectIdInfo <importlineage__response_objectidinfo>` objects | Lineage Import Result |
   +-----------+-----------------------------------------------------------------------------+-----------------------+

.. _importlineage__response_objectidinfo:

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

   [ {
     "name" : "test1221",
     "input_tables" : [ {
       "database" : "wk",
       "schema" : null,
       "table" : "wk_test1"
     } ],
     "output_tables" : [ {
       "database" : "wk",
       "schema" : null,
       "table" : "wk_test2"
     } ],
     "source_connection_id" : "aa0e89b9c7c14a6b9737d56a53d7a286",
     "target_connection_id" : "aa0e89b9c7c14a6b9737d56a53d7a286",
     "column_lineages" : [ ]
   } ]

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   [ {
     "name" : "test",
     "type_name" : "Node",
     "qualified_name" : "manual.a0683065-cfb6-42d3-a0ff-87b2cc5e3c79@node.0833a5737480d53b2f25c010dc1a7b88-workspace-ee119e8faee347a389e8c295b926331c"
   } ]

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
