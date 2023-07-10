:original_name: dataartsstudio_02_0064.html

.. _dataartsstudio_02_0064:

Stopping a Job
==============

Function
--------

This API is used to stop a job.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{job_name}/stop

-  Parameter description

   .. table:: **Table 1** URI parameters

      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                              |
      +============+===========+========+==========================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | job_name   | Yes       | String | Job name.                                                                                                                |
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

None.

Example
-------

Stops job **myJob**.

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/myJob/stop

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
