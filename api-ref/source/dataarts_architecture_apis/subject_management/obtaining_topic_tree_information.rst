:original_name: ListBusiness.html

.. _ListBusiness:

Obtaining Topic Tree Information
================================

Function
--------

Obtain the data asset subject tree information l1, l2, and l3.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/subjects/business

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                         |
   +===========+===========+=========+=====================================================================================================================================================================================================================================+
   | limit     | No        | Integer | Number of records to be queried on each page, that is, Y records to be queried. The default value is 50, and the value range is [1,100].                                                                                            |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset    | No        | Integer | Start coordinate of the query, that is, the number of skipped data records. The value can only be 0 or an integer multiple of limit. If the value does not meet the requirement, the value is rounded down. The default value is 0. |
   +-----------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | IAM token, which is obtained by calling the IAM API for obtaining a user token (value of X-Subject-Token in the response header).                                  |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This field is mandatory for authentication using tokens.                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace       | Yes             | String          | Workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Project-Id    | No              | String          | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                            |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is mandatory for API requests that use AK/SK authentication in multi-project scenarios.                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Default value: application/json;charset=UTF-8                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | This parameter is optional. If the body is available, this parameter is mandatory. If the body is unavailable, you do not need to set this parameter or verify it. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   data      Object Returned data information.
   ========= ====== ==========================

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 6** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

**Status code: 403**

.. table:: **Table 7** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

Example Requests
----------------

Obtain the number of data asset topics l1, l2, and l3 in the current workspace.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/subjects/business

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is all L1, L2, and L3 entities.

.. code-block::

   {
     "data" : {
       "value" : [ {
         "id" : "1170064658061799424",
         "name" : "test_subject",
         "qname" : "test_subject@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-9ce2cfd08fda4f3b95faa5ba65fa5ec3",
         "guid" : null,
         "ordinal" : 3,
         "row" : null,
         "catalog" : {
           "versionName" : null,
           "versionTag" : null,
           "versionId" : null,
           "createBy" : "0833a573fe80d5401f6dc010a775569a",
           "updateBy" : "0833a573fe80d5401f6dc010a775569a",
           "createTime" : "2023-11-03T10:19:13.000Z",
           "updateTime" : "2023-11-03T10:28:07.000Z",
           "l3Id" : null,
           "l2Id" : null,
           "alias" : "",
           "encoding" : null,
           "prefix" : null,
           "codeNum" : null,
           "id" : "1170064658061799424",
           "nameCh" : "test_subject",
           "nameEn" : "test_subject",
           "qualifiedName" : "test_subject@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-9ce2cfd08fda4f3b95faa5ba65fa5ec3",
           "description" : "",
           "owner" : "0833a573fe80d5401f6dc010a775569a",
           "guid" : "8c930e34-0003-4999-ab79-66374435d980",
           "code" : null,
           "tenantId" : "0833a5737480d53b2f25c010dc1a7b88-workspace-9ce2cfd08fda4f3b95faa5ba65fa5ec3",
           "selfDefinedFields" : [ ],
           "dataOwner" : "",
           "dataOwnerList" : "[\"test_user\"]",
           "dataDepartment" : null,
           "path" : "test_subject",
           "parentId" : null,
           "level" : 1,
           "ordinal" : 3,
           "status" : "PUBLISHED",
           "approvalInfo" : null,
           "newBiz" : null,
           "fromPublic" : false,
           "swapOrderId" : null,
           "levelStr" : "1",
           "lastL2Id" : null
         },
         "attributes" : {
           "alias" : "",
           "approvalInfo" : null,
           "code" : null,
           "codeNum" : null,
           "createBy" : "0833a573fe80d5401f6dc010a775569a",
           "createTime" : "2023-11-03T10:19:13.000Z",
           "dataDepartment" : null,
           "dataOwner" : "",
           "dataOwnerList" : [ "test_user" ],
           "description" : "",
           "encoding" : null,
           "fromPublic" : false,
           "guid" : "8c930e34-0003-4999-ab79-66374435d980",
           "id" : "1170064658061799424",
           "l1" : true,
           "l2" : false,
           "l2Id" : null,
           "l3" : false,
           "l3Id" : null,
           "lastL2Id" : null,
           "level" : 1,
           "levelStr" : "1",
           "name" : "test_subject",
           "nameCh" : "test_subject",
           "nameEn" : "test_subject",
           "nameEng" : "test_subject",
           "newBiz" : null,
           "ordinal" : 3,
           "owner" : "0833a573fe80d5401f6dc010a775569a",
           "parentId" : null,
           "path" : "test_subject",
           "prefix" : null,
           "qualifiedName" : "test_subject@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-9ce2cfd08fda4f3b95faa5ba65fa5ec3",
           "selfDefinedFields" : [ ],
           "status" : "PUBLISHED",
           "swapOrderId" : null,
           "tenantId" : "0833a5737480d53b2f25c010dc1a7b88-workspace-9ce2cfd08fda4f3b95faa5ba65fa5ec3",
           "updateBy" : "0833a573fe80d5401f6dc010a775569a",
           "updateTime" : "2023-11-03T10:28:07.000Z",
           "versionId" : null,
           "versionName" : null,
           "versionTag" : null
         },
         "childs" : [ ],
         "count" : 0,
         "status" : "PUBLISHED"
       } ]
     }
   }

**Status code: 400**

BadRequest

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The user request is illegal."
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "User authentication failed."
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The user does not have permission to call this API."
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | This operation succeeds, and the returned data is all L1, L2, and L3 entities. |
+-------------+--------------------------------------------------------------------------------+
| 400         | BadRequest                                                                     |
+-------------+--------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                   |
+-------------+--------------------------------------------------------------------------------+
| 403         | Forbidden                                                                      |
+-------------+--------------------------------------------------------------------------------+
