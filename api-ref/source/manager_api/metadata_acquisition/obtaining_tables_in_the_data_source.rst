:original_name: ListDataTables.html

.. _ListDataTables:

Obtaining Tables in the Data Source
===================================

Function
--------

This API is used to obtain tables in the data source.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/{connection_id}/datatables

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                             |
   +===============+===========+========+=========================================================================================================================+
   | project_id    | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.                   |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ============= ========= ====== =================================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =================================
   database_name Yes       String Database name
   table_name    No        String Names of the tables to be queried
   limit         No        String Maximum number of data records
   offset        No        String Offset
   ============= ========= ====== =================================

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

   +-------------+--------------------------------------------------------------------------+------------------------------------------+
   | Parameter   | Type                                                                     | Description                              |
   +=============+==========================================================================+==========================================+
   | total_count | Integer                                                                  | Number of tables in the current database |
   +-------------+--------------------------------------------------------------------------+------------------------------------------+
   | tables      | Array of :ref:`TablesList <listdatatables__response_tableslist>` objects | List of tables                           |
   +-------------+--------------------------------------------------------------------------+------------------------------------------+

.. _listdatatables__response_tableslist:

.. table:: **Table 5** TablesList

   +---------------+---------+---------------------------------------------------------------+
   | Parameter     | Type    | Description                                                   |
   +===============+=========+===============================================================+
   | table_name    | String  | Table name                                                    |
   +---------------+---------+---------------------------------------------------------------+
   | table_id      | String  | ID of a data table                                            |
   +---------------+---------+---------------------------------------------------------------+
   | table_name_cn | String  | Table name                                                    |
   +---------------+---------+---------------------------------------------------------------+
   | columns       | String  | Fields in a table                                             |
   +---------------+---------+---------------------------------------------------------------+
   | dw_id         | String  | Data connection ID.                                           |
   +---------------+---------+---------------------------------------------------------------+
   | dw_name       | String  | Data connection name                                          |
   +---------------+---------+---------------------------------------------------------------+
   | dw_type       | String  | Data connection type                                          |
   +---------------+---------+---------------------------------------------------------------+
   | database_name | String  | Database name                                                 |
   +---------------+---------+---------------------------------------------------------------+
   | schema_name   | String  | Schema name                                                   |
   +---------------+---------+---------------------------------------------------------------+
   | life_cycle    | Integer | Table lifecycle                                               |
   +---------------+---------+---------------------------------------------------------------+
   | description   | String  | Table description                                             |
   +---------------+---------+---------------------------------------------------------------+
   | user_id       | String  | User ID. You can obtain it from the user information on IAM.  |
   +---------------+---------+---------------------------------------------------------------+
   | user_name     | String  | Username                                                      |
   +---------------+---------+---------------------------------------------------------------+
   | project_id    | String  | Data connection ID.                                           |
   +---------------+---------+---------------------------------------------------------------+
   | create_time   | String  | Table creation time                                           |
   +---------------+---------+---------------------------------------------------------------+
   | table_size    | Integer | Table size                                                    |
   +---------------+---------+---------------------------------------------------------------+
   | total_count   | Integer | Total number of tables that match the current search criteria |
   +---------------+---------+---------------------------------------------------------------+
   | is_valid      | Integer | Whether the table is valid                                    |
   +---------------+---------+---------------------------------------------------------------+
   | extra_setting | String  | Extra settings for the table                                  |
   +---------------+---------+---------------------------------------------------------------+
   | partitioned   | Boolean | Whether to partition data                                     |
   +---------------+---------+---------------------------------------------------------------+

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

The list of tables is returned.

.. code-block::

   {
     "tables" : [ {
       "description" : null,
       "table_id" : "NativeTable-9b18c0ad6ef5404caef4e6cbaccdae6f-postgres-dm_autotest",
       "table_name" : "test01",
       "table_name_cn" : null,
       "columns" : null,
       "dw_id" : "9b18c0ad6ef5404caef4e6cbaccdae6f",
       "dw_name" : "dws_test",
       "dw_type" : "DWS",
       "database_name" : "postgres",
       "schema_name" : "dm_autotest",
       "life_cycle" : 0,
       "user_id" : "username",
       "user_name" : null,
       "project_id" : null,
       "create_time" : null,
       "table_size" : 0,
       "total_count" : 15,
       "is_valid" : 1,
       "extra_setting" : null,
       "partitioned" : true
     } ],
     "total_count" : 15
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
200         The list of tables is returned.
400         Bad request.
500         Internal server error.
=========== ===============================
