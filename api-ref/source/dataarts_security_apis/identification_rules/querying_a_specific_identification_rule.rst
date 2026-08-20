:original_name: ShowSecurityDataClassificationRule.html

.. _ShowSecurityDataClassificationRule:

Querying a Specific Identification Rule
=======================================

Function
--------

This API is used to query a specific identification rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1/{project_id}/security/data-classification/rule/{id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Indicates the ID of the rule to be queried.                                                                             |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                             |
   +==============+===========+========+=========================================================================================================================================================================================+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                       |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header). This parameter is mandatory for token authentication. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------------+---------+-----------------------------------------------------------------------------------+
   | Parameter          | Type    | Description                                                                       |
   +====================+=========+===================================================================================+
   | uuid               | String  | Rule ID.                                                                          |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | rule_type          | String  | Rule type. The options are CUSTOM and BUILTIN.                                    |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | secrecy_level      | String  | Security level name.                                                              |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | secrecy_level_num  | Long    | Confidentiality level.                                                            |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | name               | String  | Indicates the rule name.                                                          |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | guid               | String  | guid.                                                                             |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | enable             | Boolean | Indicates whether the rule is enabled.                                            |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | method             | String  | Rule method. The value can be **REGULAR**, **NONE**, **DEFAULT**, or **COMBINE**. |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | content_expression | String  | Content expression.                                                               |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | column_expression  | String  | Column expression.                                                                |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | commit_expression  | String  | Remarks expression.                                                               |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | combine_expression | String  | Condition expression                                                              |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | project_id         | String  | Project ID.                                                                       |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | description        | String  | Specifies the assignment description.                                             |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | created_by         | String  | Policy creator.                                                                   |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | created_at         | Long    | Time when a policy is created.                                                    |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | updated_by         | String  | Person who updates the policy.                                                    |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | updated_at         | Long    | Time when a policy is updated.                                                    |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | builtin_rule_id    | String  | ID of a built-in rule.                                                            |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | category_id        | String  | Category ID.                                                                      |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | instance_id        | String  | Instance ID.                                                                      |
   +--------------------+---------+-----------------------------------------------------------------------------------+
   | match_type         | String  | Match type.                                                                       |
   +--------------------+---------+-----------------------------------------------------------------------------------+

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

.. code-block::

   /v1/0833a5737480d53b2f25c010dc1a7b88/security/data-classification/rule/8a94800e8b753a35018b7e6be6950023

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "builtin_rule_id" : null,
     "category_id" : "0cce38e7c28547828905ae9e4f10a4bf",
     "column_expression" : null,
     "commit_expression" : null,
     "content_expression" : ".*",
     "created_at" : 1698633124002,
     "created_by" : "chenxiaoyu",
     "description" : "",
     "enable" : true,
     "guid" : null,
     "instance_id" : "dd97167b873d4a79b2aad54d4370a3bc",
     "match_type" : null,
     "method" : "REGULAR",
     "name" : "matchRules",
     "project_id" : "0833a5737480d53b2f25c010dc1a7b88",
     "rule_type" : "CUSTOM",
     "secrecy_level" : "asd",
     "secrecy_level_num" : 1,
     "updated_at" : 1698633124002,
     "updated_by" : "chenxiaoyu",
     "uuid" : "8a94800e8b753a35018b7e6be6950023"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
400         Bad Request
=========== ===========
