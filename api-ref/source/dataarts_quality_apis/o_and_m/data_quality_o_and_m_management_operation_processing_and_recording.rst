:original_name: UpdateQualityInstanceRecord.html

.. _UpdateQualityInstanceRecord:

Data quality O&M management operation processing and recording
==============================================================

Function
--------

This API is used to handle problems of data quality monitoring instances. On the console, you can choose More > Handling & Record to go to the problem handling page.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v2/{project_id}/quality/instances/{instance_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                     |
   +=============+===========+========+=================================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.         |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID. For details about how to obtain the instance ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                       |
   +==============+===========+========+===================================================================================================================================================+
   | workspace    | Yes       | String | DataArts Studio workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | IAM token. For details about how to obtain the token, see :ref:`Authentication <dataartsstudio_02_0010>`.                                         |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type    | Description                                                                                                                                                                     |
   +============+===========+=========+=================================================================================================================================================================================+
   | detail     | No        | String  | This field is used only when you enter handling comments or close an issue. Enter related comments or closure description.                                                      |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | operator   | No        | String  | This field is used only when the problem is handed over to others. Select the handover owner.                                                                                   |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | open       | No        | Boolean | Issue handling method. **false** indicates closing the issue. **true** indicates the issue handling suggestion or handling the issue to others.                                 |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cancel_run | No        | Boolean | Whether to cancel the task. If the task is canceled, it will be stopped immediately. Value **false** means to cancel the task, and value **true** means not to cancel the task. |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ====================
   Parameter Type   Description
   ========= ====== ====================
   data      String Returned information
   ========= ====== ====================

**Status code: 500**

.. table:: **Table 5** Response body parameters

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | error_code | String | Error code, for example, **DQC.0000** which indicates that the request was successfully processed |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                                     |
   +------------+--------+---------------------------------------------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

None

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Success
500         INTERNAL SERVER ERROR
=========== =====================
