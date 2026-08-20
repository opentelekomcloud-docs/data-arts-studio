:original_name: changeResource.html

.. _changeResource:

Changing Specifications
=======================

Function
--------

This API is used to change specifications.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/change-resource

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type    | Description                                                                                                                                                                                    |
   +====================+===========+=========+================================================================================================================================================================================================+
   | change_mode        | Yes       | Integer | Specifies the specification change type. The value can be 10 (upgrading specifications), 30 (degrading specifications), 40 (renewal), 60 (expanding specifications), or 70 (switching the OS). |
   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id        | Yes       | String  | Resource ID                                                                                                                                                                                    |
   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_spec_code | Yes       | String  | Resource specifications code, which can be obtained from :ref:`Obtaining the Instance List <listdataartsstudioinstances>`.                                                                     |
   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | product_id         | No        | String  | Product ID, which can be obtained from :ref:`Obtaining the Instance List <listdataartsstudioinstances>`.                                                                                       |
   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | promotion_info     | No        | String  | Promotion information, which can be obtained from :ref:`Obtaining the Instance List <listdataartsstudioinstances>`.                                                                            |
   +--------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "resource_id" : "2b6c183a606f4983b503b6427ba5db30",
     "product_id" : "",
     "resource_spec_code" : "dayu.experience",
     "change_mode" : 30
   }

Example Responses
-----------------

**Status code: 200**

The request for changing specifications is successful.

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

=========== ======================================================
Status Code Description
=========== ======================================================
200         The request for changing specifications is successful.
400         Bad request.
500         Internal server error.
=========== ======================================================
