:original_name: RemoveDesignQualityInfos.html

.. _RemoveDesignQualityInfos:

Clear Quality Rule
==================

Function
--------

Clears the quality rule of a table.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v2/{project_id}/design/{table_id}/qualities

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | table_id   | Yes       | String | Table ID, which is a string                                                                                             |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================+
   | table_type      | Yes             | String          | Table type. The default value is Service table. TABLE_MODEL (service table (logical entity/physical table), AGGREGATION_LOGIC_TABLE (summary table), FACT_LOGIC_TABLE (fact table), and DIMENSION_LOGIC_TABLE (dimension table). |
   |                 |                 |                 |                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  TABLE_MODEL                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  AGGREGATION_LOGIC_TABLE                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  FACT_LOGIC_TABLE                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  DIMENSION_LOGIC_TABLE                                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+--------------------------------------------------------------+----------------------------------------------+
   | Parameter | Type                                                         | Description                                  |
   +===========+==============================================================+==============================================+
   | data      | :ref:`data <removedesignqualityinfos__response_data>` object | Clear the data returned by the quality rule. |
   +-----------+--------------------------------------------------------------+----------------------------------------------+

.. _removedesignqualityinfos__response_data:

.. table:: **Table 5** data

   ========= ======= ====================================================
   Parameter Type    Description
   ========= ======= ====================================================
   value     Boolean Indicates whether the alarm is cleared successfully.
   ========= ======= ====================================================

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

To clear the quality rules of the table whose ID is 1217123755210469378 and table type is TABLE_MODEL, run the following command:

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/design/1217123755210469378/qualities?table_type=TABLE_MODEL

Example Responses
-----------------

**Status code: 200**

Success: A message indicating whether the deletion is successful is returned.

.. code-block::

   {
     "data" : {
       "value" : true
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

+-------------+-------------------------------------------------------------------------------+
| Status Code | Description                                                                   |
+=============+===============================================================================+
| 200         | Success: A message indicating whether the deletion is successful is returned. |
+-------------+-------------------------------------------------------------------------------+
| 400         | BadRequest                                                                    |
+-------------+-------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                  |
+-------------+-------------------------------------------------------------------------------+
| 403         | Forbidden                                                                     |
+-------------+-------------------------------------------------------------------------------+
