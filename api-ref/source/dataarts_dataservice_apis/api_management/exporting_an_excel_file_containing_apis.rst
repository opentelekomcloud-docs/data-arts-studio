:original_name: ExportDataServiceExcel.html

.. _ExportDataServiceExcel:

Exporting an Excel File Containing APIs
=======================================

Function
--------

This API is used to export an Excel file that contains APIs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/export/excel

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

.. table:: **Table 3** Request body parameters

   ========= ========= ================ ==================
   Parameter Mandatory Type             Description
   ========= ========= ================ ==================
   [items]   Yes       Array of strings API Export ID List
   ========= ========= ================ ==================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------+--------------------------------------------------------------------------------------+
   | Parameter | Type | Description                                                                          |
   +===========+======+======================================================================================+
   | ``-``     | File | The Excel file that contains APIs and is smaller than 4 MB is successfully exported. |
   +-----------+------+--------------------------------------------------------------------------------------+

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

Export an Excel file that contains APIs.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/export/excel

   [ "6b9e682fd6d0ef7c0f674701adb20762", "42505b429b53b42a9b535640617d9b17" ]

Example Responses
-----------------

**Status code: 200**

The Excel file is successfully exported.

.. code-block::

   "xxx.xlsx"

Status Codes
------------

=========== ========================================
Status Code Description
=========== ========================================
200         The Excel file is successfully exported.
400         Bad request
=========== ========================================
