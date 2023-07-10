:original_name: StopJob.html

.. _StopJob:

Stopping a Job
==============

Function
--------

This API is used to stop a job.

URI
---

PUT /v1.1/{project_id}/clusters/{cluster_id}/cdm/job/{job_name}/stop

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

   +-------------------+-------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type                                                                                | Description                                                                                                                                                                               |
   +===================+=====================================================================================+===========================================================================================================================================================================================+
   | validation-result | Array of :ref:`JobValidationResult <stopjob__response_jobvalidationresult>` objects | Validation result. If the job fails to be stopped, the failure cause is returned. For details, see the **validation-result** parameter. If the job is stopped, an empty list is returned. |
   +-------------------+-------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _stopjob__response_jobvalidationresult:

.. table:: **Table 4** JobValidationResult

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | message               | String                | Error message         |
   +-----------------------+-----------------------+-----------------------+
   | status                | String                | ERROR,WARNING         |
   |                       |                       |                       |
   |                       |                       | Enumeration values:   |
   |                       |                       |                       |
   |                       |                       | -  **ERROR**          |
   |                       |                       |                       |
   |                       |                       | -  **WARNING**        |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

.. code-block:: text

   PUT /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920/cdm/job/jdbc2hive/stop

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   { }

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
