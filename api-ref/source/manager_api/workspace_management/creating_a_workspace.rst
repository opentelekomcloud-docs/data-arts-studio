:original_name: CreateManagerWorkSpace.html

.. _CreateManagerWorkSpace:

Creating a Workspace
====================

Function
--------

This API is used to create a workspace.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/workspaces/{instance_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                     |
   +=============+===========+========+=================================================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                         |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | DataArts Studio instance ID. For details about how to obtain the instance ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type   | Description                                                                                                                                                                                                                                         |
   +==========================+===========+========+=====================================================================================================================================================================================================================================================+
   | bad_record_location_name | No        | String | OBS path for storing dirty data                                                                                                                                                                                                                     |
   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description              | No        | String | Workspace description                                                                                                                                                                                                                               |
   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | eps_id                   | Yes       | String | Enterprise project ID. For details about how to obtain the enterprise project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. You can obtain the enterprise project from other workspaces of the same instance or from the console. |
   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_log_location_name    | No        | String | OBS path for job logs                                                                                                                                                                                                                               |
   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                     | Yes       | String | Workspace name                                                                                                                                                                                                                                      |
   +--------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "name" : "tesfasdfasdf",
     "description" : "",
     "eps_id" : "0",
     "job_log_location_name" : "obs://xxx/ccc/",
     "bad_record_location_name" : "obs://aaaaa111/"
   }

Example Responses
-----------------

**Status code: 200**

The workspace is created.

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

=========== =========================
Status Code Description
=========== =========================
200         The workspace is created.
400         Bad request.
500         Internal server error.
=========== =========================
