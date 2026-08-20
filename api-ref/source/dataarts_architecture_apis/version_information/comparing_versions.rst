:original_name: CompareDesignVersions.html

.. _CompareDesignVersions:

Comparing Versions
==================

Function
--------

This API is used to compare two versions with different IDs.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v1/{project_id}/design/versions/compare

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+------------------+----------------------------------------+
   | Parameter | Mandatory | Type             | Description                            |
   +===========+===========+==================+========================================+
   | ids       | Yes       | Array of strings | Array of entity IDs, which is a string |
   +-----------+-----------+------------------+----------------------------------------+

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

   +-----------+-----------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter | Type                                                      | Description                                                            |
   +===========+===========================================================+========================================================================+
   | data      | :ref:`data <comparedesignversions__response_data>` object | Data, which is the unified outer data structure of the returned result |
   +-----------+-----------------------------------------------------------+------------------------------------------------------------------------+

.. _comparedesignversions__response_data:

.. table:: **Table 5** data

   +-----------+-----------------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                              | Description           |
   +===========+===================================================================================+=======================+
   | value     | :ref:`PublishVersionVO <comparedesignversions__response_publishversionvo>` object | CatalogVO information |
   +-----------+-----------------------------------------------------------------------------------+-----------------------+

.. _comparedesignversions__response_publishversionvo:

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

Compare version 1295786824106741760 with 1301676931971940352.

.. code-block:: text

   POST https://{endpoint}/v1/{project_id}/design/versions/compare?ids=1295786824106741760&&ids=1301676931971940352

   { }

Example Responses
-----------------

**Status code: 200**

The operation succeeds. **PublishVersionVO** is returned.

.. code-block::

   {
     "data" : {
       "value" : {
         "id" : "1301676931971940352",
         "version_name" : "pd_test_2024-10-31_22-39-24_572",
         "version_tag" : "pd_test_2024-10-31_22-39-24_572",
         "description" : null,
         "biz_id" : "1295696904545603584",
         "biz_type" : "TABLE_MODEL",
         "biz_info" : "{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"0833a573fe80d5401f6dc010a775569a\",\"updateBy\":\"0833a573fe80d5401f6dc010a775569a\",\"createTime\":1728959815000,\"updateTime\":1730385564000,\"l3Id\":\"1089989054919065600\",\"l2Id\":null,\"alias\":null,\"encoding\":\"LE003444\",\"prefix\":\"LE\",\"codeNum\":null,\"extendInfo\":\"{\\\"dirtyOutDatabase\\\":\\\"\\\",\\\"dirtyOutPrefix\\\":\\\"\\\",\\\"dirtyOutSuffix\\\":\\\"\\\",\\\"dirtyOutSwitch\\\":\\\"false\\\"}\",\"id\":\"1295696904545603584\",\"description\": \"None \",\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"status\":\"PUBLISHED\",\"tbName\":\"pd_test\",\"tbLogicName\":\"pd_test\",\"owner\":\"\",\"queueName\":\"default\",\"schema\":null,\"dbName\":\"bi\",\"distribute\":null,\"distributeColumn\":null,\"compression\":null,\"obsLocation\":null,\"preCombineField\":null,\"dwId\":\"8259af52bd294f98920ebce75a426391\",\"dwName\":null,\"dwType\":\"DWS\",\"physicalTable\":\"UPDATE_SUCCESS\",\"devPhysicalTable\":\"NO_NEED\",\"technicalAsset\":\"NO_NEED\",\"businessAsset\":\"NO_NEED\",\"metaDataLink\":\"NO_NEED\",\"dataQuality\":\"UPDATE_FAILED\",\"dlfTask\":\"NO_NEED\",\"summaryStatus\":\"SUMMARY_FAILED\",\"materialization\":null,\"publishToDlm\":null,\"envType\":\"PROD_TYPE\",\"devVersion\":null,\"prodVersion\":\"1299388171930447872\",\"apiId\":null,\"tbLogicGuid\":\"33c30a2c-5f23-4bb5-a9c5-c1c0c8a7d609\",\"tbGuid\":null,\"tbId\":\"NativeTable-8259af52bd294f98920ebce75a426391-pd_test\",\"partitionConf\":null,\"qualityOwner\":null,\"qualityId\":\"1295789728175833089\",\"qualityIdExtend\":null,\"useRecentlyPartition\":false,\"reversed\":null,\"dirtyOutSwitch\":false,\"dirtyOutDatabase\":\"\",\"dirtyOutPrefix\":\"\",\"dirtyOutSuffix\":\"\",\"dlfTaskId\":null,\"modelId\":\"1295338804126908416\",\"model\":null,\"selfDefinedFields\":null,\"scheduleTime\":null,\"parentTableId\":null,\"parentTableName\":null,\"parentTableCode\":null,\"relatedLogicTableId\":\"1230888997367193600\",\"relatedLogicTableName\":\"pd_test\",\"relatedLogicTableModelId\":\"1148908032844009472\",\"relatedLogicTableModelName\":\"test_import\",\"logicTbName\":\"pd_test\",\"logicTbGuid\":\"33c30a2c-5f23-4bb5-a9c5-c1c0c8a7d609\",\"logicTbId\":null,\"bizCatalogId\":\"1089989054919065600\",\"bizCatalogGuid\":null,\"catalogPath\":null,\"secretType\":\"PUBLIC\",\"tableType\":\"MANAGED\",\"dataFormat\":\"Parquet\",\"configs\":\"{}\",\"obsBucket\":null,\"approval\":null,\"sourceType\":0,\"tags\":[],\"secrecyLevels\":null,\"attributes\": [{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"0833a573fe80d5401f6dc010a775569a\",\"updateBy\":\"0833a573fe80d5401f6dc010a775569a\",\"createTime\":1728959815000,\"updateTime\":1730385565000,\"l3Id\":null,\"l2Id\":null,\"alias\":\"\",\"encoding\":\"LP070256\",\"prefix\":\"LP\",\"codeNum\":null,\"id\":\"1295696904545603585\",\"nameEn\":\"id\",\"nameCh\":\"id\",\"description\":\"\",\"obsLocation\":null,\"dataType\":\"STRING\",\"isPrimaryKey\":true,\"isPartitionKey\":false,\"isForeignKey\":false,\"extendField\":false,\"ordinal\":1,\"tableModelId\":null,\"relatedLogicAttrId\":\"1230888997920841728\",\"relatedLogicAttrName\":\"id\",\"relatedLogicAttrNameEn\":\"id\",\"standRowId\":\"1294696939622932481\",\"standRowName\":\"1.1, avavvqav,\"\"tags\":[] ,\"secrecyLevels\":[{\"versionName\":null,\"versionTag\":null,\"versionId\":null,\"createBy\":\"username1\",\"updateBy\":\"username1\",\"createTime\":1730385564000,\"updateTime\":1730385564000,\"l3Id\":null,\"l2Id\":null,\"alias\":null,\"encoding\":null,\"prefix\":null,\"codeNum\":null,\"id\":\"20356\",\"secrecyLevelId\":\"1140704811168288768\",\"bizId\":\"1295696904545603585\",\"secrecyLevelName\":\"zcy_admin_10\",\"uuid\":\"\",\"slevel\":0,\"description\":null,\"bizType\":\"TABLE_MODEL\",\"tenantId\":\"0833a5737480d53b2f25c010dc1a7b88-workspace-eeb055e69c624311b6b9cfee89a4ec70\",\"nameEn\":null,\"nameCh\":null,\"status\":null,\"lastL2Id\":null}],\"dataTypeExtend\":\"\",\"domainType\":\"STRING\",\"qualityInfos\":[],\"standElementValues\":null,\"selfDefinedFields\": [{\"fdNameCh\":\"Privacy level \",\"fdNameEn\":\"SecretLevel\",\"notNull\":false,\"fdValue\":\"aa\",\"fdName\": \"Privacy level \",\"tenantId\":null,\"nameEn\":null,\"nameCh\":null,\"createBy\":null,\"l3Id\":null,\"id\":null,\"status\":null},{\"fdNameCh\": \"Synonym \",\"fdNameEn\":\"sameWord\",\"notNull\":false,\"fdValue\":\"bb\",\"fdName\": \"Synonym \",\"tenantId\":null,\"nameEn\":null,\"nameCh\":null,\"createBy\":null,\"l3Id\":null,\"id\":null,\"status\":null}] ,\"notNull\":true,\"code\":\"LP070256\",\"bizCatalogId\":null,\"tenantId\":null,\"primaryKey\":true,\"partitionKey\":false,\"status\":null,\"lastL2Id\":null}],\"relations\":[],\"reverseRelations\":[],\"mappings\":null,\"isPartition\":false,\"code\":\"LE003444\",\"nameEn\":\"pd_test\",\"nameCh\":\"pd_test\",\"tagList\":[],\"secrecyLevelList\":[],\"lastL2Id\":null}",
         "biz_info_vo" : {
           "id" : "1295696904545603584",
           "model_id" : "1295338804126908416",
           "parent_table_id" : null,
           "parent_table_name" : null,
           "parent_table_code" : null,
           "related_logic_table_id" : "1230888997367193600",
           "related_logic_table_name" : "pd_test",
           "related_logic_table_model_id" : "1148908032844009472",
           "related_logic_table_model_name" : "test_import",
           "model" : {
             "id" : "1295338804126908416",
             "name" : "model_test",
             "description" : "",
             "is_physical" : true,
             "frequent" : false,
             "top" : true,
             "dw_type" : null,
             "create_time" : 1.728874437E9,
             "update_time" : 1.728874437E9,
             "create_by" : "username1",
             "update_by" : "username1",
             "type" : "THIRD_NF",
             "layer_id" : "1255490378069700608",
             "layer" : {
               "id" : "1255490378069700608",
               "level" : 1,
               "name" : "ODS",
               "type" : "THIRD_NF",
               "description" : null,
               "is_default" : true,
               "disabled_customized_field_ids" : [ "1254806436282773504" ]
             },
             "level" : null,
             "biz_catalog_ids" : null,
             "databases" : null,
             "table_model_prefix" : "",
             "dimension_prefix" : null,
             "is_default" : false,
             "has_permissions" : null
           },
           "data_format" : "Parquet",
           "obs_bucket" : null,
           "obs_location" : null,
           "configs" : "{}",
           "table_type" : "MANAGED",
           "owner" : "",
           "tb_name" : "pd_test",
           "dw_id" : "8259af52bd294f98920ebce75a426391",
           "db_name" : "bi",
           "queue_name" : "default",
           "schema" : null,
           "extend_info" : "{\"dirtyOutDatabase\":\"\",\"dirtyOutPrefix\":\"\",\"dirtyOutSuffix\":\"\",\"dirtyOutSwitch\":\"false\"}",
           "tb_guid" : null,
           "tb_id" : "NativeTable-8259af52bd294f98920ebce75a426391-pd_test",
           "logic_tb_name" : "pd_test",
           "logic_tb_guid" : "33c30a2c-5f23-4bb5-a9c5-c1c0c8a7d609",
           "description" : "None",
           "status" : "PUBLISHED",
           "logic_tb_id" : null,
           "biz_catalog_id" : "1089989054919065600",
           "catalog_path" : "lxy4/lxy_3",
           "create_by" : "username1",
           "update_by" : "username1",
           "create_time" : 1.728959815E9,
           "update_time" : 1.730385564E9,
           "tags" : [ ],
           "attributes" : [ {
             "id" : "1295696904545603585",
             "name_en" : "id",
             "name_ch" : "id",
             "description" : "",
             "obs_location" : null,
             "create_by" : "username1",
             "update_by" : "username1",
             "data_type" : "STRING",
             "domain_type" : "STRING",
             "data_type_extend" : "",
             "is_primary_key" : true,
             "is_partition_key" : false,
             "is_foreign_key" : false,
             "extend_field" : false,
             "not_null" : true,
             "ordinal" : 1,
             "table_model_id" : null,
             "create_time" : 1.728959815E9,
             "update_time" : 1.730385565E9,
             "tags" : [ ],
             "secrecy_levels" : [ {
               "id" : "20356",
               "secrecyLevel_id" : "1140704811168288768",
               "secrecyLevel_name" : "zcy_admin_10",
               "uuid" : "",
               "slevel" : 0,
               "description" : null,
               "biz_id" : "1295696904545603585",
               "biz_type" : "TABLE_MODEL",
               "create_by" : "username1",
               "update_by" : "username1",
               "create_time" : 1.730385564E9,
               "update_time" : 1.730385564E9
             } ],
             "stand_row_id" : "1294696939622932481",
             "stand_row_name" : "1.1, avavvqav",
             "quality_infos" : [ ],
             "alias" : "",
             "self_defined_fields" : [ {
               "fd_name_ch" : "Privacy level",
               "fd_name_en" : "SecretLevel",
               "not_null" : false,
               "fd_value" : "aa"
             }, {
               "fd_name_ch" : "Synonym",
               "fd_name_en" : "sameWord",
               "not_null" : false,
               "fd_value" : "bb"
             } ],
             "code" : "LP070256",
             "related_logic_attr_id" : "1230888997920841728",
             "related_logic_attr_name" : "id",
             "related_logic_attr_name_en" : "id"
           } ],
           "mappings" : null,
           "relations" : [ ],
           "dw_type" : "DWS",
           "dw_name" : "dws",
           "l1" : "lxy4",
           "l2" : "lxy_3",
           "l3" : null,
           "l1_id" : "1088851391579066368",
           "l2_id" : "1089989054919065600",
           "l3_id" : null,
           "partition_conf" : null,
           "dlf_task_id" : null,
           "use_recently_partition" : false,
           "reversed" : null,
           "dirty_out_switch" : false,
           "dirty_out_database" : "",
           "dirty_out_prefix" : "",
           "dirty_out_suffix" : "",
           "quality_owner" : null,
           "quality_id" : "1295789728175833089",
           "quality_id_extend" : null,
           "distribute" : null,
           "distribute_column" : null,
           "compression" : null,
           "pre_combine_field" : null,
           "is_partition" : false,
           "physical_table" : "UPDATE_SUCCESS",
           "dev_physical_table" : "NO_NEED",
           "technical_asset" : "NO_NEED",
           "business_asset" : "NO_NEED",
           "meta_data_link" : "NO_NEED",
           "data_quality" : "UPDATE_FAILED",
           "summary_status" : "SUMMARY_FAILED",
           "dev_version" : null,
           "prod_version" : "1299388171930447872",
           "dev_version_name" : null,
           "prod_version_name" : null,
           "env_type" : "PROD_TYPE",
           "alias" : null,
           "self_defined_fields" : null,
           "code" : "LE003444",
           "has_related_physical_table" : false,
           "has_related_logic_table" : false
         },
         "effect_objs" : null,
         "change_props" : "Basic information:\nQueue: CCdefault@CC\nDatabase: CCbi@CC\n\n\n\nTable field:\n\nid: Data standard: CC1.1, avavvqav@CC",
         "sql_ddl" : null,
         "physical_table" : "UPDATE_SUCCESS",
         "technical_asset" : "CREATE_SUCCESS",
         "business_asset" : "NO_NEED",
         "meta_data_link" : "UPDATE_SUCCESS",
         "data_quality" : "UPDATE_FAILED",
         "dlf_task" : "NO_NEED",
         "materialization" : null,
         "publish_to_dlm" : null,
         "biz_metric" : "NO_NEED",
         "summary_status" : "SUMMARY_FAILED",
         "is_current_version" : false,
         "create_time" : "2024-10-31T22:39:25+08:00",
         "create_by" : "username1"
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

=========== =========================================================
Status Code Description
=========== =========================================================
200         The operation succeeds. **PublishVersionVO** is returned.
400         BadRequest
401         Unauthorized
403         Forbidden
=========== =========================================================
