:original_name: ChangeSubjects.html

.. _ChangeSubjects:

Modifying or Deleting a Topic Level
===================================

Function
--------

Modify or delete a topic level.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v2/{project_id}/design/subject-levels

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------------+--------------------------+
   | Parameter | Mandatory | Type                                                                            | Description              |
   +===========+===========+=================================================================================+==========================+
   | levels    | No        | Array of :ref:`CatalogLevelVO <changesubjects__request_cataloglevelvo>` objects | Theme level information. |
   +-----------+-----------+---------------------------------------------------------------------------------+--------------------------+

.. _changesubjects__request_cataloglevelvo:

.. table:: **Table 4** CatalogLevelVO

   +-----------+-----------+---------+----------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                        |
   +===========+===========+=========+====================================================+
   | id        | No        | String  | ID, which is a string                              |
   +-----------+-----------+---------+----------------------------------------------------+
   | level     | No        | Integer | Indicates the level. The value ranges from 1 to 7. |
   +-----------+-----------+---------+----------------------------------------------------+
   | name_ch   | No        | String  | Chinese name                                       |
   +-----------+-----------+---------+----------------------------------------------------+
   | name_en   | No        | String  | English name.                                      |
   +-----------+-----------+---------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+----------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                               | Description                                                    |
   +===========+====================================================+================================================================+
   | data      | :ref:`data <changesubjects__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+----------------------------------------------------+----------------------------------------------------------------+

.. _changesubjects__response_data:

.. table:: **Table 6** data

   +-----------+--------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter | Type                                                                           | Description                                                 |
   +===========+================================================================================+=============================================================+
   | value     | :ref:`CatalogLevelVOList <changesubjects__response_cataloglevelvolist>` object | value: unified outer data structure of the returned result. |
   +-----------+--------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _changesubjects__response_cataloglevelvolist:

.. table:: **Table 7** CatalogLevelVOList

   +-----------+----------------------------------------------------------------------------------+--------------------------+
   | Parameter | Type                                                                             | Description              |
   +===========+==================================================================================+==========================+
   | levels    | Array of :ref:`CatalogLevelVO <changesubjects__response_cataloglevelvo>` objects | Theme level information. |
   +-----------+----------------------------------------------------------------------------------+--------------------------+

.. _changesubjects__response_cataloglevelvo:

.. table:: **Table 8** CatalogLevelVO

   ========= ======= ==================================================
   Parameter Type    Description
   ========= ======= ==================================================
   id        String  ID, which is a string
   level     Integer Indicates the level. The value ranges from 1 to 7.
   name_ch   String  Chinese name
   name_en   String  English name.
   ========= ======= ==================================================

**Status code: 400**

.. table:: **Table 9** Response body parameters

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

.. table:: **Table 10** Response body parameters

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

.. table:: **Table 11** Response body parameters

   +------------+--------+--------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                          |
   +============+========+======================================================================================+
   | error_code | String | Error code, for example, DS.6000, indicating that the request fails to be processed. |
   +------------+--------+--------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                        |
   +------------+--------+--------------------------------------------------------------------------------------+
   | data       | Object | Returned data information.                                                           |
   +------------+--------+--------------------------------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 12** Response body parameters

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

This API is used to obtain the level information of a topic in the current workspace.

.. code-block:: text

   PUT https://{endpoint}/v2/{project_id}/design/subject-levels

   {
     "levels" : [ {
       "id" : "1141755876357632000",
       "level" : 1,
       "name_ch" : "Subject Area Group",
       "name_en" : "Business Domain Group"
     }, {
       "id" : "1141755876366020608",
       "level" : 2,
       "name_ch" : "Subject Area",
       "name_en" : "Business Domain"
     }, {
       "id" : "1184953097022242816",
       "level" : 3,
       "name_ch" : "Subject Area L3",
       "name_en" : "Business Domain L3"
     }, {
       "id" : "1184953097022242817",
       "level" : 4,
       "name_ch" : "Subject Area L4",
       "name_en" : "Business Domain L4"
     }, {
       "id" : "1184953097022242818",
       "level" : 5,
       "name_ch" : "Subject Area L5",
       "name_en" : "Business Domain L5"
     }, {
       "id" : "1141755876370214912",
       "level" : 6,
       "name_ch" : "Business Object",
       "name_en" : "Business Object"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is CatalogLevelVOList.

.. code-block::

   {
     "data" : {
       "value" : {
         "levels" : [ {
           "id" : "1141755876357632000",
           "level" : 1,
           "name_ch" : "Subject Area Group",
           "name_en" : "Business Domain Group"
         }, {
           "id" : "1141755876366020608",
           "level" : 2,
           "name_ch" : "Subject Area",
           "name_en" : "Business Domain"
         }, {
           "id" : "1184953097022242816",
           "level" : 3,
           "name_ch" : "Subject Area L3",
           "name_en" : "Business Domain L3"
         }, {
           "id" : "1184953097022242817",
           "level" : 4,
           "name_ch" : "Subject Area L4",
           "name_en" : "Business Domain L4"
         }, {
           "id" : "1184953097022242818",
           "level" : 5,
           "name_ch" : "Subject Area L5",
           "name_en" : "Business Domain L5"
         }, {
           "id" : "1141755876370214912",
           "level" : 6,
           "name_ch" : "Business Object",
           "name_en" : "Business Object"
         } ]
       }
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

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The User Request API does not exist."
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------+
| Status Code | Description                                                           |
+=============+=======================================================================+
| 200         | This operation succeeds, and the returned data is CatalogLevelVOList. |
+-------------+-----------------------------------------------------------------------+
| 400         | BadRequest                                                            |
+-------------+-----------------------------------------------------------------------+
| 401         | Unauthorized                                                          |
+-------------+-----------------------------------------------------------------------+
| 403         | Forbidden                                                             |
+-------------+-----------------------------------------------------------------------+
| 404         | Not Found                                                             |
+-------------+-----------------------------------------------------------------------+
