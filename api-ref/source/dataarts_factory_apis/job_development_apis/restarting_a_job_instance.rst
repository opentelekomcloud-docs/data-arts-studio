:original_name: dataartsstudio_02_0067.html

.. _dataartsstudio_02_0067:

Restarting a Job Instance
=========================

Function
--------

This API is used to restart a specific job instance. A job instance can be restarted only when it is in the successful, failed, or canceled state.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{job_name}/instances/{instance_id}/restart

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                              |
      +=============+===========+========+==========================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | job_name    | Yes       | String | Job name.                                                                                                                |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | Long   | Job instance ID. For details about how to obtain it, see :ref:`Viewing a Job Instance List <dataartsstudio_02_0094>`.    |
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

Response
--------

None.

Example
-------

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/job_batch/instances/34765/restart

-  Response

   HTTP status code 204

   -  Failure response

      HTTP status code 400

      .. code-block::

         {
             "error_code":"DLF.0137",
             "error_msg":"Job instance does not exist."
         }
