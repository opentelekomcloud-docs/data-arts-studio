:original_name: ShowInstanceLog.html

.. _ShowInstanceLog:

Obtaining Logs of a Metadata Collection Task
============================================

Function
--------

Obtain task logs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/metadata/tasks/{task_id}/{instance_id}/log

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                 |
   +=============+===========+========+=============================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | task_id     | Yes       | String | Job ID                                                                                                      |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Task instance ID                                                                                            |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ================= ========= ====== =====================
   Parameter         Mandatory Type   Description
   ================= ========= ====== =====================
   bridge_id         Yes       String Bridge job ID
   classification_id No        String Classification job ID
   ================= ========= ====== =====================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------------+---------+----------------------------------------------------------+
   | Parameter              | Type    | Description                                              |
   +========================+=========+==========================================================+
   | enable_bridge          | Boolean | Indicates whether to enable the bridge mode.             |
   +------------------------+---------+----------------------------------------------------------+
   | enable_profile         | Boolean | Indicates whether to enable the configuration.           |
   +------------------------+---------+----------------------------------------------------------+
   | enable_classification  | Boolean | Indicates whether to enable the classification function. |
   +------------------------+---------+----------------------------------------------------------+
   | bridge_status          | String  | Indicates the bridge status.                             |
   +------------------------+---------+----------------------------------------------------------+
   | profile_status         | String  | Configuration status.                                    |
   +------------------------+---------+----------------------------------------------------------+
   | classification_status  | String  | Classification status.                                   |
   +------------------------+---------+----------------------------------------------------------+
   | bridge_job_log         | String  | Bridge job log.                                          |
   +------------------------+---------+----------------------------------------------------------+
   | profile_job_log        | String  | Profile job logs                                         |
   +------------------------+---------+----------------------------------------------------------+
   | classification_job_log | String  | Classification job log                                   |
   +------------------------+---------+----------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

.. code-block::

   {
     "bridge_id" : "D0D87362B46C4DBB8D9F7E3511E69E45",
     "classification_id" : null
   }

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "enable_bridge" : true,
     "enable_profile" : false,
     "enable_classification" : false,
     "bridge_status" : "success",
     "profile_status" : null,
     "classification_status" : null,
     "bridge_job_log" : "Start DLI Bridge Job.",
     "profile_job_log" : null,
     "classification_job_log" : null
   }

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         OK.
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
=========== =============
