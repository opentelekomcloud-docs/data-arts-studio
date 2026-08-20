:original_name: ShowStandardTemplate.html

.. _ShowStandardTemplate:

Querying a Data Standard Template
=================================

Function
--------

This API is used to query data standard templates in the current workspace.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/standards/templates

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

   +-----------+----------------------------------------------------------+--------------------------+
   | Parameter | Type                                                     | Description              |
   +===========+==========================================================+==========================+
   | data      | :ref:`data <showstandardtemplate__response_data>` object | Data returned by the API |
   +-----------+----------------------------------------------------------+--------------------------+

.. _showstandardtemplate__response_data:

.. table:: **Table 5** data

   +-----------+------------------------------------------------------------+-----------------------------------------------+
   | Parameter | Type                                                       | Description                                   |
   +===========+============================================================+===============================================+
   | value     | :ref:`value <showstandardtemplate__response_value>` object | Result of querying the data standard template |
   +-----------+------------------------------------------------------------+-----------------------------------------------+

.. _showstandardtemplate__response_value:

.. table:: **Table 6** value

   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                                             | Description                                                                                |
   +================+==================================================================================================+============================================================================================+
   | allFields      | Array of :ref:`StandElementFieldVO <showstandardtemplate__response_standelementfieldvo>` objects | All attributes of the data standard. The set contains a single StandElementFieldVO object. |
   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | optional       | Array of :ref:`StandElementFieldVO <showstandardtemplate__response_standelementfieldvo>` objects | This parameter is optional. The set contains a single StandElementFieldVO object.          |
   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | system_default | Array of :ref:`StandElementFieldVO <showstandardtemplate__response_standelementfieldvo>` objects | System default item. The collection contains a single StandElementFieldVO object.          |
   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | custom         | Array of :ref:`StandElementFieldVO <showstandardtemplate__response_standelementfieldvo>` objects | User-defined item. The collection contains a single StandElementFieldVO object.            |
   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | hasTemplate    | Boolean                                                                                          | Whether to use the template                                                                |
   +----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _showstandardtemplate__response_standelementfieldvo:

.. table:: **Table 7** StandElementFieldVO

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

**Status code: 404**

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

Example Requests
----------------

This API is used to query data standard templates in the current workspace.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/standards/templates

Example Responses
-----------------

**Status code: 200**

This operation succeeds, and the returned data is a StandElementFieldVO list.

.. code-block::

   {
     "data" : {
       "value" : {
         "allFields" : [ {
           "fd_name" : "nameCh",
           "fd_name_en" : null,
           "description" : "Standard Name",
           "id" : "1020622096960831488",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "nameEn",
           "fd_name_en" : null,
           "description" : "Standard Code",
           "id" : "1020622096985997312",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dataType",
           "fd_name_en" : null,
           "description" : "Data type",
           "id" : "1020622097006968832",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dataLength",
           "fd_name_en" : null,
           "description" : "Max. Data Length",
           "id" : "1020622097032134656",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "hasAllowValueList",
           "fd_name_en" : null,
           "description" : "Allowed Value Exist",
           "id" : "1020622097048911872",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "allowList",
           "fd_name_en" : null,
           "description" : "Allowed Value",
           "id" : "1020622097065689088",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "referCodeTable",
           "fd_name_en" : null,
           "description" : "Lookup Table",
           "id" : "1020622097086660608",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "codeStandColumn",
           "fd_name_en" : null,
           "description" : "Lookup Table Field",
           "id" : "1020622097103437824",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dqcRule",
           "fd_name_en" : null,
           "description" : "Quality rule",
           "id" : "1020622097124409344",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "ruleOwner",
           "fd_name_en" : null,
           "description" : "Rule Designer",
           "id" : "1020622097141186560",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dataMonitorOwner",
           "fd_name_en" : null,
           "description" : "Rule Implementer",
           "id" : "1020622097162158080",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "standardLevel",
           "fd_name_en" : null,
           "description" : "Standard Level",
           "id" : "1020622097178935296",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "description",
           "fd_name_en" : null,
           "description" : "Description",
           "id" : "1020622097195712512",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "englishName",
           "fd_name_en" : null,
           "description" : "Identifier Name",
           "id" : "1185628711836360704",
           "actived" : true,
           "required" : false,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2023-12-16T17:05:13+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         } ],
         "custom" : [ ],
         "optional" : [ {
           "fd_name" : "dataLength",
           "fd_name_en" : null,
           "description" : "Max. Data Length",
           "id" : "1020622097032134656",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "hasAllowValueList",
           "fd_name_en" : null,
           "description" : "Allowed Value Exist",
           "id" : "1020622097048911872",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "allowList",
           "fd_name_en" : null,
           "description" : "Allowed Value",
           "id" : "1020622097065689088",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "referCodeTable",
           "fd_name_en" : null,
           "description" : "Lookup Table",
           "id" : "1020622097086660608",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "codeStandColumn",
           "fd_name_en" : null,
           "description" : "Lookup Table Field",
           "id" : "1020622097103437824",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dqcRule",
           "fd_name_en" : null,
           "description" : "Quality rule",
           "id" : "1020622097124409344",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "ruleOwner",
           "fd_name_en" : null,
           "description" : "Rule Designer",
           "id" : "1020622097141186560",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dataMonitorOwner",
           "fd_name_en" : null,
           "description" : "Rule Implementer",
           "id" : "1020622097162158080",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "standardLevel",
           "fd_name_en" : null,
           "description" : "Standard Level",
           "id" : "1020622097178935296",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "description",
           "fd_name_en" : null,
           "description" : "Description",
           "id" : "1020622097195712512",
           "actived" : true,
           "required" : false,
           "searchable" : false,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "englishName",
           "fd_name_en" : null,
           "description" : "Identifier Name",
           "id" : "1185628711836360704",
           "actived" : true,
           "required" : false,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2023-12-16T17:05:13+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         } ],
         "hasTemplate" : true,
         "system_default" : [ {
           "fd_name" : "nameCh",
           "fd_name_en" : null,
           "description" : "Standard Name",
           "id" : "1020622096960831488",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "nameEn",
           "fd_name_en" : null,
           "description" : "Standard Code",
           "id" : "1020622096985997312",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
         }, {
           "fd_name" : "dataType",
           "fd_name_en" : null,
           "description" : "Data type",
           "id" : "1020622097006968832",
           "actived" : true,
           "required" : true,
           "searchable" : true,
           "optional_values" : null,
           "field_type" : null,
           "displayed_name" : null,
           "displayed_name_en" : null,
           "create_time" : "2022-09-17T09:07:50+08:00",
           "update_time" : "2024-03-13T16:48:56+08:00",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr"
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

+-------------+-------------------------------------------------------------------------------+
| Status Code | Description                                                                   |
+=============+===============================================================================+
| 200         | This operation succeeds, and the returned data is a StandElementFieldVO list. |
+-------------+-------------------------------------------------------------------------------+
| 400         | BadRequest                                                                    |
+-------------+-------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                  |
+-------------+-------------------------------------------------------------------------------+
| 403         | Forbidden                                                                     |
+-------------+-------------------------------------------------------------------------------+
| 404         | Not Found                                                                     |
+-------------+-------------------------------------------------------------------------------+
