:original_name: StopCluster.html

.. _StopCluster:

Stopping a Cluster
==================

Function
--------

This API is used to stop a cluster.

URI
---

POST /v1.1/{project_id}/clusters/{cluster_id}/action

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

   +-----------+-----------+------------------------------------------------+----------------------------------------------------------+
   | Parameter | Mandatory | Type                                           | Description                                              |
   +===========+===========+================================================+==========================================================+
   | stop      | Yes       | :ref:`stop <stopcluster__request_stop>` object | Startup of a cluster. This parameter is an empty object. |
   +-----------+-----------+------------------------------------------------+----------------------------------------------------------+

.. _stopcluster__request_stop:

.. table:: **Table 4** stop

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================================================================================================================================================================================================+
   | stopMode        | No              | String          | Stop mode                                                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **IMMEDIATELY**: immediate stop                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **GRACEFULLY**: graceful stop                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **IMMEDIATELY**                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **GRACEFULLY**                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | delayTime       | No              | Integer         | Stop delay, in seconds. This parameter is valid only when **stopMode** is set to **GRACEFULLY**. If the value of this parameter is set to **-1**, the system waits for all jobs to complete and stops accepting new jobs. If the value of this parameter is greater than **0**, the system stops the cluster after the specified time and stops accepting new jobs. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========= ================ ===========
   Parameter Type             Description
   ========= ================ ===========
   jobId     Array of strings Job ID
   ========= ================ ===========

Example Requests
----------------

Stopping a Cluster

.. code-block:: text

   POST /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/action

   {
     "stop" : {
       "stopMode" : "GRACEFULLY",
       "delayTime" : -1
     }
   }

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "jobId" : [ "ff8080815e59d92d015e5b27ccb0004d" ]
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------+
| Status Code | Description                                                       |
+=============+===================================================================+
| 200         | ok                                                                |
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
