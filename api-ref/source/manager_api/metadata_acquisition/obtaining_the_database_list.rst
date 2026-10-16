:original_name: ListDatabases.html

.. _ListDatabases:

Obtaining the Database List
===========================

Function
--------

This API is used to obtain the database list.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/{connection_id}/databases

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                             |
   +===============+===========+========+=========================================================================================================================+
   | project_id    | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.                   |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ====== ==============================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============================
   limit     No        String Maximum number of data records
   offset    No        String Offset
   ========= ========= ====== ==============================

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID                                                                                                                                                                                                        |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Parameter   | Type                                                                          | Description                                                  |
   +=============+===============================================================================+==============================================================+
   | total_count | Integer                                                                       | Number of databases connected to the current data connection |
   +-------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+
   | dw_id       | String                                                                        | Data connection ID.                                          |
   +-------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+
   | databases   | Array of :ref:`DatabasesList <listdatabases__response_databaseslist>` objects | Database list                                                |
   +-------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+

.. _listdatabases__response_databaseslist:

.. table:: **Table 5** DatabasesList

   ============= ====== ====================
   Parameter     Type   Description
   ============= ====== ====================
   database_name String Database name
   description   String Database description
   ============= ====== ====================

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

**Status code: 200**

The database list is returned.

.. code-block::

   {
     "dw_id" : "f6ce0c0de8f14ba8b7fbf23486b8ec16",
     "databases" : [ {
       "database_name" : "dlcatalog_2fe5",
       "description" : null
     }, {
       "database_name" : "dlcatalog_3e24",
       "description" : null
     }, {
       "database_name" : "dlcatalog_677a",
       "description" : null
     }, {
       "database_name" : "dlcatalog_86e4",
       "description" : null
     }, {
       "database_name" : "dlcatalog_ced5",
       "description" : null
     } ],
     "total_count" : 21
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

=========== ==============================
Status Code Description
=========== ==============================
200         The database list is returned.
400         Bad request.
500         Internal server error.
=========== ==============================
