:original_name: AuthorizeApiToInstance.html

.. _AuthorizeApiToInstance:

Batch Authorization API (Exclusive Edition)
===========================================

Function
--------

An app cannot access any APIs after being created. To enable an app to access an API, authorize the API to the app. After the authorization is successful, the app can access the API within the validity period.

API authorization includes authorization and renewal.

-  Authorization: Apps are granted the right to access APIs within the validity period.

-  Renewal: The validity period of the authorization is updated during renewal. The validity period can be extended but cannot be reduced.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apis/{api_id}/instances/{instance_id}/authorize

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                             |
   +=============+===========+========+=========================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | api_id      | Yes       | String | API ID                                                                                                                  |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Cluster ID                                                                                                              |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Request body parameters

   ========= ========= ================ ===========
   Parameter Mandatory Type             Description
   ========= ========= ================ ===========
   time      No        String           End time.
   app_ids   No        Array of strings App IDs
   ========= ========= ================ ===========

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Authorize or renew the API whose ID is 760715eb1bfce0c575abab3be3bd41e6 in the cluster whose ID is 51159105c7838353d2834181d978af50.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/760715eb1bfce0c575abab3be3bd41e6/instances/51159105c7838353d2834181d978af50/authorize

   {
     "app_ids" : [ "efa895e32e758bd316726b196ca1e8de" ],
     "time" : "2022-03-25T10:00:00.000Z"
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ================================
Status Code Description
=========== ================================
204         The API operation is successful.
400         Bad request
=========== ================================
