:original_name: dataartsstudio_02_0092.html

.. _dataartsstudio_02_0092:

Starting a Job
==============

Function
--------

This API is used to start a job.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{name}/start

-  Parameter description

   .. table:: **Table 1** URI parameters

      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                              |
      +============+===========+========+==========================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | name       | Yes       | String | Job name.                                                                                                                |
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

.. table:: **Table 3** Parameter

   ========= ========= ============== ===============================
   Parameter Mandatory Type           Description
   ========= ========= ============== ===============================
   jobParams No        List<JobParam> Parameter for starting the job.
   ========= ========= ============== ===============================

.. table:: **Table 4** JobParam data structure description

   +-----------+-----------+--------+-----------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                               |
   +===========+===========+========+===========================================================+
   | name      | Yes       | String | Name of the parameter. It cannot exceed 64 characters.    |
   +-----------+-----------+--------+-----------------------------------------------------------+
   | value     | Yes       | String | Value of the parameter. It cannot exceed 1024 characters. |
   +-----------+-----------+--------+-----------------------------------------------------------+

Response
--------

None.

Example
-------

Start job **myJob**.

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/myJob/start

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
