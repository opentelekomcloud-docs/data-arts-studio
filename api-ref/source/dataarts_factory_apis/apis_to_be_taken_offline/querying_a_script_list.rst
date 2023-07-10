:original_name: dataartsstudio_02_0100.html

.. _dataartsstudio_02_0100:

Querying a Script List
======================

Function
--------

This API is used to query the script list. A maximum of 1000 scripts can be returned for each query.

URI
---

-  URI format

   GET /v1/{project_id}/scripts?offset={offset}&limit={limit}&scriptName={scriptName}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                              |
      +=================+=================+=================+==========================================================================================================================+
      | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | The maximum number of records on each page. The value ranges from 1 to 100.                                              |
      |                 |                 |                 |                                                                                                                          |
      |                 |                 |                 | Default value: **10**                                                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Start page of the paging list. The default value is **0**. The value must be greater than or equal to **0**.             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | scriptName      | No              | String          | Script name.                                                                                                             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                             |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default. |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response
--------

.. table:: **Table 3** Response parameters

   ========= ========= ============ ============================
   Parameter Mandatory Type         Description
   ========= ========= ============ ============================
   total     Yes       Integer      The total number of scripts.
   scripts   Yes       List<Script> A list of scripts.
   ========= ========= ============ ============================

.. table:: **Table 4** Script parameters

   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                | Description                                                                                                                                                                                                                                                                                                                                                |
   +=================+=================+=====================+============================================================================================================================================================================================================================================================================================================================================================+
   | name            | Yes             | String              | Script name. The name contains a maximum of 128 characters, including only letters, numbers, hyphens (-), and periods (.). The script name must be unique.                                                                                                                                                                                                 |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String              | Script type.                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                     | -  FlinkSQL                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                     | -  DLISQL                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                     | -  SparkSQL                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                     | -  HiveSQL                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                     | -  DWSSQL                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                     | -  RDSSQL                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                     | -  Shell                                                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                     | -  PRESTO                                                                                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String              | Script content. A maximum of 64 KB is supported.                                                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | No              | String              | Directory for storing the script.                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                     | Access the DataArts Studio console and choose **DataArts Factory**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory.                                                                                  |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | connectionName  | No              | String              | Name of the connection associated with the script. This parameter is mandatory when **type** is set to **DLISQL**, **SparkSQL**, **HiveSQL**, **DWSSQL**, **Shell**, or **PRESTO**. To obtain the existing connections, refer to the instructions in :ref:`Querying a Connection List <dataartsstudio_02_0051>`. By default, this parameter is left blank. |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database        | No              | String              | Database associated with an SQL statement. This parameter is available only when **type** is set to **DLISQL**, **SparkSQL**, **HiveSQL**, **DWSSQL**, or **PRESTO**.                                                                                                                                                                                      |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                     | -  If **type** is set to **DLISQL**, obtain database information by calling the API for "Querying All Databases" in the *Data Lake Insight API Reference*.                                                                                                                                                                                                 |
   |                 |                 |                     | -  If **type** is not set to **DLISQL**, connect to the cluster in JDBC mode to query database information. By default, this parameter is left blank.                                                                                                                                                                                                      |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | queueName       | No              | String              | Queue name of the DLI resource. This parameter is available only when **type** is set to **DLISQL**. You can obtain the queue information by calling the API for "Querying All Queues" in the *Data Lake Insight API Reference*. By default, this parameter is left blank.                                                                                 |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | configuration   | No              | map <String,Object> | Configuration defined by a user for the job. This parameter is available only when **type** is set to **DLISQL**. For details about the supported configuration items, see conf parameter description in the "Submitting a SQL Job" section of the *Data Lake Insight API Reference*. By default, this parameter is left blank.                            |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String              | Description of the script. The description contains a maximum of 255 characters.                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+---------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example
-------

Query a script list.

-  Request

   .. code-block:: text

      GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "total": 1,
          "scripts": [
              {
                  "configuration": {},
                  "connectionName": "mrs_spark",
                  "content": "SELECT 1;",
                  "database": "aaa",
                  "description": "",
                  "directory": "/",
                  "name": "mrs_spark_sql",
                  "type": "SparkSQL"
              }
          ]
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.3051",
          "error_msg":"The request parameter is invalid."
      }
