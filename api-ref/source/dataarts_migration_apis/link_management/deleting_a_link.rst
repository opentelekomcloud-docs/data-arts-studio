:original_name: DeleteLink.html

.. _DeleteLink:

Deleting a Link
===============

Function
--------

This API is used to delete a link.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

DELETE /v1.1/{project_id}/clusters/{cluster_id}/cdm/link/{link_name}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | cluster_id | Yes       | String | Cluster ID                                                                                                  |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | link_name  | Yes       | String | Name of the link to be deleted                                                                              |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                  |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

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

   DELETE /v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920/cdm/link/jdbclink

Example Responses
-----------------

**Status code: 500**

Internal service error. For details about the returned error code, see Error Codes.

.. code-block::

   {
     "errCode" : "Cdm.0021",
     "externalMessage" : "Given link name is in use"
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------+
| Status Code | Description                                                                         |
+=============+=====================================================================================+
| 200         | Request succeeded.                                                                  |
+-------------+-------------------------------------------------------------------------------------+
| 400         | Request error.                                                                      |
+-------------+-------------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                              |
+-------------+-------------------------------------------------------------------------------------+
| 403         | No operation permissions.                                                           |
+-------------+-------------------------------------------------------------------------------------+
| 404         | No resources found.                                                                 |
+-------------+-------------------------------------------------------------------------------------+
| 500         | Internal service error. For details about the returned error code, see Error Codes. |
+-------------+-------------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                                |
+-------------+-------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
