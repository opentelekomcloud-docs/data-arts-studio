:original_name: StartJob.html

.. _StartJob:

Starting a Job
==============

Function
--------

This API is used to start a job.

URI
---

PUT /v1.1/{project_id}/clusters/{cluster_id}/cdm/job/{job_name}/start

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   cluster_id Yes       String Cluster ID
   job_name   Yes       String Job name
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                              |
   +==============+===========+========+==========================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                               | Description                                                                              |
   +=============+====================================================================================+==========================================================================================+
   | submissions | Array of :ref:`StartJobSubmission <startjob__response_startjobsubmission>` objects | Job running information. For details, see the descriptions of **submission** parameters. |
   +-------------+------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+

.. _startjob__response_startjobsubmission:

.. table:: **Table 4** StartJobSubmission

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                   |
   +=======================+=======================+===============================================================================================+
   | isIncrementing        | Boolean               | Whether the job migrates incremental data                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | delete_rows           | Integer               | Number of deleted rows                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | update_rows           | Integer               | Number of updated rows                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | write_rows            | Integer               | Number of written rows                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | submission-id         | Integer               | ID of the submitted job                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | job-name              | String                | Job name                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | creation-user         | String                | User who created the job                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | creation-date         | Long                  | Job creation time, accurate to millisecond                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | execute-date          | Long                  | Job execution time                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | progress              | Float                 | Job progress. If a job fails, the value is **-1**. Otherwise, the value ranges from 0 to 100. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | status                | String                | Job status                                                                                    |
   |                       |                       |                                                                                               |
   |                       |                       | -  **BOOTING**: The job is starting.                                                          |
   |                       |                       |                                                                                               |
   |                       |                       | -  **FAILURE_ON_SUBMIT**: The job failed to be submitted.                                     |
   |                       |                       |                                                                                               |
   |                       |                       | -  **RUNNING**: The job is running.                                                           |
   |                       |                       |                                                                                               |
   |                       |                       | -  **SUCCEEDED**: The job was successfully executed.                                          |
   |                       |                       |                                                                                               |
   |                       |                       | -  **FAILED**: The job execution failed.                                                      |
   |                       |                       |                                                                                               |
   |                       |                       | -  **UNKNOWN**: The job status is unknown.                                                    |
   |                       |                       |                                                                                               |
   |                       |                       | -  **NEVER_EXECUTED**: The job was not executed.                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | isStopingIncrement    | String                | Whether to stop incremental data migration                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | is-execute-auto       | Boolean               | Whether to execute the job as scheduled                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | last-update-date      | Long                  | Time when the job was last updated                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | last-udpate-user      | String                | User who last updated the job status                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | isDeleteJob           | Boolean               | Whether to delete the job after it is executed                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   PUT /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920/cdm/job/jdbc2hive/start

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "submissions" : [ {
       "job-name" : "jdbc2hive",
       "creation-user" : "cdm",
       "creation-date" : "1536905778725",
       "progress" : 1,
       "status" : "BOOTING"
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
