:original_name: ShowPathObjectById.html

.. _ShowPathObjectById:

Obtaining the Paths to a Catalog Through Its ID
===============================================

Function
--------

Obtains a path object based on the directory ID.

Obtains the path information of each layer from the root directory to the current directory based on the directory ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/servicecatalogs/{catalog_id}/layerpaths

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | catalog_id | Yes       | String | Catalog ID                                                                                                              |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                           |
   +===========+===========+=========+=======================================================================================================================================================================================+
   | limit     | No        | Integer | Maximum number of records that can be queried                                                                                                                                         |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset    | No        | Integer | Query offset, that is, X data records are skipped. The value must be **0** or an integer multiple of **limit**. If the value does not meet the requirements, it will be rounded down. |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                    |
   +==============+===========+========+================================================================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service.                                             |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                                              |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dlm-Type     | No        | String | Specifies the version type of the data service. The value can be SHARED or EXCLUSIVE.                                                                                                                                                                                                                          |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Type (format) of the message body. This parameter is mandatory if the message body exists. If the message body does not exist, leave this parameter blank. If the request body contains Chinese characters, use charset=utf8 to specify the Chinese character set, for example, application/json;charset=utf8. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------------------+--------------+
   | Parameter | Type                                                                       | Description  |
   +===========+============================================================================+==============+
   | paths     | Array of :ref:`LayerPath <showpathobjectbyid__response_layerpath>` objects | Path object. |
   +-----------+----------------------------------------------------------------------------+--------------+

.. _showpathobjectbyid__response_layerpath:

.. table:: **Table 5** LayerPath

   ========== ======= ===========
   Parameter  Type    Description
   ========== ======= ===========
   catalog_id String  Catalog ID
   name       String  Path name.
   order      Integer Path level.
   ========== ======= ===========

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain the paths to a catalog through its ID.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/servicecatalogs/51159105c7838353d2834181d978af50/layerpaths

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "paths" : [ {
       "catalog_id" : "2847131b4d5a26c5bd4bfd9d8f63f577",
       "name" : "/demo",
       "order" : 3
     }, {
       "catalog_id" : "3847131b4d565657g435536568f635342",
       "name" : "/demo2",
       "order" : 2
     }, {
       "catalog_id" : "450aa37131b4d5a26c5bcfd9d8f63j653",
       "name" : "/demo1",
       "order" : 1
     }, {
       "catalog_id" : "0",
       "name" : "/",
       "order" : 0
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Success
400         Bad request
=========== ===========
