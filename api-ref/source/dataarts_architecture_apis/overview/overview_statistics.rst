:original_name: CountOverviews.html

.. _CountOverviews:

Overview Statistics
===================

Function
--------

Overview statistics.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/definitions/statistic

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
   | data      | :ref:`data <countoverviews__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+----------------------------------------------------+----------------------------------------------------------------+

.. _countoverviews__response_data:

.. table:: **Table 4** data

   +-----------+----------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter | Type                                                                 | Description                                                 |
   +===========+======================================================================+=============================================================+
   | value     | :ref:`StatisticInfo <countoverviews__response_statisticinfo>` object | value: unified outer data structure of the returned result. |
   +-----------+----------------------------------------------------------------------+-------------------------------------------------------------+

.. _countoverviews__response_statisticinfo:

.. table:: **Table 5** StatisticInfo

   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | Parameter               | Type                                                                     | Description                      |
   +=========================+==========================================================================+==================================+
   | atomic_index            | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Atomic metric.                   |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | derivative_index        | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Derivative indicator.            |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | compound_metric         | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Composite index.                 |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | biz_index               | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Service indicator.               |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | dimension               | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Dimension.                       |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | condition_group         | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Indicates the restriction group. |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | time_condition          | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Time limit.                      |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | common_condition        | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | General restriction.             |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | dimension_logic_table   | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Dimension table.                 |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | fact_logic_table        | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Fact table.                      |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | aggregation_logic_table | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Summary table.                   |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | data_standard           | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Data standard.                   |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | table_model             | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Service table.                   |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | lookup_table            | :ref:`StatisticSchema <countoverviews__response_statisticschema>` object | Indicates the code table.        |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | pending_review          | Integer                                                                  | Waiting for my review.           |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+
   | my_applications         | Integer                                                                  | My Application.                  |
   +-------------------------+--------------------------------------------------------------------------+----------------------------------+

.. _countoverviews__response_statisticschema:

.. table:: **Table 6** StatisticSchema

   ================= ======= ==================
   Parameter         Type    Description
   ================= ======= ==================
   increase          Integer Added this month.
   total             Integer Total number.
   standard_coverage Double  Standard coverage.
   ================= ======= ==================

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

Statistics on the Overview page.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/definitions/statistic

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is StatisticInfo.

.. code-block::

   {
     "data" : {
       "value" : {
         "atomic_index" : {
           "increase" : 0,
           "total" : 5,
           "standard_coverage" : null
         },
         "derivative_index" : {
           "increase" : 0,
           "total" : 8,
           "standard_coverage" : null
         },
         "compound_metric" : {
           "increase" : 0,
           "total" : 3,
           "standard_coverage" : null
         },
         "biz_index" : {
           "increase" : 0,
           "total" : 1,
           "standard_coverage" : null
         },
         "dimension" : {
           "increase" : 1,
           "total" : 22,
           "standard_coverage" : null
         },
         "condition_group" : null,
         "time_condition" : {
           "increase" : 0,
           "total" : 14,
           "standard_coverage" : null
         },
         "common_condition" : null,
         "dimension_logic_table" : {
           "increase" : 1,
           "total" : 17,
           "standard_coverage" : null
         },
         "fact_logic_table" : {
           "increase" : 0,
           "total" : 7,
           "standard_coverage" : null
         },
         "aggregation_logic_table" : {
           "increase" : 0,
           "total" : 12,
           "standard_coverage" : null
         },
         "data_standard" : {
           "increase" : 1,
           "total" : 13,
           "standard_coverage" : null
         },
         "table_model" : {
           "increase" : 15,
           "total" : 50,
           "standard_coverage" : 0.0775
         },
         "lookup_table" : {
           "increase" : 2,
           "total" : 10,
           "standard_coverage" : null
         },
         "pending_review" : 1,
         "my_applications" : 1
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

+-------------+------------------------------------------------------------------+
| Status Code | Description                                                      |
+=============+==================================================================+
| 200         | This operation succeeds, and the returned data is StatisticInfo. |
+-------------+------------------------------------------------------------------+
| 400         | BadRequest                                                       |
+-------------+------------------------------------------------------------------+
| 401         | Unauthorized                                                     |
+-------------+------------------------------------------------------------------+
| 403         | Forbidden                                                        |
+-------------+------------------------------------------------------------------+
