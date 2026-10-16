:original_name: ListDataconnections.html

.. _ListDataconnections:

Querying the Data Source List
=============================

Function
--------

This API is used to query the data source list.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/data-connections

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                |
   +============+===========+========+============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>` |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                      |
   +===========+===========+========+==================================================================================================================================+
   | name      | No        | String | Data connection name. It can be obtained from the return result of :ref:`Querying a Data Connection List <listdataconnections>`. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | type      | No        | String | Data connection type. It can be obtained from the return result of :ref:`Querying a Data Connection List <listdataconnections>`. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | limit     | No        | String | Maximum number of data connections that can be queried each time.                                                                |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | offset    | No        | String | Page number of data connections queried each time.                                                                               |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory for :ref:`token authentication <dataartsstudio_02_0010>`. Call the "Obtaining the User Token" API of IAM to obtain the value of **X-Subject-Token** in the response header. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                 |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                          | Description                                                                                                        |
   +=======================+===============================================================================================+====================================================================================================================+
   | count                 | Integer                                                                                       | Number of data connections returned on the current page                                                            |
   +-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | max_records           | Integer                                                                                       | Total number of records returned. It is the maximum number of data connections that can be created in a workspace. |
   +-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | data_connection_lists | Array of :ref:`ApigDataSourceView <listdataconnections__response_apigdatasourceview>` objects | Returned data connection list                                                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _listdataconnections__response_apigdatasourceview:

.. table:: **Table 5** ApigDataSourceView

   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                 |
   +================+========+=============================================================================================================+
   | dw_name        | String | Data connection name                                                                                        |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | dw_type        | String | Data connection type                                                                                        |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | create_user    | String | Data connection creator                                                                                     |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | create_time    | Number | Data connection creation time, which is a timestamp                                                         |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | agent_id       | String | CDM cluster ID. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>`.    |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | agent_name     | String | Agent cluster name. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>` |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | dw_id          | String | Data connection ID                                                                                          |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | qualified_name | String | Qualified data connection name                                                                              |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+
   | description    | String | Data connection description                                                                                 |
   +----------------+--------+-------------------------------------------------------------------------------------------------------------+

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

=========== =====================================
Status Code Description
=========== =====================================
200         The data connection list is returned.
400         Bad request.
500         Internal server error.
=========== =====================================
