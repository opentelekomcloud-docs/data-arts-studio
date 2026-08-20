:original_name: BatchApproveApply.html

.. _BatchApproveApply:

Reviewing Applications
======================

Function
--------

Review the application.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/applys

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                    |
   +==============+===========+========+================================================================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service.                                             |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                                              |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dlm-Type     | No        | String | Specifies the version type of the data service. The value can be SHARED or EXCLUSIVE.                                                                                                                                                                                                                          |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Type (format) of the message body. This parameter is mandatory if the message body exists. If the message body does not exist, leave this parameter blank. If the request body contains Chinese characters, use charset=utf8 to specify the Chinese character set, for example, application/json;charset=utf8. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ============ ========= ================ ====================
   Parameter    Mandatory Type             Description
   ============ ========= ================ ====================
   apply_result No        Boolean          Application result.
   apply_ids    No        Array of strings Application ID list.
   ============ ========= ================ ====================

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Approve or reject an application.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/applys

   {
     "apply_result" : false,
     "apply_ids" : [ "05b90cb05eb6bd7fcfd834dfc290c3ce" ]
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ===========================================
Status Code Description
=========== ===========================================
204         The applications are reviewed successfully.
400         Bad request
=========== ===========================================
