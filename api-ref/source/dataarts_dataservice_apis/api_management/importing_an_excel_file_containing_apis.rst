:original_name: ImportDataServiceExcel.html

.. _ImportDataServiceExcel:

Importing an Excel File Containing APIs
=======================================

Function
--------

This API is used to import an Excel file that contains APIs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/import/excel

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                  |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dlm-Type     | No        | String | Specifies the version type of the data service. The value can be SHARED or EXCLUSIVE.                                                                                                                                                                              |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Type (format) of the message body. Here, the file is imported. The value is multipart/form-data.                                                                                                                                                                   |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** FormData parameters

   +-----------+-----------+------+------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                                  |
   +===========+===========+======+==============================================================================+
   | file      | Yes       | File | Import an Excel file that contains APIs. The file must be smaller than 4 MB. |
   +-----------+-----------+------+------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   job_id    String Returned data information.
   ========= ====== ==========================

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

Import an Excel file that contains APIs.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/import/excel

Example Responses
-----------------

**Status code: 200**

The Excel file is imported successfully.

.. code-block::

   {
     "job_id" : "252041f9838e8e5ea2e0e7317d5bcaf3"
   }

Status Codes
------------

=========== ========================================
Status Code Description
=========== ========================================
200         The Excel file is imported successfully.
400         Bad request
=========== ========================================
