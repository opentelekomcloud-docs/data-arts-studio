:original_name: dataartsstudio_02_0055.html

.. _dataartsstudio_02_0055:

Exporting a Connection
======================

Function
--------

This API is used to export all connection information that is compressed in ZIP format.

URI
---

-  URI format

   POST /v1/{project_id}/connections/export

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                              |
      +============+===========+========+==========================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

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

The value of **Content-Type** in the response message is **application/octet-stream** that needs to be converted into a file. For details, see :ref:`Parsing a Stream in a Response Message <dataartsstudio_02_0317>`. Response messages are compressed as a file. The file name format is **DLF_All_DataConnections.zip**. The file directory is as follows:

.. code-block::

   connections
   ├─{dwsConnection}.conn

Example
-------

Export a connection.

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections/export

-  Success response

   HTTP status code 200

   .. code-block::

      Response messages are compressed as a file. The file directory is as follows:
      connections
      ├─{dwsConnection}.conn

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
