:original_name: dataartsstudio_02_0106.html

.. _dataartsstudio_02_0106:

Importing Connections (to Be Taken Offline)
===========================================

.. note::

   The connection management capability is provided by Management Center. APIs of Management Center are recommended.

Function
--------

This API is used to import one or more connection files from OBS to the Data Development module. Before using this API, store connection files in OBS buckets.

URI
---

-  URI format

   POST /v1/{project_id}/connections/import

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

Request parameters

+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter       | Mandatory       | Type            | Description                                                                                                                                                                           |
+=================+=================+=================+=======================================================================================================================================================================================+
| path            | Yes             | String          | With OBS deployed: OBS path for storing the connection definition file. For details about the format of the job definition file, see the response message of the exported connection. |
|                 |                 |                 |                                                                                                                                                                                       |
|                 |                 |                 | Without OBS deployed: local path for storing the connection definition file.                                                                                                          |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| params          | No              | List<Params>    | Connection parameter. By default, this parameter is left blank.                                                                                                                       |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sameNamePolicy  | No              | String          | Policy for specifying how to handle duplicate names. The options are as follows:                                                                                                      |
|                 |                 |                 |                                                                                                                                                                                       |
|                 |                 |                 | -  SKIP                                                                                                                                                                               |
|                 |                 |                 |                                                                                                                                                                                       |
|                 |                 |                 | -  OVERWRITE                                                                                                                                                                          |
|                 |                 |                 |                                                                                                                                                                                       |
|                 |                 |                 |    Default value: **SKIP**                                                                                                                                                            |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Params connection parameters

+-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter       | Mandatory       | Type            | Description                                                                                                                                                           |
+=================+=================+=================+=======================================================================================================================================================================+
| name            | Yes             | String          | Name of a connection.                                                                                                                                                 |
+-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| type            | Yes             | String          | Connection type.                                                                                                                                                      |
+-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| params          | No              | Map<String,Stri | Connection parameter. For details about parameter names, see the description of each type of connection configuration item. By default, this parameter is left blank. |
|                 |                 |                 |                                                                                                                                                                       |
|                 |                 | ng>             |                                                                                                                                                                       |
+-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

+-----------+-----------+--------+---------------------------------------------------------------------------------------------+
| Parameter | Mandatory | Type   | Description                                                                                 |
+===========+===========+========+=============================================================================================+
| taskId    | Yes       | String | ID of the task. Used to call the API for querying system tasks to obtain the import status. |
+-----------+-----------+--------+---------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections/import
   {
       "path":"obs://00zyx/2019-07-02/DLF_All_DataConnections.zip",
       "sameNamePolicy":"OVERWRITE",
       "params":[
           {
               "name":"DWS",
               "type":"DWS",
               "params":{
                   "clusterName":"cluster1"
               }
           },
           {
               "name":"hive",
               "type":"HIVE",
               "params":{
                   "clusterName":"mrs_ymcc",
                   "connectionMethod":"agent",
                   "userName":"admin",
                   "agentName":"cdm-donotdelete",
                   "kmsKey":"KMS-42ab"
               }
           }
       ]
   }

Example Response
----------------

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "taskId":"008aae2e675933c7016759418e870000"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0815",
          "error_msg":"Fail to read OBS file."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
