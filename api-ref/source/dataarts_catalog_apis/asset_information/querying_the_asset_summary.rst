:original_name: ShowDataProfile.html

.. _ShowDataProfile:

Querying the Asset Summary
==========================

Function
--------

Query the summary.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/asset/profile

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ============= ========= ====== ===================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ===================
   dw_id         Yes       String Data connection ID.
   db_type       Yes       String Database type.
   database_name Yes       String Database name
   table_name    Yes       String Table name
   ============= ========= ====== ===================

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------+-------------+
   | Parameter | Type                                                              | Description |
   +===========+===================================================================+=============+
   | data      | :ref:`ProfileInfo <showdataprofile__response_profileinfo>` object | Summary     |
   +-----------+-------------------------------------------------------------------+-------------+
   | rowkey    | String                                                            | Row key     |
   +-----------+-------------------------------------------------------------------+-------------+
   | status    | String                                                            | Status      |
   +-----------+-------------------------------------------------------------------+-------------+

.. _showdataprofile__response_profileinfo:

.. table:: **Table 5** ProfileInfo

   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | Parameter         | Type                                                                      | Description                             |
   +===================+===========================================================================+=========================================+
   | db_type           | String                                                                    | Database type.                          |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | cancel            | Boolean                                                                   | Whether to cancel it                    |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | table_size        | Number                                                                    | Table size                              |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | database_name     | String                                                                    | Database name                           |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | obs_common_config | String                                                                    | Specifies the OBS public configuration. |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | total_row_count   | String                                                                    | Total number of rows.                   |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | fields_name       | Array of strings                                                          | File list.                              |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | table_name        | String                                                                    | Table name                              |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | sample            | String                                                                    | Sample.                                 |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | update_date       | String                                                                    | Modification time.                      |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | row_count         | Number                                                                    | Number of sampled lines.                |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | column_count      | Number                                                                    | Number of columns.                      |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | unique            | Boolean                                                                   | Unique or not.                          |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | auto_stop         | Boolean                                                                   | The task automatically stops.           |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | time_profile      | Boolean                                                                   | Time profile                            |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | queue             | String                                                                    | Queue                                   |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | dw_id             | String                                                                    | Connection ID.                          |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | colunms_metric    | Object                                                                    | Column summary information.             |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+
   | columns_list      | Array of :ref:`columnInfo <showdataprofile__response_columninfo>` objects | Column information.                     |
   +-------------------+---------------------------------------------------------------------------+-----------------------------------------+

.. _showdataprofile__response_columninfo:

.. table:: **Table 6** columnInfo

   =========== ====== ============
   Parameter   Type   Description
   =========== ====== ============
   column_name String Column name
   description String Description.
   type        String Type
   =========== ====== ============

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "status" : "success",
     "rowkey" : "1668584342946",
     "data" : {
       "db_type" : "DWS",
       "cancel" : false,
       "table_size" : 24576,
       "database_name" : "wk",
       "obs_common_config" : null,
       "total_row_count" : 1,
       "fields_name" : [ ],
       "colunms_metric" : {
         "num" : {
           "min" : null,
           "avg" : null,
           "top" : [ [ "1", null, 1 ] ],
           "null" : 1,
           "max" : null,
           "variance" : null,
           "topcount" : 1,
           "stddev_samp" : null,
           "distinct" : "0",
           "duplicate" : 0,
           "nonNull" : "1"
         },
         "sno" : {
           "avglength" : 4,
           "distinct" : "1",
           "duplicate" : 0,
           "maxlength" : 4,
           "minlength" : 4,
           "nonNull" : "1",
           "null" : 0,
           "top" : [ [ "1", "adff", 1 ] ],
           "topcount" : 1
         }
       },
       "columns_list" : [ {
         "column_name" : "sno",
         "description" : "",
         "type" : "character varying"
       }, {
         "column_name" : "bon1",
         "description" : "",
         "type" : "integer"
       } ]
     }
   }

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         OK.
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
=========== =============
