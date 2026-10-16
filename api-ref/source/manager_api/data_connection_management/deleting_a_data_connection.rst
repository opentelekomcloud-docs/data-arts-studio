:original_name: DeleteDataconnection.html

.. _DeleteDataconnection:

Deleting a Data Connection
==========================

Function
--------

This API is used to delete a data connection.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v1/{project_id}/data-connections/{data_connection_id}

.. table:: **Table 1** Path Parameters

   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type   | Description                                                                                                |
   +====================+===========+========+============================================================================================================+
   | data_connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.      |
   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | project_id         | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>` |
   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                 |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

**Status code: 500**

.. table:: **Table 4** Response body parameters

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

**Status code: 200**

The data connection is deleted.

.. code-block::

   {
     "is_success" : true,
     "message" : null
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

=========== ===============================
Status Code Description
=========== ===============================
200         The data connection is deleted.
400         Bad request.
500         Internal server error.
=========== ===============================
