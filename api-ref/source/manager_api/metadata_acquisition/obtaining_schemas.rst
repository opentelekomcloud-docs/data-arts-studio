:original_name: ListSchemas.html

.. _ListSchemas:

Obtaining Schemas
=================

Function
--------

This API is used to obtain schemas. Only GaussDB(DWS) and RDS for PostgreSQL support schemas. Before calling this API, check whether the data source supports the **schema** field.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/{connection_id}/schemas

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                             |
   +===============+===========+========+=========================================================================================================================+
   | project_id    | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.                   |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ============= ========= ====== ==============================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ==============================
   database_name Yes       String Database name
   limit         No        String Maximum number of data records
   offset        No        String Offset
   ============= ========= ====== ==============================

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

   +-------------+-------------------------------------------------------------------------+------------------------------------------------------------+
   | Parameter   | Type                                                                    | Description                                                |
   +=============+=========================================================================+============================================================+
   | total_count | Integer                                                                 | Number of schemas connected to the current data connection |
   +-------------+-------------------------------------------------------------------------+------------------------------------------------------------+
   | dw_id       | String                                                                  | Data connection ID.                                        |
   +-------------+-------------------------------------------------------------------------+------------------------------------------------------------+
   | database    | String                                                                  | Database name                                              |
   +-------------+-------------------------------------------------------------------------+------------------------------------------------------------+
   | schemas     | Array of :ref:`SchemasList <listschemas__response_schemaslist>` objects | Schemas                                                    |
   +-------------+-------------------------------------------------------------------------+------------------------------------------------------------+

.. _listschemas__response_schemaslist:

.. table:: **Table 5** SchemasList

   =========== ====== ==================
   Parameter   Type   Description
   =========== ====== ==================
   schema_name String Schema name
   description String Schema description
   =========== ====== ==================

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

The schema list is returned.

.. code-block::

   {
     "dw_id" : "9b18c0ad6ef5404caef4e6cbaccdae6f",
     "database" : "postgres",
     "schemas" : [ {
       "schema_name" : "dm_autotest",
       "description" : ""
     }, {
       "schema_name" : "dbadmin",
       "description" : ""
     }, {
       "schema_name" : "public",
       "description" : "gs_roach_stop_backup"
     }, {
       "schema_name" : "schame",
       "description" : ""
     }, {
       "schema_name" : "utl_file",
       "description" : ""
     }, {
       "schema_name" : "utl_raw",
       "description" : ""
     } ],
     "total_count" : 6
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
200         The schema list is returned.
400         Bad request.
500         Internal server error.
=========== ============================
