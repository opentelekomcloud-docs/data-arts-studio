:original_name: DeleteDesignLatestApproval.html

.. _DeleteDesignLatestApproval:

Deleting an Entity
==================

Function
--------

When a released entity is edited, an extension is generated. This API is used to delete the extension information of the entity.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v2/{project_id}/design/approvals/business/{biz_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | biz_id     | Yes       | String | ID of the entity to be deleted, which is a string                                                                       |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | biz_type        | Yes             | String          | Entity type to be deleted.                                            |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | Options:                                                              |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  ATOMIC_INDEX: atomic metric                                        |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  DERIVATIVE_INDEX: derivative indicator                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  DIMENSION: dimension                                               |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  FACT_LOGIC_TABLE: fact table                                       |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  TABLE_MODEL: relationship modeling (logical entity/physical table) |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  STANDARD_ELEMENT: data standard                                    |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  AGGREGATION_LOGIC_TABLE: summary table                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  CODE_TABLE: code table                                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  BIZ_METRIC: service indicator                                      |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  COMPOUND_METRIC: compound metric                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

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

   +-----------+----------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                           | Description                                                                                        |
   +===========+================================================================+====================================================================================================+
   | data      | :ref:`data <deletedesignlatestapproval__response_data>` object | Indicates the final deletion result, that is, the number of objects that are successfully deleted. |
   +-----------+----------------------------------------------------------------+----------------------------------------------------------------------------------------------------+

.. _deletedesignlatestapproval__response_data:

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

Delete the extended information about the table whose ID is 1217123755210469376 in ER modeling.

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/design/approvals/business/1217123755210469376?biz_type=TABLE_MODEL

Example Responses
-----------------

**Status code: 200**

Success. The returned data indicates the number of deleted data records. If the value is 1, the deletion is successful.

.. code-block::

   {
     "data" : {
       "value" : 1
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

+-------------+-------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                             |
+=============+=========================================================================================================================+
| 200         | Success. The returned data indicates the number of deleted data records. If the value is 1, the deletion is successful. |
+-------------+-------------------------------------------------------------------------------------------------------------------------+
| 400         | BadRequest                                                                                                              |
+-------------+-------------------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                                                            |
+-------------+-------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden                                                                                                               |
+-------------+-------------------------------------------------------------------------------------------------------------------------+
