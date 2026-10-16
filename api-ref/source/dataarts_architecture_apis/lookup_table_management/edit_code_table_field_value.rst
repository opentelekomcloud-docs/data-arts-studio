:original_name: UpdateCodeTableValues.html

.. _UpdateCodeTableValues:

Edit Code Table Field Value
===========================

Function
--------

Edit the values of the fields in the lookup table.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v2/{project_id}/design/code-tables/{id}/values

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Entity ID, which is a string                                                                                            |
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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                       | Description                                                  |
   +===========+===========+============================================================================================+==============================================================+
   | to_add    | No        | Array of :ref:`CodeTableFieldVO <updatecodetablevalues__request_codetablefieldvo>` objects | The code table attribute and attribute value list are added. |
   +-----------+-----------+--------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | to_modify | No        | Array of :ref:`CodeTableFieldVO <updatecodetablevalues__request_codetablefieldvo>` objects | Edit the lookup table attribute value list.                  |
   +-----------+-----------+--------------------------------------------------------------------------------------------+--------------------------------------------------------------+
   | to_remove | No        | Array of :ref:`CodeTableFieldVO <updatecodetablevalues__request_codetablefieldvo>` objects | List of lookup table attribute IDs to be deleted.            |
   +-----------+-----------+--------------------------------------------------------------------------------------------+--------------------------------------------------------------+

.. _updatecodetablevalues__request_codetablefieldvo:

.. table:: **Table 4** CodeTableFieldVO

   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | Parameter               | Mandatory | Type                                                                                                 | Description                                                      |
   +=========================+===========+======================================================================================================+==================================================================+
   | id                      | No        | String                                                                                               | Lookup table field ID, which is a string                         |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_id           | No        | String                                                                                               | ID of the lookup table (mandatory for update), which is a string |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | ordinal                 | Yes       | Integer                                                                                              | Sequence number.                                                 |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_en                 | Yes       | String                                                                                               | Field name, in English.                                          |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_ch                 | Yes       | String                                                                                               | Field name, in Chinese.                                          |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | description             | No        | String                                                                                               | Description.                                                     |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type               | Yes       | String                                                                                               | Field type                                                       |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type_extend        | No        | String                                                                                               | Extended field of the data type.                                 |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | is_unique_key           | No        | Boolean                                                                                              | Whether the field is unique.                                     |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_field_values | No        | Array of :ref:`CodeTableFieldValueVO <updatecodetablevalues__request_codetablefieldvaluevo>` objects | Code list attribute value.                                       |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | count_field_values      | No        | Integer                                                                                              | Total number of lookup table attribute values.                   |
   +-------------------------+-----------+------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+

.. _updatecodetablevalues__request_codetablefieldvaluevo:

.. table:: **Table 5** CodeTableFieldValueVO

   +-------------+-----------+---------+-----------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                         |
   +=============+===========+=========+=====================================================+
   | id          | No        | String  | Lookup table field ID, which is a string            |
   +-------------+-----------+---------+-----------------------------------------------------+
   | fd_id       | No        | String  | Attribute ID of the lookup table, which is a string |
   +-------------+-----------+---------+-----------------------------------------------------+
   | fd_value    | No        | String  | Code list attribute value.                          |
   +-------------+-----------+---------+-----------------------------------------------------+
   | ordinal     | No        | Integer | Sequence number.                                    |
   +-------------+-----------+---------+-----------------------------------------------------+
   | description | No        | String  | Description.                                        |
   +-------------+-----------+---------+-----------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +-----------+-----------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                      | Description                                                    |
   +===========+===========================================================+================================================================+
   | data      | :ref:`data <updatecodetablevalues__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+-----------------------------------------------------------+----------------------------------------------------------------+

.. _updatecodetablevalues__response_data:

.. table:: **Table 7** data

   +-----------+---------------------------------------------------------------------------------------------+------------------------------------+
   | Parameter | Type                                                                                        | Description                        |
   +===========+=============================================================================================+====================================+
   | value     | Array of :ref:`CodeTableFieldVO <updatecodetablevalues__response_codetablefieldvo>` objects | Code table field list information. |
   +-----------+---------------------------------------------------------------------------------------------+------------------------------------+

.. _updatecodetablevalues__response_codetablefieldvo:

.. table:: **Table 8** CodeTableFieldVO

   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | Parameter               | Type                                                                                                  | Description                                                      |
   +=========================+=======================================================================================================+==================================================================+
   | id                      | String                                                                                                | Lookup table field ID, which is a string                         |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_id           | String                                                                                                | ID of the lookup table (mandatory for update), which is a string |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | ordinal                 | Integer                                                                                               | Sequence number.                                                 |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_en                 | String                                                                                                | Field name, in English.                                          |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_ch                 | String                                                                                                | Field name, in Chinese.                                          |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | description             | String                                                                                                | Description.                                                     |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type               | String                                                                                                | Field type                                                       |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | domain_type             | String                                                                                                | Domain to which a field type belongs.                            |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | Options:                                                         |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | -  NUMBER: number                                                |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | -  STRING: character type                                        |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | -  DATETIME: date type                                           |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | -  BLOB: large object (BLOB)                                     |
   |                         |                                                                                                       |                                                                  |
   |                         |                                                                                                       | -  OTHER: other types                                            |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type_extend        | String                                                                                                | Extended field of the data type.                                 |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | is_unique_key           | Boolean                                                                                               | Whether the field is unique.                                     |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_field_values | Array of :ref:`CodeTableFieldValueVO <updatecodetablevalues__response_codetablefieldvaluevo>` objects | Code list attribute value.                                       |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | count_field_values      | Integer                                                                                               | Total number of lookup table attribute values.                   |
   +-------------------------+-------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+

.. _updatecodetablevalues__response_codetablefieldvaluevo:

.. table:: **Table 9** CodeTableFieldValueVO

   =========== ======= ===================================================
   Parameter   Type    Description
   =========== ======= ===================================================
   id          String  Lookup table field ID, which is a string
   fd_id       String  Attribute ID of the lookup table, which is a string
   fd_value    String  Code list attribute value.
   ordinal     Integer Sequence number.
   description String  Description.
   =========== ======= ===================================================

**Status code: 400**

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

**Status code: 401**

.. table:: **Table 11** Response body parameters

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

.. table:: **Table 12** Response body parameters

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

.. table:: **Table 13** Response body parameters

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

   PUT https://{endpoint}/v2/{project_id}/design/code-tables/1230204979835502592/values

   {
     "to_add" : [ {
       "id" : "178101",
       "code_table_id" : "1230204979835502592",
       "ordinal" : 1,
       "name_en" : "code",
       "name_ch" : "Message",
       "description" : "",
       "data_type" : "STRING",
       "domain_type" : null,
       "data_type_extend" : null,
       "is_unique_key" : false,
       "code_table_field_values" : [ {
         "fd_id" : "178101",
         "fd_value" : "4",
         "ordinal" : 4
       } ],
       "count_field_values" : 3
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
       "code_table_field_values" : [ {
         "fd_id" : "178102",
         "fd_value" : "5",
         "ordinal" : 4
       } ],
       "count_field_values" : 3
     }, {
       "id" : "178103",
       "code_table_id" : "1230204979835502592",
       "ordinal" : 3,
       "name_en" : "city",
       "name_ch" : "Specifies the city where the customer is located.",
       "description" : "",
       "data_type" : "STRING",
       "domain_type" : null,
       "data_type_extend" : null,
       "is_unique_key" : false,
       "code_table_field_values" : [ {
         "fd_id" : "178103",
         "fd_value" : "6",
         "ordinal" : 4
       } ],
       "count_field_values" : 3
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
       "code_table_field_values" : [ {
         "fd_id" : "178104",
         "fd_value" : "7",
         "ordinal" : 4
       } ],
       "count_field_values" : 3
     } ]
   }

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is a CodeTableFieldVO array.

.. code-block::

   {
     "data" : {
       "value" : [ {
         "id" : "178101",
         "code_table_id" : "1230204979835502592",
         "ordinal" : 1,
         "name_en" : "code",
         "name_ch" : "Message",
         "description" : "",
         "data_type" : "STRING",
         "domain_type" : null,
         "data_type_extend" : null,
         "is_unique_key" : false,
         "code_table_field_values" : [ {
           "id" : "19983446",
           "fd_id" : "178101",
           "fd_value" : "1",
           "ordinal" : 1,
           "description" : null
         }, {
           "id" : "19983450",
           "fd_id" : "178101",
           "fd_value" : "2",
           "ordinal" : 2,
           "description" : null
         }, {
           "id" : "19983454",
           "fd_id" : "178101",
           "fd_value" : "3",
           "ordinal" : 3,
           "description" : null
         }, {
           "id" : "19983554",
           "fd_id" : "178101",
           "fd_value" : "4",
           "ordinal" : 4,
           "description" : null
         } ],
         "count_field_values" : 4
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
         "code_table_field_values" : [ {
           "id" : "19983447",
           "fd_id" : "178102",
           "fd_value" : "5",
           "ordinal" : 1,
           "description" : null
         }, {
           "id" : "19983451",
           "fd_id" : "178102",
           "fd_value" : "6
           "ordinal" : 2,
           "description" : null
         }, {
           "id" : "19983455",
           "fd_id" : "178102",
           "fd_value" : "7",
           "ordinal" : 3,
           "description" : null
         }, {
           "id" : "19983555",
           "fd_id" : "178102",
           "fd_value" : "8",
           "ordinal" : 4,
           "description" : null
         } ],
         "count_field_values" : 4
       }, {
         "id" : "178103",
         "code_table_id" : "1230204979835502592",
         "ordinal" : 3,
         "name_en" : "city",
         "name_ch" : "Cities",
         "description" : "",
         "data_type" : "STRING",
         "domain_type" : null,
         "data_type_extend" : null,
         "is_unique_key" : false,
         "code_table_field_values" : [ {
           "id" : "19983448",
           "fd_id" : "178103",
           "fd_value" : "9",
           "ordinal" : 1,
           "description" : null
         }, {
           "id" : "19983452",
           "fd_id" : "178103",
           "fd_value" : "10",
           "ordinal" : 2,
           "description" : null
         }, {
           "id" : "19983456",
           "fd_id" : "178103",
           "fd_value" : "11",
           "ordinal" : 3,
           "description" : null
         }, {
           "id" : "19983556",
           "fd_id" : "178103",
           "fd_value" : "12",
           "ordinal" : 4,
           "description" : null
         } ],
         "count_field_values" : 4
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
         "code_table_field_values" : [ {
           "id" : "19983449",
           "fd_id" : "178104",
           "fd_value" : "13",
           "ordinal" : 1,
           "description" : null
         }, {
           "id" : "19983453",
           "fd_id" : "178104",
           "fd_value" : "14",
           "ordinal" : 2,
           "description" : null
         }, {
           "id" : "19983457",
           "fd_id" : "178104",
           "fd_value" : "15",
           "ordinal" : 3,
           "description" : null
         }, {
           "id" : "19983557",
           "fd_id" : "178104",
           "fd_value" : "16",
           "ordinal" : 4,
           "description" : null
         } ],
         "count_field_values" : 4
       } ]
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

+-------------+-----------------------------------------------------------------------------+
| Status Code | Description                                                                 |
+=============+=============================================================================+
| 200         | This operation succeeds, and the returned data is a CodeTableFieldVO array. |
+-------------+-----------------------------------------------------------------------------+
| 400         | BadRequest                                                                  |
+-------------+-----------------------------------------------------------------------------+
| 401         | Unauthorized                                                                |
+-------------+-----------------------------------------------------------------------------+
| 403         | Forbidden                                                                   |
+-------------+-----------------------------------------------------------------------------+
| 404         | Not Found                                                                   |
+-------------+-----------------------------------------------------------------------------+
