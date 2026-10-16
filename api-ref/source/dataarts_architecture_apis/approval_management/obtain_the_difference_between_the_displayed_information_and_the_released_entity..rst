:original_name: SearchDesignLatestApprovalDiff.html

.. _SearchDesignLatestApprovalDiff:

Obtain the difference between the displayed information and the released entity.
================================================================================

Function
--------

When a released entity is edited, an extension is generated. This API is used to obtain the difference between the extension information and the released entity.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v2/{project_id}/design/approvals/business/{biz_id}/diff

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | biz_id     | Yes       | String | ID of the entity to be compared, which is a string                                                                      |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | biz_type        | Yes             | String          | Entity type to be deleted.                                            |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | Options:                                                              |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  ATOMIC_INDEX: atomic metric                                        |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  DERIVATIVE_INDEX: derivative indicator                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  DIMENSION: dimension                                               |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  FACT_LOGIC_TABLE: fact table                                       |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  TABLE_MODEL: relationship modeling (logical entity/physical table) |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  STANDARD_ELEMENT: data standard                                    |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  AGGREGATION_LOGIC_TABLE: summary table                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  CODE_TABLE: code table                                             |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  BIZ_METRIC: service indicator                                      |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  COMPOUND_METRIC: compound metric                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

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

   +-----------+--------------------------------------------------------------------+--------------------------+
   | Parameter | Type                                                               | Description              |
   +===========+====================================================================+==========================+
   | data      | :ref:`data <searchdesignlatestapprovaldiff__response_data>` object | Data returned by the API |
   +-----------+--------------------------------------------------------------------+--------------------------+

.. _searchdesignlatestapprovaldiff__response_data:

.. table:: **Table 5** data

   +-----------+--------------------------------------------------------------------------------------------+----------------------+
   | Parameter | Type                                                                                       | Description          |
   +===========+============================================================================================+======================+
   | value     | :ref:`PublishVersionVO <searchdesignlatestapprovaldiff__response_publishversionvo>` object | Version information. |
   +-----------+--------------------------------------------------------------------------------------------+----------------------+

.. _searchdesignlatestapprovaldiff__response_publishversionvo:

.. table:: **Table 6** PublishVersionVO

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================+
   | id                    | String                | Version ID, which is a string                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | Version name.                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_tag           | String                | Version flag, which is read-only.                                                                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Version description.                                                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_id                | String                | Business object ID, which is a string                                                                                                                                         |
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
   | biz_info              | String                | Service details. This parameter is read-only.                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_info_vo           | Object                | Business object.                                                                                                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | effect_objs           | String                | Impact information. This parameter is read-only.                                                                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | change_props          | String                | Indicates the change information. This parameter is read-only.                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sql_ddl               | String                | SQL script, which is read-only.                                                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | physical_table        | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dev_physical_table    | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | technical_asset       | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | business_asset        | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | meta_data_link        | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_quality          | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dlf_task              | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | materialization       | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | publish_to_dlm        | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | biz_metric            | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | summary_status        | String                | Synchronization status.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | Options:                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  NO_NEED: not synchronized                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_SUCCESS: The creation is successful.                                                                                                                                |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  CREATE_FAILED: Creation failed                                                                                                                                             |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_SUCCESS: The update is successful.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  UPDATE_FAILED: The update fails.                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_SUCCESS: overall success                                                                                                                                           |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  SUMMARY_FAILED: overall failure                                                                                                                                            |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  RUNNING: overall running                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  OFFLINE: offline                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_current_version    | Boolean               | Indicates whether the version is the current version. This parameter is read-only.                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time, which is read-only. The format complies with RFC3339 and is accurate to seconds. The UTC time zone is yyyy-mm-ddTHH:MM:SSZ, for example, 1970-01-01T00:00:00Z. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_by             | String                | Creator, which is read-only.                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Example Requests
----------------

Obtain the difference between the released entity whose table ID is 1217123755210469376 and the extended information in ER modeling.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/design/approvals/business/1217123755210469376/diff?biz_type=TABLE_MODEL

Example Responses
-----------------

**Status code: 200**

This operation is successful. The returned data is a PublishVersionVO array and the total number of records.

.. code-block::

   {
     "data" : {
       "value" : {
         "id" : "1227929420048830464",
         "version_name" : "test_l2_2_2024-04-11_10-33-07_576",
         "version_tag" : "test_l2_2_2024-04-11_10-33-07_576",
         "description" : null,
         "biz_id" : "1217123755210469376",
         "biz_type" : "TABLE_MODEL",
         "biz_info" : "{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"0833a573fe80d5401f6dc010a775569a\",\"updateBy\":\"0833a573fe80d5401f6dc010a775569a\",\"createTime\":1710226516000,\"updateTime\":1712802684801,\"l3Id\":\"1123655694424358912\",\"l2Id\":\"1123655694424358912\",\"alias\":null,\"encoding\":\"test_l2_2\",\"prefix\":\"test_l2_\",\"codeNum\":null,\"extendInfo\":\"{\\\"columnTag\\\":\\\" \\\",\\\"columnSecrecyLevel\\\":\\\" \\\",\\\"tableTag\\\":\\\" \\\",\\\"dirtyOutSwitch\\\":\\\"true\\\",\\\"dirtyOutDatabase\\\":\\\"default\\\",\\\"dirtyOutPrefix\\\":\\\"err_\\\",\\\"dirtyOutSuffix\\\":\\\"\\\"}\",\"id\":\"1217123755210469376\",\"description\": \"None \",\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"status\":\"DRAFT\",\"tbName\":\"test_l2_2\",\"tbLogicName\":\"test_l2_2\",\"owner\":\"\",\"queueName\":null,\"schema\":null,\"dbName\":null,\"distribute\":null,\"distributeColumn\":null,\"compression\":null,\"obsLocation\":null,\"preCombineField\":null,\"dwId\":\"5013aa3f86df4335945131ce9d242b80\",\"dwName\":\"RDS-Mysql\",\"dwType\":\"MYSQL\",\"physicalTable\":\"CREATE_FAILED\",\"devPhysicalTable\":\"NO_NEED\",\"technicalAsset\":\"CREATE_FAILED\",\"businessAsset\":\"NO_NEED\",\"metaDataLink\":\"UPDATE_FAILED\",\"dataQuality\":\"NO_NEED\",\"dlfTask\":\"NO_NEED\",\"summaryStatus\":\"SUMMARY_FAILED\",\"materialization\":null,\"publishToDlm\":null,\"envType\":\"PROD_TYPE\",\"devVersion\":null,\"prodVersion\":null,\"apiId\":null,\"tbLogicGuid\":\"30a94acc-d5bd-44cf-a751-6fb82989a7c2\",\"tbGuid\":null,\"tbId\":null,\"partitionConf\":null,\"qualityOwner\":null,\"qualityId\":null,\"useRecentlyPartition\":false,\"reversed\":null,\"dirtyOutSwitch\":true,\"dirtyOutDatabase\":\"default\",\"dirtyOutPrefix\":\"err_\",\"dirtyOutSuffix\":\"\",\"dlfTaskId\":null,\"selfDefinedFields\":[{\"fdNameCh\":\"aaa\",\"fdNameEn\":\"aaa\",\"notNull\":false,\"fdValue\":\"\",\"id\":null,\"status\":null,\"fdName\":\"aaa\",\"tenantId\":null,\"nameCh\":null,\"nameEn\":null,\"createBy\":null,\"l3Id\":null}],\"scheduleTime\":null,\"modelId\":\"1217123720355803136\",\"parentTableId\":null,\"parentTableName\":null,\"parentTableCode\":null,\"relatedLogicTableId\":\"1210601123904405504\",\"relatedLogicTableName\":\"test_l2_2\",\"relatedLogicTableModelId\":\"1184439352260976640\",\"relatedLogicTableModelName\":\"wgtest\",\"logicTbName\":\"test_l2_2\",\"logicTbGuid\":\"30a94acc-d5bd-44cf-a751-6fb82989a7c2\",\"logicTbId\":null,\"bizCatalogId\":\"1123655694424358912\",\"bizCatalogGuid\":null,\"catalogPath\":\"{\\\"l1Id\\\":\\\"1088848987810824192\\\",\\\"l2Id\\\":\\\"1123655694424358912\\\",\\\"l3Id\\\":\\\"\\\",\\\"l4Id\\\":\\\"\\\",\\\"l5Id\\\":\\\"\\\",\\\"l6Id\\\":\\\"\\\",\\\"l7Id\\\":\\\"\\\"}\",\"secretType\":\"PUBLIC\",\"tableType\":\"MYSQL_TABLE\",\"dataFormat\":\"Parquet\",\"configs\":\"{}\",\"obsBucket\":null,\"approval\":null,\"tags\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"test_uesr\",\"updateBy\":\"0833a573fe80d5401f6dc010a775569a\",\"createTime\":1712800606000,\"updateTime\":1712801851000,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"1196773541052301312\",\"tagId\":\"1196773541052301312\",\"bizId\":\"1217123755210469376\",\"tagName\":\"aaa\",\"bizType\":\"TABLE_MODEL\",\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"status\":null,\"nameCh\":null,\"nameEn\":null,\"lastL2Id\":null}],\"secrecyLevels\":null,\"attributes\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"0833a573fe80d5401f6dc010a775569a\",\"updateBy\":\"0833a573fe80d5401f6dc010a775569a\",\"createTime\":1710226516000,\"updateTime\":1710849845000,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":\"LP070248\",\"prefix\":\"LP\",\"codeNum\":\"070248\",\"id\":\"1217123755210469377\",\"nameEn\":\"id\",\"nameCh\":\"id\",\"description\":null,\"obsLocation\":null,\"dataType\":\"VARCHAR\",\"isPrimaryKey\":true,\"isPartitionKey\":false,\"isForeignKey\":false,\"extendField\":false,\"ordinal\":1,\"tableModelId\":null,\"relatedLogicAttrId\":\"1210601124399333376\",\"relatedLogicAttrName\":\"id\",\"relatedLogicAttrNameEn\":\"id\",\"standRowId\":null,\"standRowName\":null,\"tags\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"test_uesr\",\"updateBy\":\"test_uesr\",\"createTime\":1712802684000,\"updateTime\":1712802684000,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"112667\",\"tagId\":\"1196773541052301312\",\"bizId\":\"1217123755210469377\",\"tagName\":\"aaa\",\"bizType\":\"TABLE_MODEL\",\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"status\":null,\"nameCh\":null,\"nameEn\":null,\"lastL2Id\":null}],\"secrecyLevels\":null,\"dataTypeExtend\":null,\"domainType\":\"STRING\",\"qualityInfos\":[],\"standElementValues\":null,\"selfDefinedFields\":[],\"notNull\":true,\"code\":\"LP070248\",\"bizCatalogId\":null,\"status\":null,\"tenantId\":null,\"lastL2Id\":null},{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":null,\"updateBy\":null,\"createTime\":1712802684756,\"updateTime\":1712802684756,\"l3Id\":null,\"l2Id\":null,\"alias\":\"\",\"encoding\":\"\",\"prefix\":null,\"codeNum\":null,\"id\":\"0\",\"nameEn\":\"add_column\",\"nameCh\":\"add_column\",\"description\":\"\",\"obsLocation\":null,\"dataType\":\"DOUBLE\",\"isPrimaryKey\":false,\"isPartitionKey\":false,\"isForeignKey\":false,\"extendField\":false,\"ordinal\":2,\"tableModelId\":null,\"relatedLogicAttrId\":null,\"relatedLogicAttrName\":null,\"relatedLogicAttrNameEn\":null,\"standRowId\":null,\"standRowName\":null,\"tags\":[],\"secrecyLevels\":null,\"dataTypeExtend\":\"\",\"domainType\":\"NUMBER\",\"qualityInfos\":null,\"standElementValues\":null,\"selfDefinedFields\":[],\"notNull\":false,\"code\":\"\",\"bizCatalogId\":null,\"status\":null,\"tenantId\":null,\"lastL2Id\":null}],\"relations\": [{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"test_uesr\",\"updateBy\":\"test_uesr\",\"createTime\":1712802684757,\"updateTime\":1712802684757,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"1219738211841208320\",\"name\":\"test_l2_1_test_l2_2_1-wg test \",\"role\":null,\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"sourceTableId\":\"1217123755206275075\",\"sourceTableName\":\"test_l2_1\",\"sourceTableDb\":null,\"targetTableId\":\"1217123755210469376\",\"targetTableName\":\"test_l2_2\",\"targetTableDb\":null,\"sourceType\":\"ONE\",\"targetType\":\"ONE\",\"mappings\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"test_uesr\",\"updateBy\":\"test_uesr\",\"createTime\":1712802684757,\"updateTime\":1712802684757,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"1219738214261321728\",\"relationId\":\"1219738211841208320\",\"sourceFieldId\":\"1217123755206275076\",\"sourceFieldName\":\"id\",\"targetFieldId\":\"1217123755210469377\",\"targetFieldName\":\"id\",\"status\":null,\"tenantId\":null,\"nameCh\":null,\"nameEn\":null,\"lastL2Id\":null}] ,\"status\":null,\"nameCh\":\"test_l2_1_test_l2_2_1-wg test \",\"nameEn\":\"test_l2_1_test_l2_2_1-wg test \",\"lastL2Id\":null}],\"reverseRelations\":[],\"mappings\":null,\"isPartition\":false,\"code\":\"test_l2_2\",\"nameCh\":\"test_l2_2\",\"nameEn\":\"test_l2_2\",\"tagList\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":null,\"updateBy\":null,\"createTime\":1712802787575,\"updateTime\":1712802787575,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"1196773541052301312\",\"name\":\"aaa\",\"tenantId\":null,\"description\":null,\"newBiz\":null,\"status\":null,\"nameCh\":null,\"nameEn\":null,\"lastL2Id\":null}],\"secrecyLevelList\":[],\"lastL2Id\":\"1123655694424358912\"}",
         "biz_info_vo" : {
           "id" : "1217123755210469376",
           "model_id" : "1217123720355803136",
           "parent_table_id" : null,
           "parent_table_name" : null,
           "parent_table_code" : null,
           "related_logic_table_id" : "1210601123904405504",
           "related_logic_table_name" : "test_l2_2",
           "related_logic_table_model_id" : "1184439352260976640",
           "related_logic_table_model_name" : "wgtest",
           "model" : {
             "id" : "1217123720355803136",
             "name" : "mysql",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : true,
             "level" : "SDI",
             "dw_type" : "MYSQL",
             "create_time" : 1710226508,
             "update_time" : 1710991309,
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "type" : "THIRD_NF",
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : ""
           },
           "data_format" : "Parquet",
           "obs_bucket" : null,
           "obs_location" : null,
           "configs" : "{}",
           "table_type" : "MYSQL_TABLE",
           "owner" : "",
           "tb_name" : "test_l2_2",
           "dw_id" : "5013aa3f86df4335945131ce9d242b80",
           "db_name" : null,
           "queue_name" : null,
           "schema" : null,
           "extend_info" : "{\"columnTag\":\" \",\"columnSecrecyLevel\":\" \",\"tableTag\":\" \",\"dirtyOutSwitch\":\"true\",\"dirtyOutDatabase\":\"default\",\"dirtyOutPrefix\":\"err_\",\"dirtyOutSuffix\":\"\"}",
           "tb_guid" : null,
           "tb_id" : null,
           "logic_tb_name" : "test_l2_2",
           "logic_tb_guid" : "30a94acc-d5bd-44cf-a751-6fb82989a7c2",
           "description" : "None",
           "status" : "DRAFT",
           "logic_tb_id" : null,
           "biz_catalog_id" : "1123655694424358912",
           "catalog_path" : "l52/test_l2_3",
           "create_by" : "test_uesr",
           "update_by" : "test_uesr",
           "create_time" : 1710226516,
           "update_time" : 1.712802684801E9,
           "tags" : [ {
             "id" : "1196773541052301312",
             "tag_id" : "1196773541052301312",
             "tag_name" : "aaa",
             "biz_id" : "1217123755210469376",
             "biz_type" : "TABLE_MODEL",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "create_time" : 1712800606,
             "update_time" : 1712801851
           } ],
           "attributes" : [ {
             "id" : "1217123755210469377",
             "name_en" : "id",
             "name_ch" : "id",
             "description" : null,
             "obs_location" : null,
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "data_type" : "VARCHAR",
             "domain_type" : "STRING",
             "data_type_extend" : null,
             "is_primary_key" : true,
             "is_partition_key" : false,
             "is_foreign_key" : false,
             "extend_field" : false,
             "not_null" : true,
             "ordinal" : 1,
             "table_model_id" : null,
             "create_time" : 1710226516,
             "update_time" : 1710849845,
             "tags" : [ {
               "id" : "112667",
               "tag_id" : "1196773541052301312",
               "tag_name" : "aaa",
               "biz_id" : "1217123755210469377",
               "biz_type" : "TABLE_MODEL",
               "create_by" : "test_uesr",
               "update_by" : "test_uesr",
               "create_time" : 1712802684,
               "update_time" : 1712802684
             } ],
             "secrecy_levels" : null,
             "stand_row_id" : null,
             "stand_row_name" : null,
             "quality_infos" : [ ],
             "alias" : null,
             "self_defined_fields" : [ ],
             "code" : "LP070248",
             "related_logic_attr_id" : "1210601124399333376",
             "related_logic_attr_name" : "id",
             "related_logic_attr_name_en" : "id"
           }, {
             "id" : "0",
             "name_en" : "add_column",
             "name_ch" : "add_column",
             "description" : "",
             "obs_location" : null,
             "create_by" : null,
             "update_by" : null,
             "data_type" : "DOUBLE",
             "domain_type" : "NUMBER",
             "data_type_extend" : "",
             "is_primary_key" : false,
             "is_partition_key" : false,
             "is_foreign_key" : false,
             "extend_field" : false,
             "not_null" : false,
             "ordinal" : 2,
             "table_model_id" : null,
             "create_time" : 1.712802684756E9,
             "update_time" : 1.712802684756E9,
             "tags" : [ ],
             "secrecy_levels" : null,
             "stand_row_id" : null,
             "stand_row_name" : null,
             "quality_infos" : null,
             "alias" : "",
             "self_defined_fields" : [ ],
             "code" : "",
             "related_logic_attr_id" : null,
             "related_logic_attr_name" : null,
             "related_logic_attr_name_en" : null
           } ],
           "mappings" : null,
           "relations" : [ {
             "id" : "1219738211841208320",
             "source_table_id" : "1217123755206275075",
             "target_table_id" : "1217123755210469376",
             "name" : "test_l2_1_test_l2_2_1-wg test",
             "source_table_name" : "test_l2_1",
             "target_table_name" : "test_l2_2",
             "role" : null,
             "tenant_id" : "0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70",
             "source_type" : "ONE",
             "target_type" : "ONE",
             "create_by" : "test_uesr",
             "update_by" : "test_uesr",
             "create_time" : 1.712802684757E9,
             "update_time" : 1.712802684757E9,
             "mappings" : [ {
               "id" : "1219738214261321728",
               "relation_id" : "1219738211841208320",
               "source_field_id" : "1217123755206275076",
               "target_field_id" : "1217123755210469377",
               "source_field_name" : "id",
               "target_field_name" : "id",
               "create_by" : "test_uesr",
               "update_by" : "test_uesr",
               "create_time" : 1.712802684757E9,
               "update_time" : 1.712802684757E9
             } ]
           } ],
           "dw_type" : "MYSQL",
           "dw_name" : "RDS-Mysql",
           "l1" : "l52",
           "l2" : "test_l2_3",
           "l3" : null,
           "l1_id" : "1088848987810824192",
           "l2_id" : "1123655694424358912",
           "l3_id" : null,
           "partition_conf" : null,
           "dlf_task_id" : null,
           "use_recently_partition" : false,
           "reversed" : null,
           "dirty_out_switch" : true,
           "dirty_out_database" : "default",
           "dirty_out_prefix" : "err_",
           "dirty_out_suffix" : "",
           "quality_owner" : null,
           "quality_id" : null,
           "distribute" : null,
           "distribute_column" : null,
           "compression" : null,
           "pre_combine_field" : null,
           "is_partition" : false,
           "physical_table" : "CREATE_FAILED",
           "dev_physical_table" : "NO_NEED",
           "technical_asset" : "CREATE_FAILED",
           "business_asset" : "NO_NEED",
           "meta_data_link" : "UPDATE_FAILED",
           "data_quality" : "NO_NEED",
           "summary_status" : "SUMMARY_FAILED",
           "dev_version" : null,
           "prod_version" : null,
           "dev_version_name" : null,
           "prod_version_name" : null,
           "env_type" : "PROD_TYPE",
           "alias" : null,
           "self_defined_fields" : [ {
             "fd_name_ch" : "aaa",
             "fd_name_en" : "aaa",
             "not_null" : false,
             "fd_value" : ""
           } ],
           "code" : "test_l2_2",
           "has_related_physical_table" : false,
           "has_related_logic_table" : false
         },
         "effect_objs" : null,
         "change_props" : "Basic information:\nData format: CCParquet@CC\n\n\n\nTable fields:\n\nadd_column: English name: CCadd_column@CC name: CCadd_column@CC data type: CCDOUBLE@CC primary key: CCfalse@CC partition: CCfalse@CC foreign key: CCfalse@CC sequence number: CC2@CC data type extension: CC@CC is not empty: CCfalse@CC code: CC@CC.\n\nRelationship:\n\ntest_l2_1_test_l2_2_1-wg test: Name: CCtest_l2_1_test_l2_2_1-wg test@CC child table: CCtest_l2_1@CC parent table: CCtest_l2_2@CC child pair: CCONE@CC parent pair: CCONE@CC\nField mapping:\nChild table field: CCid@CC Parent table field: CCid@CC",
         "sql_ddl" : "ALTER TABLE ${database}.test_l2_2 ADD add_column DOUBLE;",
         "physical_table" : null,
         "technical_asset" : null,
         "business_asset" : null,
         "meta_data_link" : null,
         "data_quality" : null,
         "dlf_task" : null,
         "materialization" : null,
         "publish_to_dlm" : null,
         "biz_metric" : null,
         "summary_status" : null,
         "is_current_version" : false,
         "create_time" : "2024-04-11T10:33:07.565+08:00",
         "create_by" : "test_uesr"
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

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                  |
+=============+==============================================================================================================+
| 200         | This operation is successful. The returned data is a PublishVersionVO array and the total number of records. |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 400         | BadRequest                                                                                                   |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized                                                                                                 |
+-------------+--------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden                                                                                                    |
+-------------+--------------------------------------------------------------------------------------------------------------+
