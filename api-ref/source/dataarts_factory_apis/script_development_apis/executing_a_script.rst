:original_name: dataartsstudio_02_0058.html

.. _dataartsstudio_02_0058:

Executing a Script
==================

Function
--------

This API is used to execute a specific script, which can be a DWS SQL, DLI SQL, RDS SQL, Flink SQL, Hive SQL, Presto SQL, or Spark SQL script. A script instance is generated each time the script is executed. You can call the API :ref:`Querying the Execution Result of a Script Instance <dataartsstudio_02_0101>` to obtain script execution results.

URI
---

-  URI format

   POST /v1/{project_id}/scripts/{script_name}/execute

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                              |
      +=============+===========+========+==========================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | script_name | Yes       | String | Script name.                                                                                                             |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                        |
   +===========+===========+========+====================================================================================================================================================================================+
   | params    | No        | Object | Script parameters of the Map<String,String> type. If a parameter is defined in the script, the parameter value is carried in the params. By default, this parameter is left blank. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Script parameters refer to the parameters in the script content, as shown in the following figure.

|image1|

Response
--------

.. table:: **Table 4** Response parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                      |
   +============+===========+========+==================================================================================================================================================================================================+
   | instanceId | Yes       | String | ID of the instance that executes the script. You can obtain the execution result by using the instance ID in :ref:`Querying the Execution Result of a Script Instance <dataartsstudio_02_0101>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example
-------

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts/dws_sql/execute

   .. code-block::

      {
      "params":{"tableVar":"citys",
      "time":"2019-07-25"}
      }

-  Success response

   HTTP status code 200

   .. code-block::

      {
      "instanceId": "a1ad-448a-9d56-4154193d49c5"
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

.. |image1| image:: /_static/images/en-us_image_0000001373408961.png
