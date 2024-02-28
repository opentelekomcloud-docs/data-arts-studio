:original_name: dataartsstudio_02_0101.html

.. _dataartsstudio_02_0101:

Querying the Execution Result of a Script Instance
==================================================

Function
--------

This API is used to obtain the execution status and result of a script instance.

During the query, specify the script name and script instance ID.

URI
---

-  URI format

   GET /v1/{project_id}/scripts/{script_name}/instances/{instance_id}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                                                    |
      +=============+===========+========+================================================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                          |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | script_name | Yes       | String | Script name.                                                                                                                                   |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | String | Script instance ID. For details about how to obtain the ID, see the response parameters in :ref:`Executing a Script <dataartsstudio_02_0058>`. |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                            |
   +=================+=================+=================+========================================================+
   | status          | Yes             | String          | Execution status.                                      |
   |                 |                 |                 |                                                        |
   |                 |                 |                 | **LAUNCHING:** The script instance is being submitted. |
   |                 |                 |                 |                                                        |
   |                 |                 |                 | **RUNNING:** The script instance is running.           |
   |                 |                 |                 |                                                        |
   |                 |                 |                 | **FINISHED**: The script instance is successfully run. |
   |                 |                 |                 |                                                        |
   |                 |                 |                 | **FAILED**: The script instance fails to be run.       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------+
   | results         | Yes             | List<Result>    | Execution result of the script instance.               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------+

.. table:: **Table 4** Result data structure description

   +-----------+-----------+---------------------------+---------------------------------------------------------+
   | Parameter | Mandatory | Type                      | Description                                             |
   +===========+===========+===========================+=========================================================+
   | message   | No        | String                    | Execution failure message.                              |
   +-----------+-----------+---------------------------+---------------------------------------------------------+
   | duration  | No        | float                     | Duration of executing the script instance. Unit: second |
   +-----------+-----------+---------------------------+---------------------------------------------------------+
   | rowCount  | No        | Int                       | Number of the result rows.                              |
   +-----------+-----------+---------------------------+---------------------------------------------------------+
   | rows      | No        | List<List<Object>>        | Result data.                                            |
   +-----------+-----------+---------------------------+---------------------------------------------------------+
   | schema    | No        | List<Map<String, String>> | Format definition of the result data.                   |
   +-----------+-----------+---------------------------+---------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts/dwsscript/instances/a1ad-448a-9d56-4154193d49c5

Example Response
----------------

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "results": [{
              "message": "",
                      "duration":0.5,
              "rowCount": 1,
              "rows": [[913460.0,
              765.0,
              "8/31/2015 23:26",
              "Harry Bridges Plaza (Ferry Building)",
              50.0,
              "8/31/2015 23:39",
              "San Francisco Caltrain (Townsend at 4th)",
              70.0,
              "288",
              "Subscriber",
              "2139"]],
              "schema": [{
                  "TripID": "int"
              },
              {
                  "Duration": "int"
              },
              {
                  "StartDate": "string"
              },
              {
                  "StartStation": "string"
              },
              {
                  "StartTerminal": "int"
              },
              {
                  "EndDate": "string"
              },
              {
                  "EndStation": "string"
              },
              {
                  "EndTerminal": "int"
              },
              {
                  "Bike": "string"
              },
              {
                  "SubscriberType": "string"
              },
              {
                  "ZipCode": "string"
              }]
          }],
          "status": "FINISHED"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6201",
          "error_msg":"The script does not exist."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
