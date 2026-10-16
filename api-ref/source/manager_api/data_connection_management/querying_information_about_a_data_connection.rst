:original_name: ShowDataconnection.html

.. _ShowDataconnection:

Querying Information About a Data Connection
============================================

Function
--------

This API is used to query information about a data connection.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/data-connections/{data_connection_id}

.. table:: **Table 1** Path Parameters

   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type   | Description                                                                                                |
   +====================+===========+========+============================================================================================================+
   | data_connection_id | Yes       | String | Data connection ID, which can be obtained from the :ref:`data connection list <listdataconnections>`.      |
   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | project_id         | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>` |
   +--------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                                                                                            |
   +================+=========+========================================================================================================================================+
   | dw_name        | String  | Data connection name                                                                                                                   |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | dw_type        | String  | Data connection type                                                                                                                   |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | dw_config      | Object  | Configuration items for the data connection. They vary depending on the connection type. You are advised to debug them on the console. |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | agent_id       | String  | CDM cluster ID. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>`.                               |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | agent_name     | String  | Agent cluster name. For details about how to obtain it, see :ref:`Querying the Cluster List <listclusters>`                            |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | env_type       | Integer | Environment type. Value **0** indicates the development environment, and **1** indicates the production environment.                   |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | qualified_name | String  | Qualified data connection name                                                                                                         |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | dw_id          | String  | Data connection ID                                                                                                                     |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | create_user    | String  | Data connection creator                                                                                                                |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | create_time    | Number  | Data connection creation time, which is a timestamp                                                                                    |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | dw_catagory    | String  | Data connection type                                                                                                                   |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
   | update_type    | Integer | Update type. **0** indicates creation and **1** indicates update. The default value is **0**.                                          |
   +----------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+

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

=========== ==================================================
Status Code Description
=========== ==================================================
200         Information about the data connection is returned.
400         Bad request.
500         Internal server error.
=========== ==================================================
