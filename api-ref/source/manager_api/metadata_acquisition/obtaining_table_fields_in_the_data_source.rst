:original_name: ListColumns.html

.. _ListColumns:

Obtaining Table Fields in the Data Source
=========================================

Function
--------

This API is used to obtain table fields in the data source.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/{connection_id}/datatables/{table_id}/columns

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                             |
   +===============+===========+========+=========================================================================================================================+
   | project_id    | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.                   |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | table_id      | Yes       | String | Table ID                                                                                                                |
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

   +-------------+-------------------------------------------------------------------------+---------------------------------------+
   | Parameter   | Type                                                                    | Description                           |
   +=============+=========================================================================+=======================================+
   | table_id    | String                                                                  | ID of a data table                    |
   +-------------+-------------------------------------------------------------------------+---------------------------------------+
   | total_count | Integer                                                                 | Number of fields in the current table |
   +-------------+-------------------------------------------------------------------------+---------------------------------------+
   | columns     | Array of :ref:`ColumnsList <listcolumns__response_columnslist>` objects | Field list                            |
   +-------------+-------------------------------------------------------------------------+---------------------------------------+

.. _listcolumns__response_columnslist:

.. table:: **Table 5** ColumnsList

   ============= ======= ==================================
   Parameter     Type    Description
   ============= ======= ==================================
   comment       String  Field comment
   column_name   String  Field name
   column_type   String  Field type
   seq_number    Integer Field sequence
   primary       Boolean Whether the field is a primary key
   partition_col Boolean Whether to split fields
   ============= ======= ==================================

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

The list of fields is returned.

.. code-block::

   {
     "columns" : [ {
       "comment" : "",
       "column_name" : "age",
       "column_type" : "integer",
       "seq_number" : 2,
       "primary" : false,
       "partition_col" : false
     }, {
       "comment" : "",
       "column_name" : "address",
       "column_type" : "character varying",
       "seq_number" : 3,
       "primary" : false,
       "partition_col" : false
     }, {
       "comment" : "",
       "column_name" : "phonenum",
       "column_type" : "character varying",
       "seq_number" : 4,
       "primary" : false,
       "partition_col" : false
     } ],
     "total_count" : 7,
     "table_id" : "NativeTable-9b18c0ad6ef5404caef4e6cbaccdae6f-postgres-dm_autotest-QQQQQQQstudents_infoweq"
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
200         The list of fields is returned.
400         Bad request.
500         Internal server error.
=========== ===============================
