:original_name: ImportCatalogs.html

.. _ImportCatalogs:

Importing subjects
==================

Function
--------

Used to import themes.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/design/catalogs/action

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                              |
   +=================+=================+=================+==========================================+
   | action-id       | Yes             | LIST<STRING>    | Action to be performed.                  |
   |                 |                 |                 |                                          |
   |                 |                 |                 | Options:                                 |
   |                 |                 |                 |                                          |
   |                 |                 |                 | -  start-import: The import starts.      |
   +-----------------+-----------------+-----------------+------------------------------------------+
   | skip_exist      | No              | Boolean         | Whether to overwrite the existing theme. |
   +-----------------+-----------------+-----------------+------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header).                                  |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This field is mandatory for authentication using tokens.                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace       | Yes             | String          | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Project-Id    | No              | String          | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                            |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is mandatory for API requests that use AK/SK authentication in multi-project scenarios.                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Default value: application/json;charset=UTF-8                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is optional. If the body is available, this parameter is mandatory. If the body is unavailable, you do not need to set this parameter or verify it. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** FormData parameters

   +-----------+-----------+------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                                                                                |
   +===========+===========+======+============================================================================================================================+
   | file      | Yes       | File | Excel file used for importing themes. The file size must be less than 4 MB and the number of lines must be less than 3000. |
   +-----------+-----------+------+----------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+----------------------------------------------------+----------------------------+
   | Parameter | Type                                               | Description                |
   +===========+====================================================+============================+
   | data      | :ref:`data <importcatalogs__response_data>` object | Returned data information. |
   +-----------+----------------------------------------------------+----------------------------+

.. _importcatalogs__response_data:

.. table:: **Table 6** data

   ========= ====== ====================================
   Parameter Type   Description
   ========= ====== ====================================
   uuid      String Unique ID returned by the import API
   ========= ====== ====================================

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   data      Object Returned data information.
   ========= ====== ==========================

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   data      Object Returned data information.
   ========= ====== ==========================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   data      Object Returned data information.
   ========= ====== ==========================

Example Requests
----------------

Upload the theme Excel file and submit it through the form. The file is a specific Excel file.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/design/catalogs/action?action-id=start-import&skip_exist=false

Example Responses
-----------------

**Status code: 200**

Success. The returned data is the UUID of the import task. You can query the import result based on the UUID.

.. code-block::

   {
     "data" : {
       "uuid" : "82f70d35-f61a-46dc-a245-0b86905e82d1"
     }
   }

Status Codes
------------

+-------------+---------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                   |
+=============+===============================================================================================================+
| 200         | Success. The returned data is the UUID of the import task. You can query the import result based on the UUID. |
+-------------+---------------------------------------------------------------------------------------------------------------+
| 400         | BadRequest                                                                                                    |
+-------------+---------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                                                  |
+-------------+---------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden                                                                                                     |
+-------------+---------------------------------------------------------------------------------------------------------------+
