:original_name: ListAllCatalogList.html

.. _ListAllCatalogList:

Obtaining the List of APIs and Catalogs in a Catalog
====================================================

Function
--------

This API is used to obtain the list of APIs and catalogs in the current catalog. The list is displayed in the data format of the catalog.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/servicecatalogs/{catalog_id}/detail

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | catalog_id | Yes       | String | Catalog ID                                                                                                              |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+----------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                    |
   +===========+===========+=========+================================================================+
   | offset    | No        | Integer | Query start coordinate, that is, skipping the first X records. |
   +-----------+-----------+---------+----------------------------------------------------------------+
   | limit     | No        | Integer | Maximum number of records that can be queried                  |
   +-----------+-----------+---------+----------------------------------------------------------------+

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

   +--------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter    | Type                                                                                                 | Description                                                 |
   +==============+======================================================================================================+=============================================================+
   | total        | Integer                                                                                              | Total number of data records that meet the search criteria. |
   +--------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | api_catalogs | Array of :ref:`RecordForGetAllCatalog <listallcataloglist__response_recordforgetallcatalog>` objects | App list returned this time.                                |
   +--------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _listallcataloglist__response_recordforgetallcatalog:

.. table:: **Table 5** RecordForGetAllCatalog

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | catalog_id            | String                | Catalog ID            |
   +-----------------------+-----------------------+-----------------------+
   | pid                   | String                | Parent category ID.   |
   +-----------------------+-----------------------+-----------------------+
   | name                  | String                | Name.                 |
   +-----------------------+-----------------------+-----------------------+
   | description           | String                | Catalog description.  |
   +-----------------------+-----------------------+-----------------------+
   | api_catalog_type      | String                | Catalog type          |
   |                       |                       |                       |
   |                       |                       | Enumerated values:    |
   |                       |                       |                       |
   |                       |                       | -  **CATALOG**        |
   |                       |                       |                       |
   |                       |                       | -  **API**            |
   +-----------------------+-----------------------+-----------------------+
   | create_time           | Long                  | Creation time.        |
   +-----------------------+-----------------------+-----------------------+
   | create_user           | String                | Creator.              |
   +-----------------------+-----------------------+-----------------------+
   | update_time           | Long                  | Update time.          |
   +-----------------------+-----------------------+-----------------------+
   | update_user           | String                | Updater.              |
   +-----------------------+-----------------------+-----------------------+

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

Obtain the list of APIs and catalogs in the catalog whose ID is **51159105c7838353d2834181d978af50**.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/servicecatalogs/51159105c7838353d2834181d978af50/detail

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total" : 1,
     "api_catalogs" : [ {
       "catalog_id" : "2847131b4d5a26c5bd4bfd9d8f63f577",
       "pid" : "8c9850726a1ee050be2b67e43c688870",
       "name" : "demo",
       "description" : "this is a demo",
       "api_catalog_type" : "CATALOG",
       "create_time" : 1578284788000,
       "create_user" : "Tom",
       "update_time" : 1578284788000,
       "update_user" : "Tom"
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
