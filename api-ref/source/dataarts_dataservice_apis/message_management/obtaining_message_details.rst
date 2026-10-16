:original_name: ShowMessageDetail.html

.. _ShowMessageDetail:

Obtaining Message Details
=========================

Function
--------

This API is used to obtain message details. This function is only used for displaying application details and not for processing. Therefore, background parameters such as the ID are not displayed.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/service/messages/{message_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | message_id | Yes       | String | Message ID                                                                                                              |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | id                    | String                | Application ID.                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | api_apply_status      | String                | Application status                                                  |
   |                       |                       |                                                                     |
   |                       |                       | Enumerated values:                                                  |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_PENDING_APPROVAL**: pending review                 |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_REJECTED**: rejected                               |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_PENDING_CHECK**: pending check                     |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_PENDING_EXECUTE**: pending execution               |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_SYNCHRONOUS_EXECUTE**: synchronouly executed       |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_FORCED_CANCEL**: canceled forcibly                 |
   |                       |                       |                                                                     |
   |                       |                       | -  **STATUS_TYPE_PASSED**: passed                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | api_apply_type        | String                | Application type                                                    |
   |                       |                       |                                                                     |
   |                       |                       | Enumerated values:                                                  |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_PUBLISH**: publishing an API                        |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_AUTHORIZE**: authorizing an API to an app           |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_APPLY**: reviewing an API                           |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_RENEW**: renewing an API                            |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_STOP**: stopping an API                             |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_RECOVER**: recovering an API                        |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_API_CANCEL_AUTHORIZE**: canceling API authorization |
   |                       |                       |                                                                     |
   |                       |                       | -  **APPLY_TYPE_APP_CANCEL_AUTHORIZE**: canceling app authorization |
   |                       |                       |                                                                     |
   |                       |                       | -  \**APPLY_TYPE_OFFLINE: suspending an API                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | api_id                | String                | API ID                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | api_name              | String                | API name                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | api_using_time        | Long                  | Expiry time of using the API,                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | app_id                | String                | App ID                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | app_name              | String                | App name                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | apply_time            | Long                  | Application time,                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | approval_time         | Long                  | Authorization time,                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | approver_name         | String                | Reviewer name.                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | comment               | String                | Review comments.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | user_name             | String                | Applicant name.                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

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

Obtain the review notification of the application whose ID is 51159105c7838353d2834181d978af50.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/messages/51159105c7838353d2834181d978af50

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "id" : null,
     "api_apply_status" : "STATUS_TYPE_PASSED",
     "api_apply_type" : "APPLY_TYPE_APPLY",
     "api_id" : null,
     "api_name" : "api_demo",
     "api_using_time" : 1580452617000,
     "app_id" : null,
     "app_name" : "app_demo",
     "apply_time" : 1578875421000,
     "approval_time" : null,
     "approver_name" : null,
     "comment" : "Passed",
     "user_name" : "Tom"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Success
400         Bad request
=========== ===========
