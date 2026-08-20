:original_name: AuthorizeActionApiToInstance.html

.. _AuthorizeActionApiToInstance:

API authorization operations (authorization/authorization cancellation/application/renewal)
===========================================================================================

Function
--------

-  Proactive API authorization: An API reviewer can initiate an API authorization request. After the API authorization is successful, the app can access the API within the validity period. API authorization includes authorization and renewal.

-  Authorization: Apps are granted the right to access APIs within the validity period.

-  Renewal: The validity period of the authorization is updated during renewal. The validity period can be extended but cannot be reduced.

-  API authorization cancellation: An API reviewer can cancel the authorization relationship between an API and an app. After the API authorization is canceled, the app can no longer call the API. Before performing this operation, reserve at least two days for the app to make preparations.

-  App authorization cancellation: The app owner can initiate a request to cancel the authorization relationship between an API and an app. After the API authorization is canceled, the app can no longer call the API. This operation requires no preparation time.

-  App authorization application: An app owner can initiate an application for an API. After the application is approved by the API reviewer, the app can access the API. The authorization grants the app the right to access the API within the validity period. The API review is required.

-  App renewal: The app owner can initiate a renewal request. The renewal will update the authorization validity period. The validity period can be extended but cannot be reduced. The renewal needs to be reviewed by the API.

.. note::

   -  It is recommended that you apply for your own API authorization or renewal without approval.

   -  It is recommended that the app be used to cancel the authorization. No preparation time needs to be reserved.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apis/authorize/action

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | api_id          | No              | String          | API ID                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | instance_id     | No              | String          | Cluster ID                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | app_id          | No              | String          | App ID                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | apply_type      | No              | String          | Application type                                                    |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | Enumerated values:                                                  |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **APPLY_TYPE_AUTHORIZE**: authorizing an API to an app           |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **APPLY_TYPE_API_CANCEL_AUTHORIZE**: canceling API authorization |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **APPLY_TYPE_APP_CANCEL_AUTHORIZE**: canceling app authorization |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **APPLY_TYPE_APPLY**: reviewing an API                           |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **APPLY_TYPE_RENEW**: renewing an API                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | time            | No              | String          | End time.                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

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

Authorize an API to an app./Cancel API authorization (by the API reviewer)./Cancel API authorization (by the app owner)./Apply for authorization./Renew the validity period.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apis/authorize/action

   {
     "api_id" : "47046fe7830c1be77cb0dc23bd86afa5",
     "instance_id" : "21398ikjdsjd9087122d4e",
     "app_id" : "908489209a320df61607355c57c82882",
     "apply_type" : "APPLY_TYPE_AUTHORIZE",
     "time" : "2021-01-01T10:00:00.000Z"
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
