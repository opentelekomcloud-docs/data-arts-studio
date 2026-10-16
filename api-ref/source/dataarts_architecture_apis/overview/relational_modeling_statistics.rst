:original_name: CountAllModels.html

.. _CountAllModels:

Relational Modeling Statistics
==============================

Function
--------

Outer-layer statistics on the relational modeling page.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/models/statistic

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                               | Description                                                    |
   +===========+====================================================+================================================================+
   | data      | :ref:`data <countallmodels__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+----------------------------------------------------+----------------------------------------------------------------+

.. _countallmodels__response_data:

.. table:: **Table 4** data

   +-----------+----------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter | Type                                                                             | Description                                                 |
   +===========+==================================================================================+=============================================================+
   | value     | :ref:`AllModelStatisticVO <countallmodels__response_allmodelstatisticvo>` object | value: unified outer data structure of the returned result. |
   +-----------+----------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _countallmodels__response_allmodelstatisticvo:

.. table:: **Table 5** AllModelStatisticVO

   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | Parameter | Type                                                                                 | Description                            |
   +===========+======================================================================================+========================================+
   | frequent  | Array of :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` objects | Indicates whether it is commonly used. |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | top       | Array of :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` objects | First-layer model.                     |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | logic     | Array of :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` objects | Logical model.                         |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | physical  | Array of :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` objects | Physical model.                        |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | dwr       | :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` object           | DWR data reporting layer.              |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+
   | dm        | :ref:`ModelStatisticVO <countallmodels__response_modelstatisticvo>` object           | DM data integration layer.             |
   +-----------+--------------------------------------------------------------------------------------+----------------------------------------+

.. _countallmodels__response_modelstatisticvo:

.. table:: **Table 6** ModelStatisticVO

   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | Parameter             | Type                                                             | Description                                                                           |
   +=======================+==================================================================+=======================================================================================+
   | biz_type              | String                                                           | Business entity type.                                                                 |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | Options:                                                                              |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  AGGREGATION_LOGIC_TABLE: summary table                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  ATOMIC_INDEX: atomic metric                                                        |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  ATOMIC_METRIC: atomic metric (new)                                                 |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  BIZ_CATALOG: process architecture directory                                        |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  BIZ_METRIC: service indicator                                                      |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  CODE_TABLE: code table                                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  COMMON_CONDITION: general filter                                                   |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  COMPOSITE_METRIC: Compound Metric (new)                                            |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  COMPOUND_METRIC: compound metric                                                   |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  CONDITION_GROUP: restriction group                                                 |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DEGENERATE_DIMENSION: degenerate dimension                                         |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DERIVATIVE_INDEX: derivative indicator                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DERIVED_METRIC: derivative indicator (new)                                         |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIMENSION: dimension                                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIMENSION_ATTRIBUTE: dimension attribute                                           |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIMENSION_HIERARCHIES: dimension level                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIMENSION_LOGIC_TABLE: dimension table                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIMENSION_TABLE_ATTRIBUTE: dimension attribute                                     |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DIRECTORY: directory                                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  FACT_ATTRIBUTE: fact table attribute                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  FACT_DIMENSION: fact table dimension                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  FACT_LOGIC_TABLE: fact table                                                       |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  FACT_MEASURE: fact table measurement                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  FUNCTION: function                                                                 |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  INFO_ARCH: information architecture (used for modifying themes in batches)         |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  MODEL: model                                                                       |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  QUALITY_RULE: quality rule                                                         |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  SECRECY_LEVEL: security level                                                      |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  STANDARD_ELEMENT: data standard                                                    |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  STANDARD_ELEMENT_TEMPLATE: data standard template                                  |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  SUBJECT: theme                                                                     |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  Dimension attributes of SUMMARY_DIMENSION_ATTRIBUTE: summary tables                |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  SUMMARY_INDEX: summary table indicator attribute                                   |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  SUMMARY_TIME: time period attribute of the SDR table                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TABLE_MODEL: relationship model (logical model/physical model)                     |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TABLE_MODEL_ATTRIBUTE: relationship model attribute (logical model/physical model) |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TABLE_MODEL_LOGIC: logical entity                                                  |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TABLE_TYPE: table type                                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TAG: tag                                                                           |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  TIME_CONDITION: time restriction                                                   |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | level                 | String                                                           | Data governance layers.                                                               |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | Options:                                                                              |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  SDI: source data layer                                                             |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DWI: data integration layer                                                        |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DWR: data reporting layer                                                          |
   |                       |                                                                  |                                                                                       |
   |                       |                                                                  | -  DM: data mart layer                                                                |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | db                    | Integer                                                          | Indicates the database.                                                               |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | tb                    | Integer                                                          | Data table.                                                                           |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | tb_published          | Integer                                                          | Released data table.                                                                  |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | fd                    | Integer                                                          | Field.                                                                                |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | fd_published          | Integer                                                          | Published field.                                                                      |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | st                    | Double                                                           | Standard coverage.                                                                    |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | st_published          | Double                                                           | Coverage of released standards.                                                       |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+
   | model                 | :ref:`WorkspaceVO <countallmodels__response_workspacevo>` object | Model information                                                                     |
   +-----------------------+------------------------------------------------------------------+---------------------------------------------------------------------------------------+

.. _countallmodels__response_workspacevo:

.. table:: **Table 7** WorkspaceVO

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                       |
   +=======================+=======================+===================================================================================================================================================================================================================================+
   | id                    | String                | ID, which is a string                                                                                                                                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Name of the workspace.                                                                                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description.                                                                                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_physical           | Boolean               | Indicates whether a table is a physical table.                                                                                                                                                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | frequent              | Boolean               | Indicates whether it is commonly used.                                                                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | top                   | Boolean               | Hierarchical governance.                                                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | level                 | String                | Data governance layers.                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | Options:                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  SDI: source data layer                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  DWI: data integration layer                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  DWR: data reporting layer                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  DM: data mart layer                                                                                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dw_type               | String                | Data connection type, which corresponds to the type of the data warehouse where the table is located. The value can be **DWS**, **MRS_HIVE**, **POSTGRESQL**, **MRS_SPARK**, **CLICKHOUSE**, **MYSQL**, **ORACLE**, or **DORIS**. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by             | String                | Creator.                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_by             | String                | Person who updates the information.                                                                                                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Defines the workspace type enumeration.                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | Options:                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  THIRD_NF: relational modeling                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                   |
   |                       |                       | -  DIMENSION: dimensional modeling                                                                                                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_catalog_ids       | String                | {"l1Ids":[],"l2Ids":[],"l3Ids":[]}: ID list of associated service catalogs.                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | databases             | Array of strings      | Array of database names.                                                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | table_model_prefix    | String                | Model verification prefix. The value contains a maximum of 100 characters, including digits, letters, and underscores (_), and starts with a letter.                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

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

**Status code: 401**

.. table:: **Table 9** Response body parameters

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

.. table:: **Table 10** Response body parameters

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

Relational modeling statistics.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/models/statistic

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is AllModelStatisticVO.

.. code-block::

   {
     "data" : {
       "value" : {
         "frequent" : null,
         "top" : [ {
           "biz_type" : "TABLE_MODEL",
           "level" : "SDI",
           "db" : 2,
           "tb" : 14,
           "tb_published" : 10,
           "fd" : 31,
           "fd_published" : 20,
           "st" : 0.06451612903225806,
           "st_published" : 0.1,
           "model" : {
             "id" : "1183882892003127296",
             "name" : "test_prefix_001",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : true,
             "level" : "SDI",
             "dw_type" : "DWS",
             "create_time" : "2023-12-11T21:27:57+08:00",
             "update_time" : "2024-04-08T19:18:05+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : "test_"
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 0,
           "tb_published" : 0,
           "fd" : 0,
           "fd_published" : 0,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : {
             "id" : "1230823879853875200",
             "name" : "LOGIC_B",
             "description" : "",
             "is_physical" : false,
             "frequent" : false,
             "top" : true,
             "level" : null,
             "dw_type" : "UNSPECIFIED",
             "create_time" : "2024-04-19T10:14:41+08:00",
             "update_time" : "2024-04-19T10:14:41+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           }
         } ],
         "logic" : [ {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 0,
           "tb_published" : 0,
           "fd" : 0,
           "fd_published" : 0,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : {
             "id" : "1230823879853875200",
             "name" : "LOGIC_B",
             "description" : "",
             "is_physical" : false,
             "frequent" : false,
             "top" : true,
             "level" : null,
             "dw_type" : "UNSPECIFIED",
             "create_time" : "2024-04-19T10:14:41+08:00",
             "update_time" : "2024-04-19T10:14:41+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 0,
           "tb_published" : 0,
           "fd" : 0,
           "fd_published" : 0,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : {
             "id" : "1230823841513799680",
             "name" : "LOGIC_A",
             "description" : "",
             "is_physical" : false,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "UNSPECIFIED",
             "create_time" : "2024-04-19T10:14:31+08:00",
             "update_time" : "2024-04-19T10:14:31+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 4,
           "tb_published" : 3,
           "fd" : 12,
           "fd_published" : 9,
           "st" : 0.16666666666666666,
           "st_published" : 0.1111111111111111,
           "model" : {
             "id" : "1229432454457262080",
             "name" : "test_czh",
             "description" : "",
             "is_physical" : false,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "UNSPECIFIED",
             "create_time" : "2024-04-15T14:05:39+08:00",
             "update_time" : "2024-04-15T14:05:39+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 11,
           "tb_published" : 10,
           "fd" : 25,
           "fd_published" : 23,
           "st" : 0.04,
           "st_published" : 0.043478260869565216,
           "model" : {
             "id" : "1169318954880122880",
             "name" : "logic_czh",
             "description" : "",
             "is_physical" : false,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "UNSPECIFIED",
             "create_time" : "2023-11-01T16:56:04+08:00",
             "update_time" : "2023-11-01T16:56:04+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : null
           }
         } ],
         "physical" : [ {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 1,
           "tb" : 9,
           "tb_published" : 7,
           "fd" : 34,
           "fd_published" : 20,
           "st" : 0.08823529411764706,
           "st_published" : 0.1,
           "model" : {
             "id" : "1204448983481765888",
             "name" : "test_dws",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "DWS",
             "create_time" : "2024-02-06T15:30:15+08:00",
             "update_time" : "2024-02-06T15:30:15+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : "SDI",
           "db" : 2,
           "tb" : 14,
           "tb_published" : 10,
           "fd" : 31,
           "fd_published" : 20,
           "st" : 0.06451612903225806,
           "st_published" : 0.1,
           "model" : {
             "id" : "1183882892003127296",
             "name" : "test_prefix_001",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : true,
             "level" : "SDI",
             "dw_type" : "DWS",
             "create_time" : "2023-12-11T21:27:57+08:00",
             "update_time" : "2024-04-08T19:18:05+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : "test_"
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 0,
           "tb" : 2,
           "tb_published" : 2,
           "fd" : 4,
           "fd_published" : 4,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : {
             "id" : "1178728794341699584",
             "name" : "dws_czh",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "DWS",
             "create_time" : "2023-11-27T16:07:24+08:00",
             "update_time" : "2024-04-08T19:13:13+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : "test_"
           }
         }, {
           "biz_type" : "TABLE_MODEL",
           "level" : null,
           "db" : 2,
           "tb" : 10,
           "tb_published" : 8,
           "fd" : 36,
           "fd_published" : 32,
           "st" : 0.08333333333333333,
           "st_published" : 0.09375,
           "model" : {
             "id" : "1169319480548048896",
             "name" : "mrs_hive_czh",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : false,
             "level" : null,
             "dw_type" : "MRS_HIVE",
             "create_time" : "2023-11-01T16:58:09+08:00",
             "update_time" : "2023-11-01T16:58:09+08:00",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : null
           }
         } ],
         "dwr" : {
           "biz_type" : "DIMENSION",
           "level" : null,
           "db" : 5,
           "tb" : 24,
           "tb_published" : 21,
           "fd" : 387,
           "fd_published" : 378,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : null
         },
         "dm" : {
           "biz_type" : "AGGREGATION_LOGIC_TABLE",
           "level" : null,
           "db" : 2,
           "tb" : 12,
           "tb_published" : 7,
           "fd" : 77,
           "fd_published" : 35,
           "st" : 0.0,
           "st_published" : 0.0,
           "model" : null
         }
       }
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

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | This operation succeeds, and the returned data is AllModelStatisticVO. |
+-------------+------------------------------------------------------------------------+
| 400         | BadRequest                                                             |
+-------------+------------------------------------------------------------------------+
| 401         | Unauthorized                                                           |
+-------------+------------------------------------------------------------------------+
| 403         | Forbidden                                                              |
+-------------+------------------------------------------------------------------------+
