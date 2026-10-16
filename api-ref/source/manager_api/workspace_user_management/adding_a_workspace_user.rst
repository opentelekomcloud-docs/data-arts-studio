:original_name: AddWorkSpaceUsers.html

.. _AddWorkSpaceUsers:

Adding a Workspace User
=======================

Function
--------

This API is used to add a workspace user.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/{workspace_id}/users

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

   +-----------+-----------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                               | Description                                                                                               |
   +===========+===========+====================================================================================+===========================================================================================================+
   | type      | Yes       | Integer                                                                            | User type. **0** indicates user and **1** indicates user group.                                           |
   +-----------+-----------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | user_ids  | No        | Array of :ref:`ApigIamUserDto <addworkspaceusers__request_apigiamuserdto>` objects | User list, which can be obtained using the API for querying the workspace user information list           |
   +-----------+-----------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | groups    | No        | Array of :ref:`Group <addworkspaceusers__request_group>` objects                   | User group list, which can be obtained using the API for querying the workspace user information list     |
   +-----------+-----------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | roles_ids | Yes       | Array of :ref:`ApigRole <addworkspaceusers__request_apigrole>` objects             | Workspace role list, which can be obtained using the API for querying the workspace user information list |
   +-----------+-----------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

.. _addworkspaceusers__request_apigiamuserdto:

.. table:: **Table 4** ApigIamUserDto

   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type    | Description                                                                                                                   |
   +=================+===========+=========+===============================================================================================================================+
   | user_id         | No        | String  | User ID, which can be obtained using the API for querying the workspace user information list                                 |
   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | user_name       | No        | String  | Username, which can be obtained using the API for querying the workspace user information list                                |
   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | domain_id       | No        | String  | Tenant ID, which can be obtained using the API for querying the workspace user information list                               |
   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | domain_name     | No        | String  | Tenant name, which can be obtained using the API for querying the workspace user information list                             |
   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | is_domain_owner | No        | Boolean | Whether the user is the workspace owner, which can be obtained using the API for querying the workspace user information list |
   +-----------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+

.. _addworkspaceusers__request_group:

.. table:: **Table 5** Group

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                |
   +===========+===========+========+============================================================================================+
   | id        | No        | String | User group ID, which can be obtained from Obtaining the Workspace User Information List.   |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------+
   | name      | No        | String | User group name, which can be obtained from Obtaining the Workspace User Information List. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------+

.. _addworkspaceusers__request_apigrole:

.. table:: **Table 6** ApigRole

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                            |
   +===========+===========+========+========================================================================================================================================================================================================+
   | role_id   | No        | String | Role ID, which can be obtained from the role list information. **r00001** indicates the admin, **r00002** indicates the admin, **r00003** indicates the operator, and **r00004** indicates the viewer. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

**Status code: 500**

.. table:: **Table 8** Response body parameters

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
     "user_ids" : [ {
       "user_id" : "2d032145d82546b5b83cd7a6fd7d0afc",
       "user_name" : "username1",
       "domain_id" : "0833a5736980d53b0f22c0102ffcbfc0",
       "domain_name" : "username",
       "is_domain_owner" : "false"
     } ],
     "roles_ids" : [ {
       "role_id" : "r00003"
     } ],
     "type" : 0
   }

Example Responses
-----------------

**Status code: 200**

The workspace user is added.

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

=========== ============================
Status Code Description
=========== ============================
200         The workspace user is added.
400         Bad request.
500         Internal server error.
=========== ============================
