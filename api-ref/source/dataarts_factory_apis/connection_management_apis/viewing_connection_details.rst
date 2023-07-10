:original_name: dataartsstudio_02_0052.html

.. _dataartsstudio_02_0052:

Viewing Connection Details
==========================

Function
--------

This API is used to query configuration details of a specific connection.

URI
---

-  URI format

   GET /v1/{project_id}/connections/{connection_name}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory | Type   | Description                                                                                                              |
      +=================+===========+========+==========================================================================================================================+
      | project_id      | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | connection_name | Yes       | String | Name of a connection.                                                                                                    |
      +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Connection parameters

   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                        |
   +=================+=================+====================+====================================================================================================================================================================================================================================================+
   | name            | Yes             | String             | Connection name. The name contains a maximum of 100 characters, including only letters, numbers, hyphens (-), and underscores (_). The connection name must be unique.                                                                             |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String             | Connection type.                                                                                                                                                                                                                                   |
   |                 |                 |                    |                                                                                                                                                                                                                                                    |
   |                 |                 |                    | -  DWS                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  DLI                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  SparkSQL                                                                                                                                                                                                                                        |
   |                 |                 |                    | -  HIVE                                                                                                                                                                                                                                            |
   |                 |                 |                    | -  RDS                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  CloudTable                                                                                                                                                                                                                                      |
   |                 |                 |                    | -  HOST                                                                                                                                                                                                                                            |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config          | No              | Map<String,String> | Connection configuration item. The configuration item varies with the connection type. You do not need to set the **config** parameter for DLI connections. For other types of connections, see the description of connection configuration items. |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String             | Description of the connection. The description contains a maximum of 255 characters.                                                                                                                                                               |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example
-------

Query connection details.

-  Request

   .. code-block:: text

      GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections/connection1

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "name":"connection1",
          "type":"DWS",
          "config":{
              "clusterName":"test",
              "userName":"dbadmin",
                  "password":"*********",
              "kmsKey":"cdm-dlf",
              "agentName":"cdm-donotdelete",
              "sslEnable":false
          }
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6322",
          "error_msg":"The data connection does not exist."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
