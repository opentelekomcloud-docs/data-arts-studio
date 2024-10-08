:original_name: dataartsstudio_02_0051.html

.. _dataartsstudio_02_0051:

Querying a Connection List (to Be Taken Offline)
================================================

.. note::

   The connection management capability is provided by Management Center. APIs of Management Center are recommended.

Function
--------

This API is used to query a connection list.

URI
---

-  URI format

   GET /v1/{project_id}/connections?offset={offset}&limit={limit}&connectionName={connectionName}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                           |
      +=================+=================+=================+=======================================================================================================================+
      | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | The value is no less than **0**. The default value is **0**.                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | The maximum number of records on each page. Value range: 1 to 100                                                     |
      |                 |                 |                 |                                                                                                                       |
      |                 |                 |                 | Default value: **10**                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | connectionName  | No              | String          | Name of a connection.                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

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

Response Parameters
-------------------

+-------------+-----------+-----------------------------------------------------------------------------------------------+----------------------------------+
| Parameter   | Mandatory | Type                                                                                          | Description                      |
+=============+===========+===============================================================================================+==================================+
| total       | Yes       | Integer                                                                                       | The total number of connections. |
+-------------+-----------+-----------------------------------------------------------------------------------------------+----------------------------------+
| connections | Yes       | List<:ref:`Connections <dataartsstudio_02_0051__en-us_topic_0181616873_table15534111511492>`> | Connection list.                 |
+-------------+-----------+-----------------------------------------------------------------------------------------------+----------------------------------+

.. _dataartsstudio_02_0051__en-us_topic_0181616873_table15534111511492:

.. table:: **Table 3** connections parameters

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

Example Request
---------------

Query connections.

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections

Example Response
----------------

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "total":1,
          "connections":[
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
          ]
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.3051",
          "error_msg":"The request parameter is invalid."
      }
