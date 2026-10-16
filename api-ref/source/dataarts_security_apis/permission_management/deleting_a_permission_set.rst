:original_name: DeleteSecurityPermissionSet.html

.. _DeleteSecurityPermissionSet:

Deleting a Permission Set
=========================

Function
--------

Deletes a privilege set.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v1/{project_id}/security/permission-sets/{permission_set_id}

.. table:: **Table 1** Path Parameters

   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                             |
   +===================+===========+========+=========================================================================================================================+
   | project_id        | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | permission_set_id | Yes       | String | Permission set ID.                                                                                                      |
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

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

.. code-block::

   /v1/0833a5737480d53b2f25c010dc1a7b88/security/permission-sets/fea96c90024711b8bf8d6886407b814b

Example Responses
-----------------

None

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
204         No Content
400         Bad Request
=========== ===========
