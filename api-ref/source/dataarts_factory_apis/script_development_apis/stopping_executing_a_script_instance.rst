:original_name: dataartsstudio_02_0059.html

.. _dataartsstudio_02_0059:

Stopping Executing a Script Instance
====================================

Function
--------

This API is used to stop executing a script instance.

URI
---

-  URI format

   POST /v1/{project_id}/scripts/{script_name}/instances/{instance_id}/stop

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

None.

Example Request
---------------

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts/dwsscript/instances/a1ad-448a-9d56-4154193d49c5/stop

Example Response
----------------

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6205",
          "error_msg":"The script running history does not exist."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
