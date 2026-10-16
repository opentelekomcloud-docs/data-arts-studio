:original_name: ShowMetricTree.html

.. _ShowMetricTree:

Querying the Metric Asset Directory Tree
========================================

Function
--------

This API is used to query the indicator asset directory tree.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/asset/metric-tree

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------+------------------------------------------------------------------------------------------------+-------------------+
   | Parameter    | Type                                                                                           | Description       |
   +==============+================================================================================================+===================+
   | architecture | Array of :ref:`ArchitectureStatistic <showmetrictree__response_architecturestatistic>` objects | Structure system. |
   +--------------+------------------------------------------------------------------------------------------------+-------------------+

.. _showmetrictree__response_architecturestatistic:

.. table:: **Table 4** ArchitectureStatistic

   +-----------+------------------------------------------------------------------------------------------------+---------------------------------------+
   | Parameter | Type                                                                                           | Description                           |
   +===========+================================================================================================+=======================================+
   | children  | Array of :ref:`ArchitectureStatistic <showmetrictree__response_architecturestatistic>` objects | Indicates the sub-indicator.          |
   +-----------+------------------------------------------------------------------------------------------------+---------------------------------------+
   | count     | Integer                                                                                        | Indicates the number of sub-counters. |
   +-----------+------------------------------------------------------------------------------------------------+---------------------------------------+
   | guid      | String                                                                                         | Asset GUID.                           |
   +-----------+------------------------------------------------------------------------------------------------+---------------------------------------+
   | name      | String                                                                                         | Name                                  |
   +-----------+------------------------------------------------------------------------------------------------+---------------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 7** Response body parameters

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

metric assets.

.. code-block::

   {
     "architecture" : [ {
       "children" : [ {
         "children" : null,
         "count" : 1,
         "guid" : "f31ad3b7-5c54-45e3-8afe-369c43d45438",
         "name" : "process_name_second"
       } ],
       "count" : 0,
       "guid" : "64db45a2-38d1-453d-bb13-404dde03fedc",
       "name" : "process_name_first"
     } ]
   }

Status Codes
------------

=========== ==============
Status Code Description
=========== ==============
200         metric assets.
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== ==============
