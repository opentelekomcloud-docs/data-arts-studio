:original_name: ShowBusinessAssets.html

.. _ShowBusinessAssets:

Querying Logical Assets
=======================

Function
--------

Query business assets, including business objects and logical entities synchronized from data specifications.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/asset/business-assets/search

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

.. table:: **Table 3** Request body parameters

   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type    | Description                                                                                                                                                                                    |
   +=======================+===========+=========+================================================================================================================================================================================================+
   | search_all_attributes | Yes       | Boolean | Indicates whether the keyword query matches all attributes. The value true indicates that all attributes are queried, and the value false indicates that only the name description is queried. |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No        | Object  | List of tags                                                                                                                                                                                   |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                 | Yes       | Integer | Indicates the number of returned records.                                                                                                                                                      |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset                | Yes       | Integer | Query offset.                                                                                                                                                                                  |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | guid                  | No        | String  | Query the guid of the node.                                                                                                                                                                    |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query                 | Yes       | String  | Query keyword. If search_all_attributes is set to true, all attributes are queried. If search_all_attributes is set to false, only the name description is queried.                            |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | Yes       | String  | Query type.                                                                                                                                                                                    |
   +-----------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------------------------+---------------------------------+
   | Parameter | Type                                                                         | Description                     |
   +===========+==============================================================================+=================================+
   | count     | Integer                                                                      | Total number of service assets. |
   +-----------+------------------------------------------------------------------------------+---------------------------------+
   | assets    | Array of :ref:`OpenEntity <showbusinessassets__response_openentity>` objects | List of service assets.         |
   +-----------+------------------------------------------------------------------------------+---------------------------------+

.. _showbusinessassets__response_openentity:

.. table:: **Table 5** OpenEntity

   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                                                                       | Description                                                                                                                                      |
   +=========================+============================================================================+==================================================================================================================================================+
   | attributes              | Object                                                                     | Attribute Map(String, Object). key: attribute name; value: attribute value.                                                                      |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | connection              | :ref:`Connection <showbusinessassets__response_connection>` object         | Data connection                                                                                                                                  |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time             | Number                                                                     | Creation time.                                                                                                                                   |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_by              | String                                                                     | Creator                                                                                                                                          |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_text            | String                                                                     | Name of an asset.                                                                                                                                |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | guid                    | String                                                                     | Asset GUID.                                                                                                                                      |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | relationship_attributes | Object                                                                     | Related attribute Map(String, Object). The key field indicates the relationship type, and the value field indicates the association information. |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | type_name               | String                                                                     | Asset type.                                                                                                                                      |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_by              | String                                                                     | Updater                                                                                                                                          |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time             | Number                                                                     | Update time.                                                                                                                                     |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                    | Array of :ref:`TagHeader <showbusinessassets__response_tagheader>` objects | Tag                                                                                                                                              |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | classification_names    | Array of strings                                                           | Category name list.                                                                                                                              |
   +-------------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showbusinessassets__response_connection:

.. table:: **Table 6** Connection

   =============== ====== =====================
   Parameter       Type   Description
   =============== ====== =====================
   guid            String Associated GUID
   display_text    String Displayed content
   type_name       String Type name
   connection_type String Connection type
   qualified_name  String Name of a restriction
   =============== ====== =====================

.. _showbusinessassets__response_tagheader:

.. table:: **Table 7** TagHeader

   ============= ====== ===========================================
   Parameter     Type   Description
   ============= ====== ===========================================
   name          String Asset name.
   dexcription   Object Tag description.
   display_text  String Tag name.
   relation_guid String Associated GUID.
   tag_guid      String Specifies the GUID associated with the tag.
   ============= ====== ===========================================

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 10** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 11** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

.. code-block::

   {
     "search_all_attributes" : false,
     "limit" : 10,
     "offset" : 0,
     "query" : "dli_table",
     "type" : "LOGICENTITY"
   }

Example Responses
-----------------

**Status code: 200**

Business assets.

.. code-block::

   {
     "assets" : [ {
       "attributes" : {
         "owner" : "",
         "code" : "53f31e71-512a-41d8-81d8-7c49ce68d7b3",
         "description" : "None",
         "updateTime" : 1661908856018,
         "dataClassify" : "BASE_DATA",
         "securityLevel" : null,
         "nameEng" : "dli_table",
         "tables" : [ {
           "uniqueAttributes" : {
             "qualifiedName" : "cbu_training.dli_table@dli.0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8"
           },
           "type_name" : "dli_table_managed",
           "name" : "dli_table",
           "guid" : "d99a8270-63b5-4252-ad37-8cebe7530a73"
         } ],
         "selfDefinedFields" : null,
         "qualified_name" : "subject_area_group.subject_area.object.dli_table@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8",
         "createTime" : 1661908856018,
         "name" : "dli_table",
         "alias" : null,
         "fields" : [ {
           "type_name" : "BusinessLogicEntityColumn",
           "guid" : "d05187d0-adb0-4953-8239-eedb88c21b30"
         }, {
           "type_name" : "BusinessLogicEntityColumn",
           "guid" : "d75821b5-ef73-4650-ac4e-340b255db412"
         }, {
           "type_name" : "BusinessLogicEntityColumn",
           "guid" : "cd7e8939-50f7-4096-b4e4-9f7b73167a97"
         } ],
         "parameters" : null,
         "publishStatus" : null,
         "workspaceId" : "61aa10df45e54431a1901cb3527adab8"
       },
       "classification_names" : null,
       "connection" : null,
       "create_time" : 1661908450270,
       "created_by" : "username",
       "display_text" : "dli_table",
       "guid" : "a970c4fb-ac97-4339-95e6-944912c58a2b",
       "relationship_attributes" : {
         "tables" : [ {
           "display_text" : null,
           "guid" : "d99a8270-63b5-4252-ad37-8cebe7530a73",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         } ],
         "catelog" : {
           "display_text" : null,
           "guid" : "7fbed9da-331d-4695-b8fa-5587605f37e4",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         },
         "fields" : [ {
           "display_text" : null,
           "guid" : "d05187d0-adb0-4953-8239-eedb88c21b30",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         }, {
           "display_text" : null,
           "guid" : "d75821b5-ef73-4650-ac4e-340b255db412",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         }, {
           "display_text" : null,
           "guid" : "cd7e8939-50f7-4096-b4e4-9f7b73167a97",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         } ],
         "tags" : [ ]
       },
       "tags" : null,
       "type_name" : "BusinessLogicEntity",
       "update_time" : 1661908450270,
       "updated_by" : "uaername"
     } ],
     "count" : 1
   }

Status Codes
------------

=========== ================
Status Code Description
=========== ================
200         Business assets.
400         Bad request.
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== ================
