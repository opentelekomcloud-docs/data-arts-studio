:original_name: ResetLinkAttributeAndStandard.html

.. _ResetLinkAttributeAndStandard:

Associated Attributes and Data Standards
========================================

Function
--------

Associate attributes with data standards.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

PUT /v2/{project_id}/design/standards/attribute

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

   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                       |
   +=================+=================+==================+===================================================================+
   | ids             | Yes             | Array of strings | Attribute ID list, which is a string                              |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | stand_row_id    | Yes             | String           | ID of the associated data standard, which is a string             |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | table_id        | Yes             | String           | Table ID, which is a string                                       |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | biz_type        | Yes             | String           | Table type. The default value is TABLE_MODEL.                     |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | Options:                                                          |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  TABLE_MODEL: relationship model (logical model/physical model) |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  AGGREGATION_LOGIC_TABLE: summary table                         |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  FACT_LOGIC_TABLE: fact table                                   |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  DIMENSION: dimension                                           |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  DIMENSION_LOGIC_TABLE: dimension table                         |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                              | Description                                                    |
   +===========+===================================================================+================================================================+
   | data      | :ref:`data <resetlinkattributeandstandard__response_data>` object | data: unified outermost data structure of the returned result. |
   +-----------+-------------------------------------------------------------------+----------------------------------------------------------------+

.. _resetlinkattributeandstandard__response_data:

.. table:: **Table 5** data

   +-----------+-------------------------------------------------------------------------------------------------------------+--------------------+
   | Parameter | Type                                                                                                        | Description        |
   +===========+=============================================================================================================+====================+
   | value     | :ref:`LinkAttributeAndElementVO <resetlinkattributeandstandard__response_linkattributeandelementvo>` object | Attribute ID list. |
   +-----------+-------------------------------------------------------------------------------------------------------------+--------------------+

.. _resetlinkattributeandstandard__response_linkattributeandelementvo:

.. table:: **Table 6** LinkAttributeAndElementVO

   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                       |
   +=======================+=======================+===================================================================+
   | ids                   | Array of strings      | Attribute ID list, which is a string                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | stand_row_id          | String                | ID of the associated data standard, which is a string             |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | table_id              | String                | Table ID, which is a string                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | biz_type              | String                | Table type. The default value is TABLE_MODEL.                     |
   |                       |                       |                                                                   |
   |                       |                       | Options:                                                          |
   |                       |                       |                                                                   |
   |                       |                       | -  TABLE_MODEL: relationship model (logical model/physical model) |
   |                       |                       |                                                                   |
   |                       |                       | -  AGGREGATION_LOGIC_TABLE: summary table                         |
   |                       |                       |                                                                   |
   |                       |                       | -  FACT_LOGIC_TABLE: fact table                                   |
   |                       |                       |                                                                   |
   |                       |                       | -  DIMENSION: dimension                                           |
   |                       |                       |                                                                   |
   |                       |                       | -  DIMENSION_LOGIC_TABLE: dimension table                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------+

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

Associate table attributes with data standards based on request parameters.

.. code-block:: text

   PUT https://{endpoint}/v2/{project_id}/design/standards/attribute

   {
     "ids" : [ "1229920251374923780" ],
     "stand_row_id" : "1169318364674498561",
     "table_id" : "1229920251379118081",
     "biz_type" : "TABLE_MODEL"
   }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "data" : {
       "value" : {
         "ids" : [ "1229920251374923780" ],
         "stand_row_id" : "1169318364674498561",
         "table_id" : "1229920251379118081",
         "biz_type" : "TABLE_MODEL"
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

=========== ============
Status Code Description
=========== ============
200         Success
400         BadRequest
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============
