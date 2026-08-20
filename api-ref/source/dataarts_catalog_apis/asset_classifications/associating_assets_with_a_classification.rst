:original_name: BatchAssociateClassificationToEntities.html

.. _BatchAssociateClassificationToEntities:

Associating Assets with a Classification
========================================

Function
--------

Associating Assets with Categories in Batches: Categories can be added only to columns of data tables and OBS objects.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/asset/entities/classification

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

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

   +----------------+-----------+-------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter      | Mandatory | Type                                                                                                  | Description           |
   +================+===========+=======================================================================================================+=======================+
   | guids          | Yes       | Array of strings                                                                                      | Data asset list.      |
   +----------------+-----------+-------------------------------------------------------------------------------------------------------+-----------------------+
   | classification | Yes       | :ref:`OpenClassification <batchassociateclassificationtoentities__request_openclassification>` object | Category information. |
   +----------------+-----------+-------------------------------------------------------------------------------------------------------+-----------------------+

.. _batchassociateclassificationtoentities__request_openclassification:

.. table:: **Table 4** OpenClassification

   =========== ========= ====== ================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ================================
   name        Yes       String Category name
   description No        String Category Description
   create_user No        String Category creator.
   create_time No        Number Time when a category is created.
   update_time No        Number Time when a category is updated.
   update_user No        String Category updater.
   guid        No        String GUID of a category.
   =========== ========= ====== ================================

Response Parameters
-------------------

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
     "guids" : [ "0aa90b11-5064-4c6a-9c00-a35267a85aab", "348f0dc5-e03f-487e-a967-3e1abacccce8" ],
     "classification" : {
       "name" : "hive_common"
     }
   }

Example Responses
-----------------

None

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         OK.
400         Bad Request:
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== =============
