:original_name: dataartsstudio_02_0067.html

.. _dataartsstudio_02_0067:

Rerunning a Job Instance
========================

Function
--------

This API is used to rerun a specific job instance. A job instance can be rerun only when it is in the successful, failed, or canceled state.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{job_name}/instances/{instance_id}/restart

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                           |
      +=============+===========+========+=======================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | job_name    | Yes       | String | Job name                                                                                                              |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | Long   | Job instance ID. For details about how to obtain it, see :ref:`Viewing a Job Instance List <dataartsstudio_02_0094>`. |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                            |
   +=================+=================+=================+========================================================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                                                          |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default.                              |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                                                     |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 |    .. note::                                                                                                           |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 |       -  You need to specify a workspace for multiple DataArts Studio instances.                                       |
   |                 |                 |                 |       -  This parameter is mandatory if no default workspace is available. If you do not set it, an error is reported. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameters

   +--------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type    | Description                                                                                                                                                                           |
   +====================+===========+=========+=======================================================================================================================================================================================+
   | retry_location     | No        | String  | Where the job rerun starts. The value can be **error_node** (error node), **first_node** (first node), or **specified_node** (a specified node). The default value is **first_node**. |
   +--------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_param_version  | No        | String  | Parameters to use. The value can be **original_version** (parameters of the original job) or **latest_version** (parameters of the latest job).                                       |
   +--------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ignore_obs_monitor | No        | boolean | Whether to ignore OBS listening                                                                                                                                                       |
   +--------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_name          | No        | String  | Name of the node from which the job rerun starts when **retry_location** is set to **specified_node**                                                                                 |
   +--------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None.

Example Request
---------------

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/job_batch/instances/34765/restart
   {
       "retry_location": "error_node",
       "job_param_version": "original_version",
       "ignore_obs_monitor": "true",
       "node_name": "test_node"
   }

Example Response
----------------

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0137",
          "error_msg":"Job instance does not exist."
      }
