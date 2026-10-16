:original_name: ShowCodeTableById.html

.. _ShowCodeTableById:

Viewing Lookup Table Details
============================

Function
--------

This API is used to view details about a lookup table by ID.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/code-tables/{id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | id         | Yes       | String | Entity ID, which is a string                                                                                            |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                  | Description                                                    |
   +===========+=======================================================+================================================================+
   | data      | :ref:`data <showcodetablebyid__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+-------------------------------------------------------+----------------------------------------------------------------+

.. _showcodetablebyid__response_data:

.. table:: **Table 4** data

   +-----------+---------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                | Description           |
   +===========+=====================================================================+=======================+
   | value     | :ref:`CodeTableVO <showcodetablebyid__response_codetablevo>` object | Code table structure. |
   +-----------+---------------------------------------------------------------------+-----------------------+

.. _showcodetablebyid__response_codetablevo:

.. table:: **Table 5** CodeTableVO

   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                    | Description                                                                                                                                                                   |
   +=======================+=========================================================================================+===============================================================================================================================================================================+
   | id                    | String                                                                                  | Lookup table ID, which is a string                                                                                                                                            |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_en               | String                                                                                  | Table name, in English.                                                                                                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_ch               | String                                                                                  | Table name, in Chinese.                                                                                                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tb_version            | Integer                                                                                 | Table version.                                                                                                                                                                |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory_id          | String                                                                                  | Directory ID, which is a string                                                                                                                                               |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory_path        | String                                                                                  | Directory tree.                                                                                                                                                               |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                  | Description.                                                                                                                                                                  |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by             | String                                                                                  | Creator.                                                                                                                                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                  | Release status of an entity. This parameter is read-only and does not need to be set during creation and update.                                                              |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | Options:                                                                                                                                                                      |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  DRAFT: draft                                                                                                                                                               |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  PUBLISH_DEVELOPING: to be reviewed                                                                                                                                         |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  PUBLISHED: released                                                                                                                                                        |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  OFFLINE_DEVELOPING: to be reviewed                                                                                                                                         |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  OFFLINE: offline                                                                                                                                                           |
   |                       |                                                                                         |                                                                                                                                                                               |
   |                       |                                                                                         | -  REJECT: rejected                                                                                                                                                           |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                                                                                  | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z. |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                                                                                  | Update time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.   |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | approval_info         | :ref:`ApprovalVO <showcodetablebyid__response_approvalvo>` object                       | Approval information. This parameter is read-only. Latest review information about a business object, including the business details, reviewer information, and review time.  |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | new_biz               | :ref:`BizVersionManageVO <showcodetablebyid__response_bizversionmanagevo>` object       | Service version management. This parameter is read-only.                                                                                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_table_fields     | Array of :ref:`CodeTableFieldVO <showcodetablebyid__response_codetablefieldvo>` objects | Code list attribute information.                                                                                                                                              |
   +-----------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showcodetablebyid__response_approvalvo:

.. table:: **Table 6** ApprovalVO

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================+
   | id                    | String                | Application ID, which is a string                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Project ID. For details about how to obtain the project ID, see the API path parameter project_id.                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_ch               | String                | Chinese name of a service.                                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_en               | String                | English name of a service.                                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_id                | String                | Business ID, which is a string                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_type              | String                | Business entity type.                                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Options:                                                                                                                                        |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  AGGREGATION_LOGIC_TABLE: summary table                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  ATOMIC_INDEX: atomic metric                                                                                                                  |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  ATOMIC_METRIC: atomic metric (new)                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  BIZ_CATALOG: process architecture directory                                                                                                  |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  BIZ_METRIC: service indicator                                                                                                                |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  CODE_TABLE: code table                                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  COMMON_CONDITION: general filter                                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  COMPOSITE_METRIC: Compound Metric (new)                                                                                                      |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  COMPOUND_METRIC: compound metric                                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  CONDITION_GROUP: restriction group                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DEGENERATE_DIMENSION: degenerate dimension                                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DERIVATIVE_INDEX: derivative indicator                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DERIVED_METRIC: derivative indicator (new)                                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIMENSION: dimension                                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIMENSION_ATTRIBUTE: dimension attribute                                                                                                     |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIMENSION_HIERARCHIES: dimension level                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIMENSION_LOGIC_TABLE: dimension table                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIMENSION_TABLE_ATTRIBUTE: dimension attribute                                                                                               |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DIRECTORY: directory                                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  FACT_ATTRIBUTE: fact table attribute                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  FACT_DIMENSION: fact table dimension                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  FACT_LOGIC_TABLE: fact table                                                                                                                 |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  FACT_MEASURE: fact table measurement                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  FUNCTION: function                                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  INFO_ARCH: information architecture (used for modifying themes in batches)                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  MODEL: model                                                                                                                                 |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  QUALITY_RULE: quality rule                                                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  SECRECY_LEVEL: security level                                                                                                                |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  STANDARD_ELEMENT: data standard                                                                                                              |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  STANDARD_ELEMENT_TEMPLATE: data standard template                                                                                            |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  SUBJECT: theme                                                                                                                               |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  Dimension attributes of SUMMARY_DIMENSION_ATTRIBUTE: summary tables                                                                          |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  SUMMARY_INDEX: summary table indicator attribute                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  SUMMARY_TIME: time period attribute of the SDR table                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TABLE_MODEL: relationship model (logical model/physical model)                                                                               |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TABLE_MODEL_ATTRIBUTE: relationship model attribute (logical model/physical model)                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TABLE_MODEL_LOGIC: logical entity                                                                                                            |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TABLE_TYPE: table type                                                                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TAG: tag                                                                                                                                     |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  TIME_CONDITION: time restriction                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_info              | String                | Serialized service details. The type is string.                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_info_obj          | Object                | Service details. The type is object.                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_version           | Integer               | Service version.                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_status            | String                | Release status of an entity. This parameter is read-only and does not need to be set during creation and update.                                |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Options:                                                                                                                                        |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DRAFT: draft                                                                                                                                 |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  PUBLISH_DEVELOPING: to be reviewed                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  PUBLISHED: released                                                                                                                          |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  OFFLINE_DEVELOPING: to be reviewed                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  OFFLINE: offline                                                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  REJECT: rejected                                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | approval_status       | String                | Service approval status. This parameter is read-only.                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Options:                                                                                                                                        |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  DEVELOPING: being reviewed                                                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  APPROVED: approved                                                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  REJECT: rejected                                                                                                                             |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  WITHDREW: approval cancellation                                                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | approval_type         | String                | Service review type.                                                                                                                            |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Options:                                                                                                                                        |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  PUBLISH: released                                                                                                                            |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  OFFLINE: offline                                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | submit_time           | String                | Submitted At                                                                                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by             | String                | Creator.                                                                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | l1                    | String                | Chinese name of the subject area group. This parameter is read-only and does not need to be set when you create or update a subject area group. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | l2                    | String                | Chinese name of the subject area. This parameter is read-only and does not need to be set during creation and update.                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | l3                    | String                | Chinese name of the business object. This parameter is read-only and does not need to be set during creation and update.                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | approval_time         | String                | Review time.                                                                                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | approver              | String                | Reviewer.                                                                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | email                 | String                | Email address of the reviewer.                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | msg                   | String                | Review information.                                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory_path        | String                | Directory tree.                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showcodetablebyid__response_bizversionmanagevo:

.. table:: **Table 7** BizVersionManageVO

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================+
   | id                    | String                | Field ID, which is a string                                                                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_type              | String                | Business entity type.                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  AGGREGATION_LOGIC_TABLE: summary table                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  ATOMIC_INDEX: atomic metric                                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  ATOMIC_METRIC: atomic metric (new)                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  BIZ_CATALOG: process architecture directory                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  BIZ_METRIC: service indicator                                                                                                                                              |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CODE_TABLE: code table                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  COMMON_CONDITION: general filter                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  COMPOSITE_METRIC: Compound Metric (new)                                                                                                                                    |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  COMPOUND_METRIC: compound metric                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CONDITION_GROUP: restriction group                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DEGENERATE_DIMENSION: degenerate dimension                                                                                                                                 |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DERIVATIVE_INDEX: derivative indicator                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DERIVED_METRIC: derivative indicator (new)                                                                                                                                 |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIMENSION: dimension                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIMENSION_ATTRIBUTE: dimension attribute                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIMENSION_HIERARCHIES: dimension level                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIMENSION_LOGIC_TABLE: dimension table                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIMENSION_TABLE_ATTRIBUTE: dimension attribute                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DIRECTORY: directory                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  FACT_ATTRIBUTE: fact table attribute                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  FACT_DIMENSION: fact table dimension                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  FACT_LOGIC_TABLE: fact table                                                                                                                                               |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  FACT_MEASURE: fact table measurement                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  FUNCTION: function                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  INFO_ARCH: information architecture (used for modifying themes in batches)                                                                                                 |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  MODEL: model                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  QUALITY_RULE: quality rule                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SECRECY_LEVEL: security level                                                                                                                                              |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  STANDARD_ELEMENT: data standard                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  STANDARD_ELEMENT_TEMPLATE: data standard template                                                                                                                          |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUBJECT: theme                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  Dimension attributes of SUMMARY_DIMENSION_ATTRIBUTE: summary tables                                                                                                        |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_INDEX: summary table indicator attribute                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_TIME: time period attribute of the SDR table                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TABLE_MODEL: relationship model (logical model/physical model)                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TABLE_MODEL_ATTRIBUTE: relationship model attribute (logical model/physical model)                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TABLE_MODEL_LOGIC: logical entity                                                                                                                                          |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TABLE_TYPE: table type                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TAG: tag                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  TIME_CONDITION: time restriction                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_id                | String                | Business ID, which is a string                                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_info              | String                | Business object information.                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Release status of an entity. This parameter is read-only and does not need to be set during creation and update.                                                              |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  DRAFT: draft                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  PUBLISH_DEVELOPING: to be reviewed                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  PUBLISHED: released                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE_DEVELOPING: to be reviewed                                                                                                                                         |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  REJECT: rejected                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_version           | Integer               | Service version, which is read-only.                                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z.   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showcodetablebyid__response_codetablefieldvo:

.. table:: **Table 8** CodeTableFieldVO

   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | Parameter               | Type                                                                                              | Description                                                      |
   +=========================+===================================================================================================+==================================================================+
   | id                      | String                                                                                            | Lookup table field ID, which is a string                         |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_id           | String                                                                                            | ID of the lookup table (mandatory for update), which is a string |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | ordinal                 | Integer                                                                                           | Sequence number.                                                 |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_en                 | String                                                                                            | Field name, in English.                                          |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | name_ch                 | String                                                                                            | Field name, in Chinese.                                          |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | description             | String                                                                                            | Description.                                                     |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type               | String                                                                                            | Field type                                                       |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | domain_type             | String                                                                                            | Domain to which a field type belongs.                            |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | Options:                                                         |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | -  NUMBER: number                                                |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | -  STRING: character type                                        |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | -  DATETIME: date type                                           |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | -  BLOB: large object (BLOB)                                     |
   |                         |                                                                                                   |                                                                  |
   |                         |                                                                                                   | -  OTHER: other types                                            |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | data_type_extend        | String                                                                                            | Extended field of the data type.                                 |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | is_unique_key           | Boolean                                                                                           | Whether the field is unique.                                     |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | code_table_field_values | Array of :ref:`CodeTableFieldValueVO <showcodetablebyid__response_codetablefieldvaluevo>` objects | Code list attribute value.                                       |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | count_field_values      | Integer                                                                                           | Total number of lookup table attribute values.                   |
   +-------------------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------+

.. _showcodetablebyid__response_codetablefieldvaluevo:

.. table:: **Table 9** CodeTableFieldValueVO

   =========== ======= ===================================================
   Parameter   Type    Description
   =========== ======= ===================================================
   id          String  Lookup table field ID, which is a string
   fd_id       String  Attribute ID of the lookup table, which is a string
   fd_value    String  Code list attribute value.
   ordinal     Integer Sequence number.
   description String  Description.
   =========== ======= ===================================================

**Status code: 400**

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

**Status code: 401**

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

**Status code: 403**

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

**Status code: 404**

.. table:: **Table 13** Response body parameters

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

This API is used to query lookup table information based on the lookup table ID.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/code-tables/1230204979835502592

Example Responses
-----------------

**Status code: 200**

This operation is successful, and the returned data is CodeTableVO details.

.. code-block::

   {
     "data" : {
       "value" : {
         "id" : "1012307352952635392",
         "name_en" : "RY_000001",
         "name_ch" : "Gender",
         "tb_version" : 0,
         "directory_id" : "1012307270173851648",
         "directory_path" : null,
         "description" : "",
         "create_by" : "abc",
         "status" : "PUBLISHED",
         "create_time" : "2022-08-25T10:28:01+08:00",
         "update_time" : "2022-08-25T10:31:08+08:00",
         "approval_info" : null,
         "new_biz" : null,
         "code_table_fields" : [ {
           "id" : "66929",
           "code_table_id" : "1012307352952635392",
           "ordinal" : 1,
           "name_en" : "code",
           "name_ch" : "Message",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
         }, {
           "id" : "66930",
           "code_table_id" : "1012307352952635392",
           "ordinal" : 2,
           "name_en" : "value",
           "name_ch" : "Value",
           "description" : "",
           "data_type" : "STRING",
           "domain_type" : null,
           "data_type_extend" : null,
           "is_unique_key" : false,
           "code_table_field_values" : [ ],
           "count_field_values" : null
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

+-------------+-----------------------------------------------------------------------------+
| Status Code | Description                                                                 |
+=============+=============================================================================+
| 200         | This operation is successful, and the returned data is CodeTableVO details. |
+-------------+-----------------------------------------------------------------------------+
| 400         | BadRequest                                                                  |
+-------------+-----------------------------------------------------------------------------+
| 401         | Unauthorized                                                                |
+-------------+-----------------------------------------------------------------------------+
| 403         | Forbidden                                                                   |
+-------------+-----------------------------------------------------------------------------+
| 404         | Not Found                                                                   |
+-------------+-----------------------------------------------------------------------------+
