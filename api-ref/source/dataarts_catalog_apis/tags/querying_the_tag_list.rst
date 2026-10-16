:original_name: ShowGlossaryList.html

.. _ShowGlossaryList:

Querying the Tag List
=====================

Function
--------

This API is used to query the tag list.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/tags

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                            |
   +=============+===========+========+========================================================================================+
   | type        | No        | String | Default label type: all.                                                               |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | name        | No        | String | Label name                                                                             |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | create_user | No        | String | Tag creation user.                                                                     |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | start       | No        | String | Start time                                                                             |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | end         | No        | String | End time.                                                                              |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | limit       | No        | String | Pagination parameter: maximum number of records on each page. The default value is 10. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | offset      | No        | String | Number of pages. The default value is **0**.                                           |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | sort_by     | No        | String | Sorting field. The default value is **createTime**.                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+
   | sort_order  | No        | String | Sorting order. The default value is **desc**.                                          |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace    | Yes       | String | Workspace ID. For details about how to obtain it, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+--------------------------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                                           | Description                  |
   +===========+================================================================================+==============================+
   | count     | Integer                                                                        | Total number.                |
   +-----------+--------------------------------------------------------------------------------+------------------------------+
   | limit     | Integer                                                                        | Pagination parameter limit.  |
   +-----------+--------------------------------------------------------------------------------+------------------------------+
   | offset    | Integer                                                                        | Pagination parameter offset. |
   +-----------+--------------------------------------------------------------------------------+------------------------------+
   | quota     | Integer                                                                        | Metric quota.                |
   +-----------+--------------------------------------------------------------------------------+------------------------------+
   | tags      | Array of :ref:`GlossaryInfo <showglossarylist__response_glossaryinfo>` objects | List of tags.                |
   +-----------+--------------------------------------------------------------------------------+------------------------------+

.. _showglossarylist__response_glossaryinfo:

.. table:: **Table 5** GlossaryInfo

   =========== ====== =======================
   Parameter   Type   Description
   =========== ====== =======================
   name        String Tag name.
   description String Description
   guid        String Specifies the tag GUID.
   create_user String Create a user.
   create_time Number Creation time.
   =========== ====== =======================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "count" : 20,
     "limit" : 1,
     "offset" : 1,
     "quota" : 100,
     "tags" : [ {
       "create_time" : 1663826213551,
       "create_user" : "user_demo",
       "description" : null,
       "guid" : "b4412463-7253-4b60-8184-c938fe46d0aa",
       "name" : "123"
     } ]
   }

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         OK.
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
=========== =============
