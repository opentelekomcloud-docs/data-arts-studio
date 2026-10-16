:original_name: InitializeStandardTemplate.html

.. _InitializeStandardTemplate:

Standard Template for Initializing Data
=======================================

Function
--------

Initialize the data standard template.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/design/standards/templates/action

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                   |
   +===========+===========+========+===============================================================================================================+
   | action-id | Yes       | String | If action-id is set to init, this parameter is a fixed parameter for initializing the data standard template. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

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

   +-----------+----------------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                           | Description                                                    |
   +===========+================================================================+================================================================+
   | data      | :ref:`data <initializestandardtemplate__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+----------------------------------------------------------------+----------------------------------------------------------------+

.. _initializestandardtemplate__response_data:

.. table:: **Table 5** data

   +-----------+--------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
   | Parameter | Type                                                                                                   | Description                                           |
   +===========+========================================================================================================+=======================================================+
   | value     | Array of :ref:`StandElementFieldVO <initializestandardtemplate__response_standelementfieldvo>` objects | Array of field details in the data standard template. |
   +-----------+--------------------------------------------------------------------------------------------------------+-------------------------------------------------------+

.. _initializestandardtemplate__response_standelementfieldvo:

.. table:: **Table 6** StandElementFieldVO

   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type    | Description                                                                                                                                                                                                                                                                                                                                                        |
   +===================+=========+====================================================================================================================================================================================================================================================================================================================================================================+
   | fd_name           | String  | Attribute name.                                                                                                                                                                                                                                                                                                                                                    |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fd_name_en        | String  | English name of an attribute.                                                                                                                                                                                                                                                                                                                                      |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | String  | Attribute description.                                                                                                                                                                                                                                                                                                                                             |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | descriptionEn     | String  | Attribute description in English.                                                                                                                                                                                                                                                                                                                                  |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | label             | String  | Attribute tag.                                                                                                                                                                                                                                                                                                                                                     |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | disabled          | Boolean | Disable or not.                                                                                                                                                                                                                                                                                                                                                    |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                | String  | Data standard ID, which is a string                                                                                                                                                                                                                                                                                                                                |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | actived           | Boolean | Indicates whether to display the default item. The default item is displayed and cannot be modified. The value true indicates that the attribute is displayed when the data standard is used (the attribute can be operated during adding, modification, and query). The value false indicates that the attribute is not displayed when the data standard is used. |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | required          | Boolean | Whether the header input parameter is mandatory. true: mandatory; false: optional.                                                                                                                                                                                                                                                                                 |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | searchable        | Boolean | Indicates whether the content can be searched. The value true indicates that the data can be searched on the data standard list page, and the value false indicates that the data cannot be searched on the data standard list page.                                                                                                                               |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | optional_values   | String  | Allowed value.                                                                                                                                                                                                                                                                                                                                                     |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | field_type        | Integer | Field type. The value 0 indicates a system field, and the value 1 indicates a customized field.                                                                                                                                                                                                                                                                    |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | displayed_name    | String  | Frontend display name.                                                                                                                                                                                                                                                                                                                                             |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | displayed_name_en | String  | Frontend display name in English.                                                                                                                                                                                                                                                                                                                                  |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time       | String  | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.                                                                                                                                                                                      |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time       | String  | Update time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.                                                                                                                                                                                        |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by         | String  | Creator.                                                                                                                                                                                                                                                                                                                                                           |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_by         | String  | Person who updates the information.                                                                                                                                                                                                                                                                                                                                |
   +-------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

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

**Status code: 401**

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

**Status code: 403**

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

**Status code: 404**

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

Initialize the data standard template.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/design/standards/templates/action?action-id=init

   {
     "fields" : [ {
       "descriptionEn" : "Standard Name",
       "fd_name" : "nameCh",
       "description" : "Standard Name",
       "required" : true,
       "searchable" : true,
       "actived" : true,
       "label" : "Standard Name",
       "displayed_name" : "Standard Name",
       "displayed_name_en" : "Standard name"
     }, {
       "descriptionEn" : "Standard Code",
       "fd_name" : "nameEn",
       "description" : "Standard Code",
       "required" : true,
       "searchable" : true,
       "actived" : true,
       "label" : "Standard Code",
       "displayed_name" : "Standard Code",
       "displayed_name_en" : "Standard code"
     }, {
       "descriptionEn" : "Data Type",
       "fd_name" : "dataType",
       "description" : "Data Type",
       "required" : true,
       "searchable" : true,
       "actived" : true,
       "label" : "Data type",
       "displayed_name" : "Data Type",
       "displayed_name_en" : "Data type"
     }, {
       "descriptionEn" : "Standard English Name",
       "fd_name" : "englishName",
       "description" : "Identifier Name",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Identifier Name",
       "disabled" : false,
       "displayed_name" : "Identifier Name",
       "displayed_name_en" : "Name (EN)"
     }, {
       "descriptionEn" : "Data Length",
       "fd_name" : "dataLength",
       "description" : "Max. Data Length",
       "required" : false,
       "searchable" : false,
       "actived" : true,
       "label" : "Data Length",
       "disabled" : false,
       "displayed_name" : "Max. Data Length",
       "displayed_name_en" : "Data length"
     }, {
       "descriptionEn" : "Allowed Value",
       "fd_name" : "hasAllowValueList",
       "description" : "Allowed Value Exist",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Allowed Value Exist",
       "disabled" : false,
       "displayed_name" : "Allowed Value Exist",
       "displayed_name_en" : "Allowed value exist"
     }, {
       "descriptionEn" : "Allowed Value List",
       "fd_name" : "allowList",
       "description" : "Allowed Value",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Allowed Value",
       "disabled" : true,
       "displayed_name" : "Allowed Value",
       "displayed_name_en" : "Allowed values"
     }, {
       "descriptionEn" : "Referenced Lookup Table",
       "fd_name" : "referCodeTable",
       "description" : "Lookup Table",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Referenced Lookup Table",
       "disabled" : false,
       "displayed_name" : "Lookup Table",
       "displayed_name_en" : "Lookup table"
     }, {
       "descriptionEn" : "Lookup Table Field",
       "fd_name" : "codeStandColumn",
       "description" : "Lookup Table Field",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Lookup Table Field",
       "disabled" : true,
       "displayed_name" : "Lookup Table Field",
       "displayed_name_en" : "Lookup table field"
     }, {
       "descriptionEn" : "Quality Rule",
       "fd_name" : "dqcRule",
       "description" : "Quality rule",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Quality rule",
       "disabled" : false,
       "displayed_name" : "Quality rule",
       "displayed_name_en" : "Quality rule"
     }, {
       "descriptionEn" : "Owner of Business Rules",
       "fd_name" : "ruleOwner",
       "description" : "Rule Designer",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Rule Designer",
       "disabled" : false,
       "displayed_name" : "Rule Designer",
       "displayed_name_en" : "Rule designer"
     }, {
       "descriptionEn" : "Owner of Data Monitoring",
       "fd_name" : "dataMonitorOwner",
       "description" : "Rule Implementer",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Rule Implementer",
       "disabled" : false,
       "displayed_name" : "Rule Implementer",
       "displayed_name_en" : "Rule implementer"
     }, {
       "descriptionEn" : "Standard Level",
       "fd_name" : "standardLevel",
       "description" : "Level",
       "required" : false,
       "searchable" : false,
       "actived" : false,
       "label" : "Standard Level",
       "disabled" : false,
       "displayed_name" : "Standard Level",
       "displayed_name_en" : "Standard level"
     }, {
       "descriptionEn" : "Description",
       "fd_name" : "description",
       "description" : "Description",
       "required" : false,
       "searchable" : false,
       "actived" : true,
       "label" : "Description",
       "disabled" : false,
       "displayed_name" : "Description",
       "displayed_name_en" : "Description"
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
         "fd_name" : "nameCh",
         "fd_name_en" : null,
         "description" : "Standard Name",
         "id" : "1230921379143135232",
         "actived" : true,
         "required" : true,
         "searchable" : true,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "nameEn",
         "fd_name_en" : null,
         "description" : "Standard Code",
         "id" : "1230921379164106752",
         "actived" : true,
         "required" : true,
         "searchable" : true,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "dataType",
         "fd_name_en" : null,
         "description" : "Data Type",
         "id" : "1230921379180883968",
         "actived" : true,
         "required" : true,
         "searchable" : true,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "englishName",
         "fd_name_en" : null,
         "description" : "Identifier Name",
         "id" : "1230921379201855488",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "dataLength",
         "fd_name_en" : null,
         "description" : "Data Length",
         "id" : "1230921379222827008",
         "actived" : true,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "hasAllowValueList",
         "fd_name_en" : null,
         "description" : "Allowed Value Exist",
         "id" : "1230921379239604224",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "allowList",
         "fd_name_en" : null,
         "description" : "Allowed Value",
         "id" : "1230921379260575744",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "referCodeTable",
         "fd_name_en" : null,
         "description" : "Lookup Table",
         "id" : "1230921379277352960",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "codeStandColumn",
         "fd_name_en" : null,
         "description" : "Lookup Table Field",
         "id" : "1230921379298324480",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "dqcRule",
         "fd_name_en" : null,
         "description" : "Quality rule",
         "id" : "1230921379315101696",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "ruleOwner",
         "fd_name_en" : null,
         "description" : "Rule Designer",
         "id" : "1230921379340267520",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "dataMonitorOwner",
         "fd_name_en" : null,
         "description" : "Rule Implementer",
         "id" : "1230921379361239040",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "standardLevel",
         "fd_name_en" : null,
         "description" : "Level",
         "id" : "1230921379382210560",
         "actived" : false,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
       }, {
         "fd_name" : "description",
         "fd_name_en" : null,
         "description" : "Description",
         "id" : "1230921379398987776",
         "actived" : true,
         "required" : false,
         "searchable" : false,
         "optional_values" : null,
         "field_type" : null,
         "displayed_name" : null,
         "displayed_name_en" : null,
         "create_time" : "2024-04-19T16:42:06+08:00",
         "update_time" : "2024-04-19T16:42:06+08:00",
         "create_by" : "test_uesr",
         "update_by" : "test_uesr"
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

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "DS.60xx",
     "error_msg" : "The User Request API does not exist."
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
404         Not Found
=========== ============
