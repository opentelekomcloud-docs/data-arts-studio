:original_name: SearchCodeTableValues.html

.. _SearchCodeTableValues:

Viewing Field Values in the Code Table
======================================

Function
--------

Check the values of the fields in the code table.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/code-tables/{id}/values

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Entity ID, which is a string                                                                                            |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                         |
   +===========+===========+=========+=====================================================================================================================================================================================================================================+
   | limit     | No        | Integer | Number of records to be queried on each page, that is, Y records to be queried. The default value is 50, and the value range is [1,100].                                                                                            |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset    | No        | Integer | Start coordinate of the query, that is, the number of skipped data records. The value can only be 0 or an integer multiple of limit. If the value does not meet the requirement, the value is rounded down. The default value is 0. |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   data      Object Returned data information.
   ========= ====== ==========================

**Status code: 400**

.. table:: **Table 5** Response body parameters

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

**Status code: 403**

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

**Status code: 404**

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

Edit the field values of the lookup table based on the request parameters, including adding fields to the lookup table.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/code-tables/1230204979835502592/values

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is a CodeTableFieldInfoVO array and the total number of records.

.. code-block::

   {
     "data" : {
       "value" : {
         "id" : "1230204979835502592",
         "name_en" : "DC000007",
         "name_ch" : "test_update_code_table",
         "tb_version" : 0,
         "directory_id" : "1194963842254491648",
         "directory_path" : "test_czh_dir",
         "description" : "",
         "from_public" : false,
         "create_by" : "test_uesr",
         "status" : "DRAFT",
         "create_time" : "2024-04-17T17:15:23+08:00",
         "update_time" : "2024-04-17T17:25:34+08:00",
         "approval_info" : null,
         "new_biz" : null,
         "code_table_fields" : [ {
           "id" : "178101",
           "code_table_id" : "1230204979835502592",
           "ordinal" : 1,
           "name_en" : "code",
           "name_ch" : "Status",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
         }, {
           "id" : "178102",
           "code_table_id" : "1230204979835502592",
           "ordinal" : 2,
           "name_en" : "province",
           "name_ch" : "Economical",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
         }, {
           "id" : "178103",
           "code_table_id" : "1230204979835502592",
           "ordinal" : 3,
           "name_en" : "city",
           "name_ch" : "City",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
         }, {
           "id" : "178104",
           "code_table_id" : "1230204979835502592",
           "ordinal" : 4,
           "name_en" : "county",
           "name_ch" : "County",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
         } ]
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

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The User Request API does not exist."
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                     |
+=============+=================================================================================================================+
| 200         | This operation succeeds, and the returned data is a CodeTableFieldInfoVO array and the total number of records. |
+-------------+-----------------------------------------------------------------------------------------------------------------+
| 400         | BadRequest                                                                                                      |
+-------------+-----------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                                                    |
+-------------+-----------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden                                                                                                       |
+-------------+-----------------------------------------------------------------------------------------------------------------+
| 404         | Not Found                                                                                                       |
+-------------+-----------------------------------------------------------------------------------------------------------------+
