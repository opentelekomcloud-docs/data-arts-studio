:original_name: UpdateSecurityPermissionSetPermission.html

.. _UpdateSecurityPermissionSetPermission:

Updating the Rights of a Rights Set
===================================

Function
--------

This API is used to update the permissions of a permission set.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v1/{project_id}/security/permission-sets/{permission_set_id}/permissions/{permission_id}

.. table:: **Table 1** Path Parameters

   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                             |
   +===================+===========+========+=========================================================================================================================+
   | project_id        | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | permission_set_id | Yes       | String | Permission set ID.                                                                                                      |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | permission_id     | Yes       | String | Permission ID.                                                                                                          |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                       |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header). This parameter is mandatory for token authentication. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ================== ========= ================ ==========================
   Parameter          Mandatory Type             Description
   ================== ========= ================ ==========================
   dw_id              No        String           Data connection ID.
   permission_actions No        Array of strings Permission operation list.
   ================== ========= ================ ==========================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                           |
   +========================+=======================+=======================================================================================+
   | id                     | String                | id.                                                                                   |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | permission_set_id      | String                | Permission set ID.                                                                    |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | project_id             | String                | Project ID.                                                                           |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | instance_id            | String                | Instance ID.                                                                          |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | permission_type        | String                | Permission type. The options are DENY and ALLOW.                                      |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | permission_action      | String                | Permission operation list.                                                            |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | permission_actions     | Array of strings      | Permission operation list.                                                            |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | permission_action_code | Integer               | Permission operation code, which is a bitmap.                                         |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | cluster_id             | String                | Cluster ID                                                                            |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | cluster_name           | String                | Cluster name                                                                          |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | datasource_type        | String                | Data source type:                                                                     |
   |                        |                       |                                                                                       |
   |                        |                       | -  Hive data source                                                                   |
   |                        |                       |                                                                                       |
   |                        |                       | -  DWS Data Source                                                                    |
   |                        |                       |                                                                                       |
   |                        |                       | -  DLI Data Source                                                                    |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | database_name          | String                | Database name.                                                                        |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | schema_name            | String                | Specifies the schema name.                                                            |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | namespace              | String                | Namespace                                                                             |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | table_name             | String                | Table name                                                                            |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | column_name            | String                | Column name.                                                                          |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | row_level_security     | String                | Row-level policy.                                                                     |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | sync_status            | String                | Synchronization status. The value is UNKNOWN,NOT_SYNC,SYNCING,SYNC_SUCCESS,SYNC_FAIL. |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | sync_msg               | String                | Synchronization information.                                                          |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+
   | url                    | String                | URL                                                                                   |
   +------------------------+-----------------------+---------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

.. code-block::

   /v1/0833a5737480d53b2f25c010dc1a7b88/security/permission-sets/fea96c90024711b8bf8d6886407b814b/permissions/511fe36e2cc0e33a094a8bdaa4b73e55

   {
     "permission_actions" : [ "SELECT" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "cluster_id" : "4367f185-79d4-41ae-afd5-54d55176aa68",
     "cluster_name" : "mrs_3x_autotest_do_not_del",
     "column_name" : "*",
     "database_name" : "default",
     "datasource_type" : "HIVE",
     "id" : "511fe36e2cc0e33a094a8bdaa4b73e55",
     "instance_id" : "dd97167b873d4a79b2aad54d4370a3bc",
     "namespace" : null,
     "permission_action" : "SELECT",
     "permission_action_code" : 2,
     "permission_actions" : [ "SELECT" ],
     "permission_set_id" : "fea96c90024711b8bf8d6886407b814b",
     "permission_type" : "ALLOW",
     "project_id" : "0833a5737480d53b2f25c010dc1a7b88",
     "row_level_security" : null,
     "schema_name" : null,
     "sync_msg" : null,
     "sync_status" : "NOT_SYNC",
     "table_name" : "*"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
400         Bad Request
=========== ===========
