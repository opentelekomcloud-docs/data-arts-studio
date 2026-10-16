:original_name: DeleteWorkspaceusers.html

.. _DeleteWorkspaceusers:

Deleting a Workspace User
=========================

Function
--------

This API is used to delete a user from a workspace.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/{workspace_id}/delete-users

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                         |
   +==============+===========+========+=====================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`          |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | workspace_id | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                           |
   +===========+===========+========+=======================================================================================================+
   | user_ids  | Yes       | Object | User group list, which can be obtained using the API for querying the workspace user information list |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

Example Requests
----------------

.. code-block::

   {
     "user_ids" : [ "2d032145d82546b5b83cd7a6fd7d0afc" ]
   }

Example Responses
-----------------

**Status code: 200**

The user is deleted from the workspace.

.. code-block::

   {
     "message" : null,
     "is_success" : true
   }

**Status code: 400**

Bad request.

.. code-block::

   {
     "error_code" : "DAYU.4402",
     "error_msg" : "The operation failed, detail msg {0}."
   }

**Status code: 500**

Internal server error.

.. code-block::

   {
     "error_code" : "DAYU.3531",
     "error_msg" : "Internal server error: {0}"
   }

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The user is deleted from the workspace.
400         Bad request.
500         Internal server error.
=========== =======================================
