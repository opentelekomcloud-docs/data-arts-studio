:original_name: ListApicInstances.html

.. _ListApicInstances:

Obtaining a Gateway Instance (Exclusive Edition)
================================================

Function
--------

This API is used to obtain a gateway instance (exclusive edition).

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/apigw/instances

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================+
   | apig_type       | Yes             | String          | Gateway type                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | Enumerated values include:                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **APIGW**: APIGW gateway                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                       |
   |                 |                 |                 | -  **ROMA_APIC**: ROMA gateway                                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records that can be queried                                                                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Query offset, that is, X data records are skipped. The value must be **0** or an integer multiple of **limit**. If the value does not meet the requirements, it will be rounded down. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                    |
   +==============+===========+========+================================================================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service.                                             |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                                              |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dlm-Type     | No        | String | Specifies the version type of the data service. The value can be SHARED or EXCLUSIVE.                                                                                                                                                                                                                          |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Type (format) of the message body. This parameter is mandatory if the message body exists. If the message body does not exist, leave this parameter blank. If the request body contains Chinese characters, use charset=utf8 to specify the Chinese character set, for example, application/json;charset=utf8. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------------+---------------------------------------------------------------------------------------+-------------------+
   | Parameter         | Type                                                                                  | Description       |
   +===================+=======================================================================================+===================+
   | gateway_instances | Array of :ref:`ApigInstanceDTO <listapicinstances__response_apiginstancedto>` objects | Gateway instance. |
   +-------------------+---------------------------------------------------------------------------------------+-------------------+

.. _listapicinstances__response_apiginstancedto:

.. table:: **Table 5** ApigInstanceDTO

   ============= ====== ===========================
   Parameter     Type   Description
   ============= ====== ===========================
   instance_id   String Gateway instance ID.
   instance_name String Name of a gateway instance.
   ============= ====== ===========================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain a gateway instance in DataArts DataService Exclusive.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apigw/instances

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "gateway_instances" : [ {
       "instance_id" : "0ca3311f5dc941b7b3d1950d1682b646",
       "instance_name" : "apigw_test_001"
     } ]
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         Success
400         Bad Request:
=========== ============
