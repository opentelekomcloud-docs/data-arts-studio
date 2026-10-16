:original_name: DeleteDesignDimension.html

.. _DeleteDesignDimension:

Deleting Dimensions
===================

Function
--------

This API is used to delete dimensions with specified IDs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v2/{project_id}/design/dimensions

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================================================================================+
   | ids             | Yes             | Array of strings | ID list, which is a string                                                                                                                                                                             |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | del_types       | No              | String           | Deletion type.                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                        |
   |                 |                 |                  | Enumerated values:                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                        |
   |                 |                 |                  | -  **PHYSICAL_TABLE**: whether to delete physical database tables. This parameter is valid only for tables that can be materialized. (If this parameter is set, physical database tables are deleted.) |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                      | Description                                                                                        |
   +===========+===========================================================+====================================================================================================+
   | data      | :ref:`data <deletedesigndimension__response_data>` object | Indicates the final deletion result, that is, the number of objects that are successfully deleted. |
   +-----------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------+

.. _deletedesigndimension__response_data:

.. table:: **Table 5** data

   ========= ======= ======================================
   Parameter Type    Description
   ========= ======= ======================================
   value     Integer Number of successfully deleted objects
   ========= ======= ======================================

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

Delete dimensions based on the input parameters. Only dimensions in the draft, offline, or rejected state can be deleted.

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/design/dimensions

   {
     "ids" : [ "1227990857618227200" ]
   }

Example Responses
-----------------

**Status code: 200**

The operation succeeds, and the number of deleted dimensions is returned.

.. code-block::

   {
     "value" : 1
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

+-------------+---------------------------------------------------------------------------+
| Status Code | Description                                                               |
+=============+===========================================================================+
| 200         | The operation succeeds, and the number of deleted dimensions is returned. |
+-------------+---------------------------------------------------------------------------+
| 400         | BadRequest                                                                |
+-------------+---------------------------------------------------------------------------+
| 401         | Unauthorized                                                              |
+-------------+---------------------------------------------------------------------------+
| 403         | Forbidden                                                                 |
+-------------+---------------------------------------------------------------------------+
