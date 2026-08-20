:original_name: ImportModels.html

.. _ImportModels:

Import models, relationship modeling, dimension modeling, code tables, service indicators, and process architecture.
====================================================================================================================

Function
--------

Import models, relationship modeling, dimension modeling, code tables, service indicators, and process architecture.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/design/models/action

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | action-id       | Yes             | String          | Action to be executed. Select an import action based on the imported object.                                                                                       |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | Options:                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_relation: Import a relationship model (logical entity/physical table).                                                                                   |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_dimension: imports dimension tables and fact tables.                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_codetable: import lookup table                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_datastandard: data import standard                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_bizmetric: imports service metrics.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_bizcatalog: imports the BPA.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_atomic: imports atomic metrics.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_derivative: imports derivative indicators.                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_compound: Import a compound metric.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | -  import_aggregation: Import the summary table.                                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_id        | No              | String          | ID of a relational modeling model. This parameter is mandatory when a model (import_relation) is imported.                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory_id    | No              | String          | ID of the target directory. This parameter is optional and takes effect for importing a lookup table (import_datastandard) or data standard (import_datastandard). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | skip_exist      | No              | Boolean         | Whether to overwrite the existing entity.                                                                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header).                                         |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | This field is mandatory for authentication using tokens.                                                                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace       | Yes             | String          | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Project-Id    | No              | String          | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                                   |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | This parameter is mandatory for API requests that use AK/SK authentication in multi-project scenarios.                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Default value: application/json;charset=UTF-8                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | This parameter is optional. If the body is available, this parameter is mandatory. If the body is unavailable, you do not need to set this parameter or verify it.        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Language      | No              | String          | Default value: **en-us**.                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                           |
   |                 |                 |                 | This parameter is optional, but is mandatory for import and export APIs. Available options include **zh-cn** and **en-us**, indicating Chinese and English, respectively. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** FormData parameters

   +-----------+-----------+------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                                                                       |
   +===========+===========+======+===================================================================================================================+
   | file      | Yes       | File | The size of the Excel file to be imported must be less than 4 MB, and the number of lines must be less than 3000. |
   +-----------+-----------+------+-------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+--------------------------------------------------+----------------------------+
   | Parameter | Type                                             | Description                |
   +===========+==================================================+============================+
   | data      | :ref:`data <importmodels__response_data>` object | Returned data information. |
   +-----------+--------------------------------------------------+----------------------------+

.. _importmodels__response_data:

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

Upload the model Excel file and submit it through the form. The file is a specific file.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/design/models/action?action-id=import_relation&skip_exist=false&model_id=1208730797675311104

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
