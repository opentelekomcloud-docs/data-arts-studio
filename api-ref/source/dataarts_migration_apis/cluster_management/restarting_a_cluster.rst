:original_name: RestartCluster_0.html

.. _RestartCluster_0:

Restarting a Cluster
====================

Function
--------

This API is used to restart a cluster.

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

   +-----------+-----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                      | Description                                                                                                              |
   +===========+===========+===========================================================+==========================================================================================================================+
   | restart   | Yes       | :ref:`restart <restartcluster_0__request_restart>` object | Cluster restart. For details about how to define the cluster to restart, see the descriptions of **restart** parameters. |
   +-----------+-----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _restartcluster_0__request_restart:

.. table:: **Table 4** restart

   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                          |
   +==================+=================+=================+======================================================================================================================================================+
   | restartDelayTime | No              | Integer         | Restart delay, in seconds                                                                                                                            |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restartMode      | No              | String          | Restart mode                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | -  **IMMEDIATELY**: immediate restart                                                                                                                |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | -  **FORCELY**: forcible restart                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | -  **SOFTLY**: common restart                                                                                                                        |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | The default value is **IMMEDIATELY**. Forcibly restarting the service process will interrupt the service process and restart the VMs in the cluster. |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restartLevel     | No              | String          | Restart level                                                                                                                                        |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | -  **SERVICE**: service restart                                                                                                                      |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | -  **VM**: VM restart                                                                                                                                |
   |                  |                 |                 |                                                                                                                                                      |
   |                  |                 |                 | The default value is **SERVICE**.                                                                                                                    |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type             | No              | String          | Type of the cluster to be restarted. The value can be set to **cdm** only.                                                                           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance         | No              | String          | Reserved field. When **restartLevel** is set to **SERVICE**, this parameter is mandatory and an empty string should be entered.                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group            | No              | String          | Reserved field. When **restartLevel** is set to **SERVICE**, this parameter is mandatory and an empty string should be entered.                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   jobId     String Job ID
   ========= ====== ===========

Example Requests
----------------

Restarting a Cluster

.. code-block:: text

   POST /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/action

   {
     "restart" : {
       "instance" : "",
       "type" : "cdm",
       "group" : ""
     }
   }

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "jobId" : "ff8080815e59d92d015e5b27ccb0004d"
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
