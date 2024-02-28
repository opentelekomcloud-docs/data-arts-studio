:original_name: dataartsstudio_02_0097.html

.. _dataartsstudio_02_0097:

Creating a Script
=================

Function
--------

This API is used to create a script. Currently, the following script types are supported: DLI SQL, Flink SQL, RDS SQL, Spark SQL, Hive SQL, DWS SQL, Shell, Presto SQL, ClickHouse SQL, HetuEngine SQL, Python, Spark Python, and Impala SQL.

URI
---

-  URI format

   POST /v1/{project_id}/scripts

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                             |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default. |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

.. table:: **Table 3** Script parameters

   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   +=================+=================+=====================+=================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | name            | Yes             | String              | Script name. The name contains a maximum of 128 characters, including only letters, numbers, hyphens (-), and periods (.). The script name must be unique.                                                                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String              | Script type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                     | -  FlinkSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                     | -  DLISQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  SparkSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                     | -  HiveSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                     | -  DWSSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  RDSSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  Shell                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                     | -  PRESTO                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  ClickHouseSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                     | -  HetuEngineSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                     | -  PYTHON                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  ImpalaSQL                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                     | -  Spark Python                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String              | Script content. A maximum of 4 MB is supported.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | No              | String              | Directory for storing the script.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                     | Access the DataArts Studio console and choose **Data Development**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory.                                                                                                                                                                                                       |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | connectionName  | No              | String              | Name of the connection associated with the script. This parameter is mandatory when **type** is set to **DLISQL**, **SparkSQL**, **HiveSQL**, **DWSSQL**, **Shell**, **PRESTO**, **ClickHouseSQL**, **HetuEngineSQL**, **RDSSQL**, **ImpalaSQL**, **Spark Python**, or **PYTHON**. To obtain the existing connections, refer to the instructions in :ref:`Querying a Connection List (to Be Taken Offline) <dataartsstudio_02_0051>`. By default, this parameter is left blank. |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database        | No              | String              | Database associated with an SQL statement. This parameter is available only when **type** is set to **DLISQL**, **SparkSQL**, **HiveSQL**, **DWSSQL**, **PRESTO**, **RDSSQL**, **ClickHouseSQL**, **ImpalaSQL**, or **HetuEngineSQL**.                                                                                                                                                                                                                                          |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                     | -  If **type** is set to **DLI SQL**, obtain database information by calling the API for querying all databases in the *Data Lake Insight API Reference*.                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     | -  This parameter is mandatory when the script is not of any type listed.                                                                                                                                                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | queueName       | Yes             | String              | Queue name of the DLI resource. This parameter is available only when **type** is set to **DLISQL**. You can obtain the queue information by calling the API for "Querying All Queues" in the *Data Lake Insight API Reference*. By default, this parameter is left blank.                                                                                                                                                                                                      |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | configuration   | No              | map <String,Object> | Configuration defined by a user for the job. This parameter is available only when **type** is set to **DLISQL**. For details about the supported configuration items, see conf parameter description in the "Submitting a SQL Job" section of the *Data Lake Insight API Reference*. By default, this parameter is left blank.                                                                                                                                                 |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String              | The description contains a maximum of 255 characters.                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | targetStatus    | No              | String              | This parameter is required if the review function is enabled. It indicates the target status of the script. The value can be **SAVED**, **SUBMITTED**, or **PRODUCTION**.                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                     | -  **SAVED** indicates that the script is saved but cannot be scheduled or executed. It can be executed only after submitted and approved.                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                     | -  **SUBMITTED** indicates that the script is automatically submitted after it is saved and can be executed after it is approved.                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                     | -  **PRODUCTION** indicates that the script can be directly executed after it is created. Note: Only the workspace administrator can create scripts in the **PRODUCTION** state.                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | approvers       | No              | List<JobApprover>   | Script approver. This parameter is required if the review function is enabled. For details, see :ref:`Table 4 <dataartsstudio_02_0097__table943565132314>`.                                                                                                                                                                                                                                                                                                                     |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0097__table943565132314:

.. table:: **Table 4** Approver attributes

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   approverName Yes       String Approver name
   ============ ========= ====== =============

Response Parameters
-------------------

None.

Example Request
---------------

Create a script named **echoTimeShell** whose type is Shell, content is **echo a**, and associated connection is **con**.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts
   {
       "name": "echoTimeShell",
       "type": "Shell",
       "content": "echo a",
       "connectionName": "con"
   }

Create a script when the review function is enabled.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts
   {
       "name": "echoTimeShell",
       "type": "Shell",
       "content": "echo a",
       "connectionName": "con",
       "targetStatus":"SUBMITTED",
       "approvers": [
         {
           "approverName": "userName1"
         },
         {
           "approverName": "userName2"
         }
       ]
   }

Example Response
----------------

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6247",
          "error_msg":"The script type is not specified."
      }

Status Code
-----------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
