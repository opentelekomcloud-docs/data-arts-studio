:original_name: dataartsstudio_02_0053.html

.. _dataartsstudio_02_0053:

Editing a Connection (to Be Taken Offline)
==========================================

.. note::

   The connection management capability is provided by Management Center. APIs of Management Center are recommended.

Function
--------

This API is used to edit a connection.

URI
---

-  URI format

   PUT /v1/{project_id}/connections/{connection_name}?ischeck=true

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory | Type   | Description                                                                                                           |
      +=================+===========+========+=======================================================================================================================+
      | project_id      | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | connection_name | Yes       | String | Name of a connection.                                                                                                 |
      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | ischeck         | No        | String | Indicates whether to perform check. The default value is **No**.                                                      |
      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

Response Parameters
-------------------

None.

Example Request
---------------

Modify a connection.

.. code-block:: text

   PUT /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections/connection1?ischeck=true
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

Example Response
----------------

-  Success response

   HTTP status code 204

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
