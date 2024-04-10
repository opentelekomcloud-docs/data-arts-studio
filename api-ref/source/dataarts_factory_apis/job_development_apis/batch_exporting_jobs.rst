:original_name: dataartsstudio_02_0089.html

.. _dataartsstudio_02_0089:

Batch Exporting Jobs
====================

Function
--------

This API is used to batch export jobs, including job dependency scripts and CDM job definitions.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/batch-export

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                     |
   +=================+=================+=================+=================================================================================+
   | jobList         | Yes             | List            | A list of jobs to be exported. A maximum of 100 jobs can be exported at a time. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | exportDepend    | No              | boolean         | Specifies whether to export the scripts and resources that the job depends on.  |
   |                 |                 |                 |                                                                                 |
   |                 |                 |                 | Default value: **true**                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+

Response Parameters
-------------------

The response message of batch exporting jobs is the same as that of exporting jobs. For details, see :ref:`Response Parameters <dataartsstudio_02_0088__en-us_topic_0181281356_section561243517589>`.

Example Request
---------------

Export two jobs named **job_batch** and **job_stream**, respectively. Scripts and resources on which the job depends are exported by default.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/batch-export
   {
      "jobList":["job_batch","job_stream"],
      "exportDepend":true
   }

Example Response
----------------

-  Success response

   The value of **Content-Type** in the response message is **application/octet-stream** that needs to be converted into a file. For details, see :ref:`Parsing a Stream in a Response Message <dataartsstudio_02_0317>`. The response is a compressed file named **jobs.zip**. The file structure after decompression is as follows:

   .. code-block::

      jobs
      +---job_batch
      |       dws_sql.script
      |       job_batch.job
      \---job_stream
      job_stream.job

   **job_batch.job** and **job_stream.job** are job definition files.

   **dws_sql.script** is the DWS SQL script file used by **job_batch.job**.

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.3051",
          "error_msg":"The request parameter is invalid."
      }
