:original_name: SearchDesignSqlDdl.html

.. _SearchDesignSqlDdl:

Previewing SQL Statements
=========================

Function
--------

This API is used to preview SQL statements.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/design/table/{tb_id}/ddl

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | tb_id      | Yes       | String | Table ID/Indicator ID                                                                                                   |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +============+===========+========+==============================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | biz_type   | No        | String | Table models: **TABLE_MODEL** for basic tables (default), **DIMENSION_LOGIC_TABLE** for dimension tables, **FACT_LOGIC_TABLE** for fact tables, and **AGGREGATION_LOGIC_TABLE** for summary tables; metric models: **DERIVATIVE_INDEX** for derivative models and **COMPOUND_METRIC** for compound models. This parameter is optional for the default **TABLE_MODEL** (basic tables) and mandatory for other table models and metric models. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | No        | String | ID of the version to be queried.                                                                                                                                                                                                                                                                                                                                                                                                             |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type       | No        | String | Query type. The value can be **DDL** (table), **MAPPING** (mapping), or **METRIC** (metric). This parameter is optional for table models and mandatory for metric models.                                                                                                                                                                                                                                                                    |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header).                                  |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This field is mandatory for authentication using tokens.                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace       | Yes             | String          | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Project-Id    | No              | String          | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                            |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is mandatory for API requests that use AK/SK authentication in multi-project scenarios.                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Default value: application/json;charset=UTF-8                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is optional. If the body is available, this parameter is mandatory. If the body is unavailable, you do not need to set this parameter or verify it. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+--------------------------------------------------------+---------------------------------+
   | Parameter | Type                                                   | Description                     |
   +===========+========================================================+=================================+
   | data      | :ref:`data <searchdesignsqlddl__response_data>` object | Data returned by the interface. |
   +-----------+--------------------------------------------------------+---------------------------------+

.. _searchdesignsqlddl__response_data:

.. table:: **Table 5** data

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   value     String SQL information.
   ========= ====== ================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 7** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

**Status code: 403**

.. table:: **Table 8** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

Example Requests
----------------

Obtain the SQL information whose indicator ID is 1349071612426813440, indicator model is DERIVATIVE_INDEX, and query type is METRIC.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/design/table/1349071612426813440/ddl?biz_type=DERIVATIVE_INDEX&type=METRIC

Example Responses
-----------------

**Status code: 200**

The operation is successful, and the returned data is DDL.

.. code-block::

   {
     "data" : {
       "value" : "SELECT\n    count(fact_test_d_l.pt)  AS test_d_l,\n    fact_test_d_l.pt AS fact_test_d_l_pt,\n    dim_start_node.node_code AS dim_start_node_node_code,\n    dim_end_node.node_code AS dim_end_node_node_code\nFROM  bi.fact_test_d_l fact_test_d_l\n    LEFT JOIN bi.dim_exiu dim_end_node ON  dim_end_node.node_code = fact_test_d_l.end_node_code\n    LEFT JOIN bi.dim_exiu dim_start_node ON  dim_start_node.node_code = fact_test_d_l.start_node_code\nWHERE  1=1\nGROUP BY\n    fact_test_d_l.pt,\n    dim_start_node.node_code,\n    dim_end_node.node_code;"
     }
   }

**Status code: 400**

BadRequest

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The user request is illegal."
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "User authentication failed."
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The user does not have permission to call this API."
   }

Status Codes
------------

=========== ==========================================================
Status Code Description
=========== ==========================================================
200         The operation is successful, and the returned data is DDL.
400         BadRequest
401         Unauthorized
403         Forbidden
=========== ==========================================================
