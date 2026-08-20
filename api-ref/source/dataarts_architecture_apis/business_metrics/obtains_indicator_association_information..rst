:original_name: ListMetricRelations.html

.. _ListMetricRelations:

Obtains indicator association information.
==========================================

Function
--------

This API is used to obtain the current metric graph.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/metric-relations/{id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Entity ID, which is a string                                                                                            |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ====== ============
   Parameter Mandatory Type   Description
   ========= ========= ====== ============
   biz_type  Yes       String Metric type.
   ========= ========= ====== ============

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

   +-----------+---------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                    | Description                                                    |
   +===========+=========================================================+================================================================+
   | data      | :ref:`data <listmetricrelations__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+---------------------------------------------------------+----------------------------------------------------------------+

.. _listmetricrelations__response_data:

.. table:: **Table 5** data

   +-----------+-----------------------------------------------------------+-------------------------------------------------------------+
   | Parameter | Type                                                      | Description                                                 |
   +===========+===========================================================+=============================================================+
   | value     | :ref:`value <listmetricrelations__response_value>` object | value: unified outer data structure of the returned result. |
   +-----------+-----------------------------------------------------------+-------------------------------------------------------------+

.. _listmetricrelations__response_value:

.. table:: **Table 6** value

   ========= ================ =========================================
   Parameter Type             Description
   ========= ================ =========================================
   all       Array of objects Information about all service indicators.
   links     Object           Associate indicators.
   groups    Object           Group.
   total     Integer          Total number.
   ========= ================ =========================================

**Status code: 400**

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

**Status code: 401**

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

**Status code: 403**

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

Example Requests
----------------

This API is used to query the metric graph based on the metric ID.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/metric-relations/1193199235202428928?biz_type=BIZ_METRIC

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is MetricRelationVOList.

.. code-block::

   {
     "data" : {
       "value" : {
         "all" : [ {
           "vo" : {
             "id" : "1014197025488699392",
             "name_en" : "zonghe8830",
             "name_ch" : "zonghe8830(testweidu830)",
             "description" : "",
             "create_by" : "abc",
             "data_type" : "STRING",
             "l1_id" : null,
             "l2_id" : null,
             "l3_id" : "767858832738234368",
             "status" : "DRAFT",
             "atomic_index_id" : "1014195214723756032",
             "time_condition_id" : null,
             "time_field_id" : null,
             "time_field_name" : null,
             "common_conditions" : [ ],
             "dimension_groups" : [ {
               "group_id" : "1014194851576721408",
               "role" : null,
               "dimension_id" : "1014194851576721408",
               "hierarchies_id" : null,
               "ordinal" : 1,
               "group_name" : "testweidu830",
               "group_code" : "testweidu830",
               "biz_type" : "DIMENSION",
               "hierarchies" : null,
               "l1" : null,
               "l2" : null,
               "l3" : null,
               "l1_id" : null,
               "l2_id" : null,
               "l3_id" : null,
               "dw_type" : null,
               "id" : "1014197025585168384"
             } ],
             "monitor" : null,
             "atomic_index" : {
               "id" : "1014195214723756032",
               "name_en" : "zonghe8830",
               "name_ch" : "zonghe8830",
               "description" : "",
               "create_by" : null,
               "cal_exp" : "sum(${1014195020200325120}) ",
               "cal_fn_ids" : null,
               "l1_id" : null,
               "l2_id" : null,
               "l3_id" : null,
               "table_id" : "1014195020183547904",
               "tb_name" : null,
               "dw_type" : null,
               "field_ids" : [ "1014195020200325120" ],
               "field_names" : null,
               "status" : "DRAFT",
               "biz_type" : "FACT_LOGIC_TABLE",
               "create_time" : "2022-09-02T09:56:31.536+08:00",
               "update_time" : "2022-09-02T09:56:31.536+08:00",
               "l1" : null,
               "l2" : null,
               "l3" : null,
               "approval_info" : null,
               "new_biz" : null
             },
             "time_condition_name" : null,
             "create_time" : "2022-08-30T15:36:54+08:00",
             "update_time" : "2022-08-30T15:36:54+08:00",
             "l1" : null,
             "l2" : null,
             "l3" : null,
             "summary_table_id" : null,
             "approval_info" : null,
             "new_biz" : null
           },
           "id" : "1014197025488699392",
           "tables" : [ ],
           "biz_type" : "DERIVATIVE_INDEX",
           "parent_ids" : [ ],
           "child_ids" : [ "1014195214723756032" ]
         } ],
         "total" : 2,
         "groups" : {
           "1014194851576721408" : {
             "dimension_groups" : [ {
               "group_id" : "1014194851576721408",
               "role" : null,
               "dimension_id" : "1014194851576721408",
               "hierarchies_id" : null,
               "ordinal" : 1,
               "group_name" : "testweidu830",
               "group_code" : "testweidu830",
               "biz_type" : "DIMENSION",
               "hierarchies" : null,
               "l1" : null,
               "l2" : null,
               "l3" : null,
               "l1_id" : null,
               "l2_id" : null,
               "l3_id" : null,
               "dw_type" : null,
               "id" : "1014197025585168384"
             } ],
             "ids" : [ "1014197025488699392" ]
           }
         },
         "links" : {
           "vo" : {
             "id" : "1014197025488699392",
             "name_en" : "zonghe8830",
             "name_ch" : "zonghe8830(testweidu830)",
             "description" : "",
             "create_by" : "abc",
             "data_type" : "STRING",
             "l1_id" : null,
             "l2_id" : null,
             "l3_id" : "767858832738234368",
             "status" : "DRAFT",
             "atomic_index_id" : "1014195214723756032",
             "time_condition_id" : null,
             "time_field_id" : null,
             "time_field_name" : null,
             "common_conditions" : [ ],
             "dimension_groups" : [ {
               "group_id" : "1014194851576721408",
               "role" : null,
               "dimension_id" : "1014194851576721408",
               "hierarchies_id" : null,
               "ordinal" : 1,
               "group_name" : "testweidu830",
               "group_code" : "testweidu830",
               "biz_type" : "DIMENSION",
               "hierarchies" : null,
               "l1" : null,
               "l2" : null,
               "l3" : null,
               "l1_id" : null,
               "l2_id" : null,
               "l3_id" : null,
               "dw_type" : null,
               "id" : "1014197025585168384"
             } ],
             "monitor" : null,
             "atomic_index" : {
               "id" : "1014195214723756032",
               "name_en" : "zonghe8830",
               "name_ch" : "zonghe8830",
               "description" : "",
               "create_by" : null,
               "cal_exp" : "sum(${1014195020200325120}) ",
               "cal_fn_ids" : null,
               "l1_id" : null,
               "l2_id" : null,
               "l3_id" : null,
               "table_id" : "1014195020183547904",
               "tb_name" : null,
               "dw_type" : null,
               "field_ids" : [ "1014195020200325120" ],
               "field_names" : null,
               "status" : "DRAFT",
               "biz_type" : "FACT_LOGIC_TABLE",
               "create_time" : "2022-09-02T09:56:31.536+08:00",
               "update_time" : "2022-09-02T09:56:31.536+08:00",
               "l1" : null,
               "l2" : null,
               "l3" : null,
               "approval_info" : null,
               "new_biz" : null
             },
             "time_condition_name" : null,
             "create_time" : "2022-08-30T15:36:54+08:00",
             "update_time" : "2022-08-30T15:36:54+08:00",
             "l1" : null,
             "l2" : null,
             "l3" : null,
             "summary_table_id" : null,
             "approval_info" : null,
             "new_biz" : null
           },
           "id" : "1014197025488699392",
           "tables" : [ ],
           "biz_type" : "DERIVATIVE_INDEX",
           "parent_ids" : [ ],
           "child_ids" : [ "1014195214723756032" ]
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

+-------------+-------------------------------------------------------------------------+
| Status Code | Description                                                             |
+=============+=========================================================================+
| 200         | This operation succeeds, and the returned data is MetricRelationVOList. |
+-------------+-------------------------------------------------------------------------+
| 400         | BadRequest                                                              |
+-------------+-------------------------------------------------------------------------+
| 401         | Unauthorized                                                            |
+-------------+-------------------------------------------------------------------------+
| 403         | Forbidden                                                               |
+-------------+-------------------------------------------------------------------------+
