:original_name: CreateConnections.html

.. _CreateConnections:

Creating a Data Connection
==========================

Function
--------

This API is used to create a data connection.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/data-connections

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                |
   +============+===========+========+============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>` |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------+----------------------------------------------------------------------------------------+-----------------------+
   | Parameter       | Mandatory | Type                                                                                   | Description           |
   +=================+===========+========================================================================================+=======================+
   | data_source_vos | No        | Array of :ref:`ApigDataSourceVo <createconnections__request_apigdatasourcevo>` objects | Data source structure |
   +-----------------+-----------+----------------------------------------------------------------------------------------+-----------------------+

.. _createconnections__request_apigdatasourcevo:

.. table:: **Table 4** ApigDataSourceVo

   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type    | Description                                                                                                                                                                                                |
   +================+===========+=========+============================================================================================================================================================================================================+
   | dw_name        | Yes       | String  | Data connection type, which is customized during connection creation and obtained from :ref:`Querying the Data Connection List <listdataconnections>` during connection editting.                          |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dw_type        | Yes       | String  | Data connection type, for example, DWS, DLI, Hive, RDS, or SparkSQL. You can view all data connection types on the console and obtain data connections from :ref:`Data Connections <listdataconnections>`. |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dw_config      | Yes       | Object  | Configuration items for the data connection. They vary depending on the connection type. You are advised to debug them on the console.                                                                     |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agent_id       | No        | String  | CDM cluster ID. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>`.                                                                                                   |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agent_name     | No        | String  | Agent cluster name. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>`                                                                                                |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_type       | No        | Integer | Environment type. Value **0** indicates the development environment, and **1** indicates the production environment.                                                                                       |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | qualified_name | No        | String  | Qualified data connection name                                                                                                                                                                             |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dw_id          | No        | String  | Data connection ID, which can be obtained from ListDataconnections.xml.                                                                                                                                    |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_user    | No        | String  | Data connection creator                                                                                                                                                                                    |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time    | No        | Number  | Data connection creation time, which is a timestamp                                                                                                                                                        |
   +----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_msg  String Returned error information.
   error_code String Returned error code.
   ========== ====== ===========================

**Status code: 500**

.. table:: **Table 6** Response body parameters

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
     "data_source_vos" : [ {
       "dw_config" : {
         "clusterId" : "353ff458-a560-413e-9b84-33f930cb8057",
         "clusterName" : "mrs_3x_autotest_do_not_del",
         "dbUserName" : "xxxxxx",
         "dbPassword" : "xxxxxx",
         "kmsId" : "a721616c-9a12-47b1-a805-3cfcd3e63cd7",
         "kmsName" : "KMS-1111",
         "mrsConnectionType" : "agent"
       },
       "env_type" : 0,
       "dw_type" : "HIVE",
       "dw_name" : "test_hive_01",
       "agent_id" : "91f81a12-75c5-43ce-aab8-7149ecef3b17",
       "agent_name" : "cdm-4autotest-nodelete"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

The data connection is created.

.. code-block::

   {
     "data_connection_id" : "1c868514f45447a59c41485b70ae5e05"
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
200         The data connection is created.
400         Bad request.
500         Internal server error.
=========== ===============================
