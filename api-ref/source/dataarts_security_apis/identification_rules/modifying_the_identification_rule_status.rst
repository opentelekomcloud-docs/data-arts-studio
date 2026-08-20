:original_name: UpdateSecurityRuleEnableStatus.html

.. _UpdateSecurityRuleEnableStatus:

Modifying the Identification Rule Status
========================================

Function
--------

This API is used to modify the identification rule status.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v1/{project_id}/security/data-classification/rule/switch-status/{id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Recognition rule ID.                                                                                                    |
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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+---------+------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                          |
   +===========+===========+=========+======================================================+
   | enable    | No        | Boolean | Indicates whether to enable the identification rule. |
   +-----------+-----------+---------+------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ======= =====================================================
   Parameter Type    Description
   ========= ======= =====================================================
   rule_id   String  Recognition rule ID.
   rule_name String  Recognition rule name.
   enabled   Boolean Indicates whether the identification rule is enabled.
   ========= ======= =====================================================

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

.. code-block::

   /v1/0833a5737480d53b2f25c010dc1a7b88/security/data-classification/rule/switch-status/8a9480a58b0d64a1018b137553670006

   {
     "enable" : true
   }

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "enabled" : true,
     "rule_id" : "8a9480a58b0d64a1018b137553670006",
     "rule_name" : "Special_Administrative_Region"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
400         Bad Request
=========== ===========
