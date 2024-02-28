:original_name: DeleteJob_0.html

.. _DeleteJob_0:

Deleting a Job
==============

Function
--------

This API is used to delete a job.

URI
---

DELETE /v1.1/{project_id}/clusters/{cluster_id}/cdm/job/{job_name}

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

**Status code: 500**

.. table:: **Table 3** Response body parameters

   =============== ====== =============
   Parameter       Type   Description
   =============== ====== =============
   errCode         String Error code
   externalMessage String Error message
   =============== ====== =============

Example Requests
----------------

.. code-block:: text

   DELETE /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920/cdm/job/jdbc2hive

Example Responses
-----------------

**Status code: 500**

An internal service error occurred. For details, see error codes.

.. code-block::

   {
     "errCode" : "Cdm.0100",
     "externalMessage" : "Job[jdbc2hive] doesn't exist."
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------+
| Status Code | Description                                                       |
+=============+===================================================================+
| 200         | OK                                                                |
+-------------+-------------------------------------------------------------------+
| 400         | Request error.                                                    |
+-------------+-------------------------------------------------------------------+
| 401         | Authentication failed.                                            |
+-------------+-------------------------------------------------------------------+
| 403         | You do not have required permissions to perform this operation.   |
+-------------+-------------------------------------------------------------------+
| 404         | The requested resource was not found.                             |
+-------------+-------------------------------------------------------------------+
| 500         | An internal service error occurred. For details, see error codes. |
+-------------+-------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
