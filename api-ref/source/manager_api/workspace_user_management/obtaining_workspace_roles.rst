:original_name: ListWorkspaceRoles.html

.. _ListWorkspaceRoles:

Obtaining Workspace Roles
=========================

Function
--------

This API is used to obtain the roles of a workspace.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/users/role

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                |
   +============+===========+========+============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>` |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                        |
   +==============+===========+========+====================================================================================================================================+
   | instance_id  | No        | String | DataArts Studio instance ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id | No        | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter | Type                                                                         | Description                                  |
   +===========+==============================================================================+==============================================+
   | [items]   | Array of :ref:`ApigRoleVo <listworkspaceroles__response_apigrolevo>` objects | List of roles in a DataArts Studio workspace |
   +-----------+------------------------------------------------------------------------------+----------------------------------------------+

.. _listworkspaceroles__response_apigrolevo:

.. table:: **Table 5** ApigRoleVo

   =========== ====== ================
   Parameter   Type   Description
   =========== ====== ================
   role_id     String Role ID
   role_code   String Role code
   role_name   String Role name
   description String Role description
   =========== ====== ================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

Example Requests
----------------

None

Example Responses
-----------------

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

=========== ====================================
Status Code Description
=========== ====================================
200         Roles of the workspace are returned.
400         Bad request.
500         Internal server error.
=========== ====================================
