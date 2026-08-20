:original_name: ModifyCustomizedFields.html

.. _ModifyCustomizedFields:

Modifying a Customized Item
===========================

Function
--------

Modify customized items (including table customized items, attribute customized items, theme customized items, and service indicator customized items).

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v2/{project_id}/design/customized-fields

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

   +-----------------+-----------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                            | Description                                     |
   +=================+=================+=================================================================================================+=================================================+
   | type            | Yes             | String                                                                                          | Type of a customized item.                      |
   |                 |                 |                                                                                                 |                                                 |
   |                 |                 |                                                                                                 | Options:                                        |
   |                 |                 |                                                                                                 |                                                 |
   |                 |                 |                                                                                                 | -  TABLE: table customized item                 |
   |                 |                 |                                                                                                 |                                                 |
   |                 |                 |                                                                                                 | -  ATTRIBUTE: customized attribute item         |
   |                 |                 |                                                                                                 |                                                 |
   |                 |                 |                                                                                                 | -  SUBJECT: theme customization item            |
   |                 |                 |                                                                                                 |                                                 |
   |                 |                 |                                                                                                 | -  METRIC: service indicator customization item |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | fields          | No              | Array of :ref:`CustomizedFieldsVO <modifycustomizedfields__request_customizedfieldsvo>` objects | List of customized items.                       |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------+

.. _modifycustomizedfields__request_customizedfieldsvo:

.. table:: **Table 4** CustomizedFieldsVO

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                       |
   +=================+=================+=================+===================================================================================================+
   | id              | No              | String          | ID, which is a string                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | name_ch         | Yes             | String          | Chinese name of a user-defined item.                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | name_en         | Yes             | String          | English name of a customized item.                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | not_null        | Yes             | Boolean         | Whether a parameter is mandatory.                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | optional_values | No              | String          | Sorting order. Options: If there are multiple optional values, separate them with semicolons (;). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Type of a customized item.                                                                        |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | Options:                                                                                          |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  TABLE: table customized item                                                                   |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  ATTRIBUTE: customized attribute item                                                           |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  SUBJECT: theme customization item                                                              |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  METRIC: service indicator customization item                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | ordinal         | No              | Integer         | System sorting field. You do not need to set this parameter when creating or modifying a record.  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Description of a user-defined item.                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                       | Description                                                    |
   +===========+============================================================+================================================================+
   | data      | :ref:`data <modifycustomizedfields__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+------------------------------------------------------------+----------------------------------------------------------------+

.. _modifycustomizedfields__response_data:

.. table:: **Table 6** data

   +-----------+--------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                             | Description                       |
   +===========+==================================================================================================+===================================+
   | value     | Array of :ref:`CustomizedFieldsVO <modifycustomizedfields__response_customizedfieldsvo>` objects | Data connection information array |
   +-----------+--------------------------------------------------------------------------------------------------+-----------------------------------+

.. _modifycustomizedfields__response_customizedfieldsvo:

.. table:: **Table 7** CustomizedFieldsVO

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================+
   | id                    | String                | ID, which is a string                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_ch               | String                | Chinese name of a user-defined item.                                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_en               | String                | English name of a customized item.                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_null              | Boolean               | Whether a parameter is mandatory.                                                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | optional_values       | String                | Sorting order. Options: If there are multiple optional values, separate them with semicolons (;).                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Type of a customized item.                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TABLE: table customized item                                                                                                                                               |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  ATTRIBUTE: customized attribute item                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUBJECT: theme customization item                                                                                                                                          |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  METRIC: service indicator customization item                                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ordinal               | Integer               | System sorting field. You do not need to set this parameter when creating or modifying a record.                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Description of a user-defined item.                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by             | String                | Creator, which is read-only.                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_by             | String                | Updater, which is read-only.                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 8** Response body parameters

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

**Status code: 403**

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

Example Requests
----------------

This API is used to modify a customized item of a table.

.. code-block:: text

   PUT https://{endpoint}/v2/{project_id}/design/customized-fields

   {
     "type" : "TABLE",
     "fields" : [ {
       "id" : "1211611269321355264",
       "name_ch" : "User-defined item 1",
       "name_en" : "selfDefine1",
       "not_null" : false,
       "optional_values" : "",
       "description" : "Test 1",
       "ordinal" : 0,
       "type" : "TABLE"
     }, {
       "id" : "1211611269321355265",
       "name_ch" : "User-defined item 2",
       "name_en" : "selfDefine2",
       "not_null" : true,
       "optional_values" : "",
       "description" : "Modification 2",
       "ordinal" : 1,
       "type" : "TABLE"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "data" : {
       "value" : [ {
         "id" : "1211611269321355264",
         "name_ch" : "User-defined item 1",
         "name_en" : "selfDefine1",
         "not_null" : false,
         "optional_values" : "",
         "type" : "TABLE",
         "ordinal" : 0,
         "description" : "Test 1",
         "create_by" : null,
         "update_by" : null,
         "create_time" : null,
         "update_time" : null
       }, {
         "id" : "1211611269321355265",
         "name_ch" : "User-defined item 2",
         "name_en" : "selfDefine2",
         "not_null" : true,
         "optional_values" : "",
         "type" : "TABLE",
         "ordinal" : 1,
         "description" : "Modification 2",
         "create_by" : null,
         "update_by" : null,
         "create_time" : null,
         "update_time" : null
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

=========== ============
Status Code Description
=========== ============
200         Success
400         BadRequest
401         Unauthorized
403         Forbidden
=========== ============
