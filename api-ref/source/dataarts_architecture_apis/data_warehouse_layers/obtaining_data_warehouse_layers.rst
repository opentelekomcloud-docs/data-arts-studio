:original_name: ListDesignDataLayers.html

.. _ListDesignDataLayers:

Obtaining Data Warehouse Layers
===============================

Function
--------

This API is used to obtain data warehouse layers.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/design/data-layers

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
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

   +-----------+----------------------------------------------------------+--------------------------+
   | Parameter | Type                                                     | Description              |
   +===========+==========================================================+==========================+
   | data      | :ref:`data <listdesigndatalayers__response_data>` object | Data returned by the API |
   +-----------+----------------------------------------------------------+--------------------------+

.. _listdesigndatalayers__response_data:

.. table:: **Table 5** data

   +-----------+----------------------------------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                                             | Description                    |
   +===========+==================================================================================+================================+
   | value     | Array of :ref:`DataLayerVO <listdesigndatalayers__response_datalayervo>` objects | Array of data warehouse layers |
   +-----------+----------------------------------------------------------------------------------+--------------------------------+

.. _listdesigndatalayers__response_datalayervo:

.. table:: **Table 6** DataLayerVO

   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter                     | Type             | Description                                                                                                 |
   +===============================+==================+=============================================================================================================+
   | id                            | String           | Data warehouse layer ID, which is a string                                                                  |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | level                         | Integer          | Level, starting from 1                                                                                      |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | name                          | String           | Name                                                                                                        |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | type                          | String           | Data warehouse layer type, which can be **ER**, **DIMENSION**, or **DM**                                    |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | description                   | String           | Data warehouse layer description                                                                            |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | is_default                    | Boolean          | Whether the layer is the default layer that cannot be deleted, which can be SDI, DWR, or DM                 |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+
   | disabled_customized_field_ids | Array of strings | IDs of the customized fields disabled at the layer, including table-level and field-level customized fields |
   +-------------------------------+------------------+-------------------------------------------------------------------------------------------------------------+

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

**Status code: 404**

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

Query data warehouse layers based on parameters.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/design/data-layers

Example Responses
-----------------

**Status code: 200**

The operation succeeds, and the **DataLayerVO** array of the layers is returned.

.. code-block::

   {
     "data" : {
       "value" : [ {
         "id" : 123456,
         "level" : 1,
         "name" : "SDI",
         "type" : "THIRD_NF",
         "description" : "SDI",
         "is_default" : true,
         "disabled_customized_field_ids" : [ ]
       }, {
         "id" : 123457,
         "level" : 3,
         "name" : "DWR",
         "type" : "DIMENSION",
         "is_default" : true,
         "description" : "DWR",
         "disabled_customized_field_ids" : [ ]
       }, {
         "id" : 123458,
         "level" : 3,
         "name" : "DM",
         "type" : "DM",
         "is_default" : true,
         "description" : "DM",
         "disabled_customized_field_ids" : [ ]
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

+-------------+----------------------------------------------------------------------------------+
| Status Code | Description                                                                      |
+=============+==================================================================================+
| 200         | The operation succeeds, and the **DataLayerVO** array of the layers is returned. |
+-------------+----------------------------------------------------------------------------------+
| 400         | BadRequest                                                                       |
+-------------+----------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                     |
+-------------+----------------------------------------------------------------------------------+
| 403         | Forbidden                                                                        |
+-------------+----------------------------------------------------------------------------------+
| 404         | Not Found                                                                        |
+-------------+----------------------------------------------------------------------------------+
