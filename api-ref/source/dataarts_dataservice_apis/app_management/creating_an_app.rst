:original_name: CreateApp.html

.. _CreateApp:

Creating an App
===============

Function
--------

This API is used to create an app

or an IAM app.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/service/apps

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

   +------------------+-----------------+-----------------+-------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                         |
   +==================+=================+=================+=====================================+
   | app_type         | No              | String          | App type                            |
   |                  |                 |                 |                                     |
   |                  |                 |                 | The following values are available: |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **APP**                          |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **IAM**                          |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **APIG** (discarded)             |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **APIGW** (discarded)            |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **DLM** (discarded)              |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **ROMA_APIC** (discarded)        |
   +------------------+-----------------+-----------------+-------------------------------------+
   | name             | No              | String          | Application name.                   |
   +------------------+-----------------+-----------------+-------------------------------------+
   | description      | No              | String          | Application description.            |
   +------------------+-----------------+-----------------+-------------------------------------+
   | apig_type        | No              | String          | Gateway type                        |
   |                  |                 |                 |                                     |
   |                  |                 |                 | Enumerated values:                  |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **APIG**: APIG gateway           |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **APIGW**: APIGW gateway         |
   |                  |                 |                 |                                     |
   |                  |                 |                 | -  **ROMA_APIC**: ROMA gateway      |
   +------------------+-----------------+-----------------+-------------------------------------+
   | apig_instance_id | No              | String          | Gateway instance ID.                |
   +------------------+-----------------+-----------------+-------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | id                    | String                | App ID                                        |
   +-----------------------+-----------------------+-----------------------------------------------+
   | name                  | String                | Application name.                             |
   +-----------------------+-----------------------+-----------------------------------------------+
   | description           | String                | Application description.                      |
   +-----------------------+-----------------------+-----------------------------------------------+
   | app_key               | String                | Application key.                              |
   +-----------------------+-----------------------+-----------------------------------------------+
   | app_secret            | String                | Application secret.                           |
   +-----------------------+-----------------------+-----------------------------------------------+
   | register_time         | Long                  | Creation time.                                |
   +-----------------------+-----------------------+-----------------------------------------------+
   | update_time           | Long                  | Update time.                                  |
   +-----------------------+-----------------------+-----------------------------------------------+
   | create_user           | String                | Creator.                                      |
   +-----------------------+-----------------------+-----------------------------------------------+
   | update_user           | String                | Updater.                                      |
   +-----------------------+-----------------------+-----------------------------------------------+
   | app_type              | String                | App type.                                     |
   |                       |                       |                                               |
   |                       |                       | Enumerated values:                            |
   |                       |                       |                                               |
   |                       |                       | -  **APP**: app                               |
   |                       |                       |                                               |
   |                       |                       | -  **IAM**: IAM                               |
   |                       |                       |                                               |
   |                       |                       | -  **APIG**: APIG (discarded)                 |
   |                       |                       |                                               |
   |                       |                       | -  **APIGW**: APIGW (deprecated)              |
   |                       |                       |                                               |
   |                       |                       | -  **DLM**: DataArts DataService (deprecated) |
   |                       |                       |                                               |
   |                       |                       | -  **ROMA_APIC**: ROMA (deprecated)           |
   +-----------------------+-----------------------+-----------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Create an app.

.. code-block::

   /v1/0833a5737480d53b2f250010d01a7b88/service/apps

   {
     "app_type" : "APP",
     "name" : "app_test_001",
     "description" : "This is the app's description."
   }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "id" : "908489209a320df61607355c57c82882",
     "name" : "app_test_001",
     "description" : "This is the app's description.",
     "app_key" : "fbbf9462bb434cb4a13ee7d2bb70c418",
     "app_secret" : "c1245f01937442e098ffa6ff134cb3dc",
     "register_time" : 1578284788000,
     "update_time" : 1578284788000,
     "create_user" : "create_user",
     "update_user" : "update_user",
     "app_type" : "APP"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Success
400         Bad request
=========== ===========
