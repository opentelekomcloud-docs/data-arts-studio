:original_name: ExportDesignModelTableDdl.html

.. _ExportDesignModelTableDdl:

Exporting DDL Statements of Tables in a Model
=============================================

Function
--------

Exports DDL statements of a specified table based on the model ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/workspaces/{model_id}/export

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                           |
   +============+===========+========+=======================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                               |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_id   | Yes       | String | ID of the relational model, which is a string. The value of **model_id** can be obtained from the API used to :ref:`obtain a model <listworkspaces>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+------------------+--------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                  |
   +===========+===========+==================+==============================================================+
   | tb_names  | No        | Array of strings | Name of the table to be exported.                            |
   +-----------+-----------+------------------+--------------------------------------------------------------+
   | with_db   | No        | Boolean          | The exported DDL package does not contain the database name. |
   +-----------+-----------+------------------+--------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                          | Description                |
   +===========+===============================================================+============================+
   | data      | :ref:`data <exportdesignmodeltableddl__response_data>` object | Returned data information. |
   +-----------+---------------------------------------------------------------+----------------------------+

.. _exportdesignmodeltableddl__response_data:

.. table:: **Table 5** data

   ========= ====== ================================================
   Parameter Type   Description
   ========= ====== ================================================
   value     String DDL statement of the table exported from the API
   ========= ====== ================================================

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

Export the DDL of the class and trl_aSCb01c tables in the model whose ID is 1217123720355803136. The DDL contains the database name.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/workspaces/1217123720355803136/export?with_db=true&tb_names=class&tb_names=trl_aSCb01c

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is DDL text information.

.. code-block::

   {
     "data" : {
       "value" : "CREATE TABLE IF NOT EXISTS ${database}.class (\n        class_id BIGINT  NOT NULL  comment '1111',\n        class_name VARCHAR(1024)  NOT NULL  comment '2222',\n        teacher VARCHAR(255)  comment '3333'\n,\nPRIMARY KEY(class_id)\n);\nALTER TABLE ${database}.pd_test COMMENT' None';\nCREATE TABLE IF NOT EXISTS ${database}.logic_{}$A_2 (\n        id VARCHAR(255)\n);\nALTER TABLE ${database}.logic_{}$A_2 COMMENT 'aaa';"
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
| 200         | This operation succeeds, and the returned data is DDL text information. |
+-------------+-------------------------------------------------------------------------+
| 400         | BadRequest                                                              |
+-------------+-------------------------------------------------------------------------+
| 401         | Unauthorized                                                            |
+-------------+-------------------------------------------------------------------------+
| 403         | Forbidden                                                               |
+-------------+-------------------------------------------------------------------------+
