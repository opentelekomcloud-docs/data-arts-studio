:original_name: dataartsstudio_02_0088.html

.. _dataartsstudio_02_0088:

Exporting a Job
===============

Function
--------

This API is used to export a job, including job definitions, job dependency scripts, and CDM job definitions.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{name}/export

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                    |
   +=================+=================+=================+================================================================================+
   | exportDepend    | No              | boolean         | Specifies whether to export the scripts and resources that the job depends on. |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Default value: true                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+

.. _dataartsstudio_02_0088__en-us_topic_0181281356_section561243517589:

Response
--------

The value of **Content-Type** in the response message is **application/octet-stream** that needs to be converted into a file. For details, see :ref:`Parsing a Stream in a Response Message <dataartsstudio_02_0317>`. Response messages are compressed as a file. The file name format is **DLF\_**\ *job_name*\ **.zip**. The file directory is as follows:

.. code-block::

   jobs
   ├─{job_name}.job
   scripts
   ├─{script_name}.script
   resources
   ├─{resource_name}.resource

:ref:`Table 4 <dataartsstudio_02_0088__en-us_topic_0181281356_table115125816213>` describes the file directory parameters.

.. _dataartsstudio_02_0088__en-us_topic_0181281356_table115125816213:

.. table:: **Table 4** Response parameters

   +---------------+-----------+--------+-----------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                   |
   +===============+===========+========+===============================================+
   | job_name      | Yes       | String | Job name.                                     |
   +---------------+-----------+--------+-----------------------------------------------+
   | script_name   | No        | String | Name of the script that the job depends on.   |
   +---------------+-----------+--------+-----------------------------------------------+
   | resource_name | No        | String | Name of the resource that the job depends on. |
   +---------------+-----------+--------+-----------------------------------------------+

-  {job_name}.job

   The parameters in the file are the same as the request parameters of the API for creating a job. For details, see :ref:`Creating a Job <dataartsstudio_02_0084>`.

-  {script_name}.script

   The parameters in the file are the same as the request parameters of the API for creating a resource. For details, see :ref:`Creating a Script <dataartsstudio_02_0097>`.

Example
-------

Export job **myJob**.

-  Request

   .. code-block:: text

      POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/myJob/export
      {
         "exportDepend":true
      }

-  Success response

   HTTP status code 200

   The name of the exported file is **DLF_myJob.zip**. The file structure after decompression is as follows:

   .. code-block::

      jobs
      ├─myJob.job
      scripts
      ├─CS_PROCESS_TRIP.script
      ├─TRIP_RAW_STANDARD.script

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
