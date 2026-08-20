:original_name: ExportDataServiceZip.html

.. _ExportDataServiceZip:

Exporting a .zip File Containing All APIs
=========================================

Function
--------

This API is used to export a .zip file that contains all APIs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/export/zip

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Request body parameters

   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | Parameter                 | Mandatory       | Type             | Description                                                 |
   +===========================+=================+==================+=============================================================+
   | name                      | No              | String           | API name. This parameter supports fuzzy match.              |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | create_user               | No              | String           | Name of the API creator.                                    |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | description               | No              | String           | API description,                                            |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | tags                      | No              | Array of strings | API tag list                                                |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | table_name                | No              | String           | Name of the database table used by the API.                 |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | publish_status_type       | No              | String           | API publishing status                                       |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | Enumerated values include:                                  |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **PUBLISHED**: published                                 |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **NOT_PUBLISHED**: unpublished                           |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | api_specific_type_str     | No              | String           | API data obtaining mode                                     |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | Enumerated values:                                          |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **API_SPECIFIC_TYPE_CONFIGURATION**: configuration       |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **API_SPECIFIC_TYPE_SCRIPT**: script                     |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **API_SPECIFIC_TYPE_MYBATIS**: MyBatis                   |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **API_SPECIFIC_TYPE_GROOVY**: Groovy                     |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | start_time                | No              | String           | Time when the API starts to be created.                     |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | end_time                  | No              | String           | Time when the API creation ends.                            |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+
   | authorization_status_type | No              | String           | Authorization status.                                       |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | Enumerated values:                                          |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **NO_AUTHORIZATION_REQUIRED**: no authorization required |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **UNAUTHORIZED**: unauthorized                           |
   |                           |                 |                  |                                                             |
   |                           |                 |                  | -  **AUTHORIZED**: authorized                               |
   +---------------------------+-----------------+------------------+-------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------+-------------------------------------------------------------------------------------------------------------+
   | Parameter | Type | Description                                                                                                 |
   +===========+======+=============================================================================================================+
   | ``-``     | File | A .zip file that contains multiple Excel files is exported. Each Excel file contains a maximum of 200 APIs. |
   +-----------+------+-------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Export a .zip file that contains all APIs.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/export/zip

   {
     "name" : "name",
     "create_user" : "dev",
     "api_specific_type_str" : "API_SPECIFIC_TYPE_CONFIGURATION",
     "start_time" : "2024-02-29T16:00:00.000Z",
     "end_time" : "2024-07-02T15:59:59.998Z",
     "tags" : [ "111", "22", "33" ]
   }

Example Responses
-----------------

**Status code: 200**

The .zip file that contains all APIs is exported.

.. code-block::

   "xxx.zip"

Status Codes
------------

=========== =================================================
Status Code Description
=========== =================================================
200         The .zip file that contains all APIs is exported.
400         Bad request
=========== =================================================
