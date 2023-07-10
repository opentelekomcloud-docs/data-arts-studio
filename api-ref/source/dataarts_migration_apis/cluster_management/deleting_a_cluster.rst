:original_name: DeleteCluster.html

.. _DeleteCluster:

Deleting a Cluster
==================

Function
--------

This API is used to delete a cluster.

URI
---

DELETE /v1.1/{project_id}/clusters/{cluster_id}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   cluster_id Yes       String Cluster ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                              |
   +==============+===========+========+==========================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------------+-----------------+-----------------+-------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                 |
   +=========================+=================+=================+=============================================================+
   | keep_last_manual_backup | Yes             | Integer         | Number of backup log files. Retain the default value **0**. |
   |                         |                 |                 |                                                             |
   |                         |                 |                 | Default: **0**                                              |
   +-------------------------+-----------------+-----------------+-------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   jobId     String Job ID
   ========= ====== ===========

Example Requests
----------------

.. code-block:: text

   DELETE /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920

   {
     "keep_last_manual_backup" : 0
   }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "jobId" : "ff8080815e55125a015e552eddba001a"
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------+
| Status Code | Description                                                       |
+=============+===================================================================+
| 202         | Accepted                                                          |
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
| 503         | Service unavailable.                                              |
+-------------+-------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
