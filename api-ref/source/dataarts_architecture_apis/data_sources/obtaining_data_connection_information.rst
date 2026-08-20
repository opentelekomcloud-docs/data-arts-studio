:original_name: SearchDwByType.html

.. _SearchDwByType:

Obtaining Data Connection Information
=====================================

Function
--------

This API is used to obtain data connection information of a specified type.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/atlas/data-warehouses

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ============= ========= ======= ======================================
   Parameter     Mandatory Type    Description
   ============= ========= ======= ======================================
   force_refresh No        Boolean Indicates whether to query the latest.
   dw_type       Yes       String  Data connection type.
   limit         No        Integer limit
   offset        No        Integer limit
   ============= ========= ======= ======================================

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

   +-----------+----------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                               | Description                                                    |
   +===========+====================================================+================================================================+
   | data      | :ref:`data <searchdwbytype__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+----------------------------------------------------+----------------------------------------------------------------+

.. _searchdwbytype__response_data:

.. table:: **Table 5** data

   +-----------+--------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                 | Description                       |
   +===========+======================================================================================+===================================+
   | value     | Array of :ref:`DataConnectionVO <searchdwbytype__response_dataconnectionvo>` objects | Data connection information array |
   +-----------+--------------------------------------------------------------------------------------+-----------------------------------+

.. _searchdwbytype__response_dataconnectionvo:

.. table:: **Table 6** DataConnectionVO

   +--------------+--------+--------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                        |
   +==============+========+====================================================================+
   | dw_name      | String | Name of a data connection.                                         |
   +--------------+--------+--------------------------------------------------------------------+
   | dw_id        | String | Data connection ID.                                                |
   +--------------+--------+--------------------------------------------------------------------+
   | display_name | String | Data connection name, which adapts to the existing implementation. |
   +--------------+--------+--------------------------------------------------------------------+
   | dw_type      | String | Data connection type.                                              |
   +--------------+--------+--------------------------------------------------------------------+

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

Obtain information about a DWS data connection.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/atlas/data-warehouses?dw_type=DWS

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is all DataConnectionVO entities of the specified type.

.. code-block::

   {
     "data" : {
       "value" : [ {
         "dw_id" : "c5daea963128457cb7579404da5a23c7",
         "dw_name" : "dws_test",
         "dw_type" : "DWS"
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

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                            |
+=============+========================================================================================================+
| 200         | This operation succeeds, and the returned data is all DataConnectionVO entities of the specified type. |
+-------------+--------------------------------------------------------------------------------------------------------+
| 400         | BadRequest                                                                                             |
+-------------+--------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                                           |
+-------------+--------------------------------------------------------------------------------------------------------+
| 403         | Forbidden                                                                                              |
+-------------+--------------------------------------------------------------------------------------------------------+
