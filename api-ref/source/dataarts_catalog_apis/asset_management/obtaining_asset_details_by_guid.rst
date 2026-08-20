:original_name: ShowEntityInfoByGuid.html

.. _ShowEntityInfoByGuid:

Obtaining Asset Details by GUID
===============================

Function
--------

You can obtain table details based on the table GUID. The table details include the column information. You can also obtain the column information based on the column GUID.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/asset/entities/{guid}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                     |
   +============+===========+========+=================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`.                     |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+
   | guid       | Yes       | String | GUID of the asset. For details about how to obtain the asset GUID, see :ref:`Data Development Job ID <dataartsstudio_02_0351>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type                                                         | Description                                                                                                  |
   +===================+==============================================================+==============================================================================================================+
   | entity            | :ref:`entity <showentityinfobyguid__response_entity>` object | Asset details entity.                                                                                        |
   +-------------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | referred_entities | Object                                                       | Reference entity Map(String, OpenEntity). The key is the asset GUID, and the value is the asset information. |
   +-------------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

.. _showentityinfobyguid__response_entity:

.. table:: **Table 4** entity

   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                                                                         | Description                                                                                                                                     |
   +=========================+==============================================================================+=================================================================================================================================================+
   | attributes              | Object                                                                       | Attribute Map(String, Object). key: attribute name; value: attribute value.                                                                     |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | connection              | :ref:`Connection <showentityinfobyguid__response_connection>` object         | Data connection                                                                                                                                 |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time             | Number                                                                       | Creation time.                                                                                                                                  |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_by              | String                                                                       | Creator                                                                                                                                         |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_text            | String                                                                       | Name of an asset.                                                                                                                               |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | guid                    | String                                                                       | Asset GUID.                                                                                                                                     |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | relationship_attributes | Object                                                                       | Related attribute Map(String, Object). The key field indicates the association name, and the value field indicates the association information. |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | type_name               | String                                                                       | Asset type.                                                                                                                                     |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_by              | String                                                                       | Updater                                                                                                                                         |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time             | Number                                                                       | Update time.                                                                                                                                    |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                    | Array of :ref:`TagHeader <showentityinfobyguid__response_tagheader>` objects | List of tags.                                                                                                                                   |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | classification_names    | Array of strings                                                             | Category name list.                                                                                                                             |
   +-------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showentityinfobyguid__response_connection:

.. table:: **Table 5** Connection

   =============== ====== =====================
   Parameter       Type   Description
   =============== ====== =====================
   guid            String Associated GUID
   display_text    String Displayed content
   type_name       String Type name
   connection_type String Connection type
   qualified_name  String Name of a restriction
   =============== ====== =====================

.. _showentityinfobyguid__response_tagheader:

.. table:: **Table 6** TagHeader

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

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 10** Response body parameters

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

ok.

.. code-block::

   {
     "entity" : {
       "attributes" : {
         "code" : "d96c8f4e-7f59-4313-bed2-b68ef60e31b9",
         "standardClassify" : null,
         "description" : "",
         "rule" : null,
         "type" : "STRING",
         "standardCode" : null,
         "securityLevel" : null,
         "propertyType" : "DIM",
         "alias" : "",
         "definition" : null,
         "workspaceId" : "61aa10df45e54431a1901cb3527adab8",
         "owner" : "",
         "synonyms" : null,
         "length" : 0,
         "updateTime" : 1661908856022,
         "dataMaintainOwner" : null,
         "hasValueList" : false,
         "nameEng" : "name",
         "linkedStandardType" : null,
         "selfDefinedFields" : null,
         "dataMonitorOwner" : null,
         "qualified_name" : "subject_area_group.subject_area.object.dli_table.name@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8",
         "createTime" : 1661908856022,
         "name" : "Name.",
         "ruleOwner" : null,
         "valueExample" : null,
         "valueScope" : null,
         "parameters" : null
       },
       "classification_names" : null,
       "connection" : null,
       "create_time" : 1661908450270,
       "created_by" : "username",
       "display_text" : "Name.",
       "guid" : "d05187d0-adb0-4953-8239-eedb88c21b30",
       "relationship_attributes" : {
         "tableColumn" : {
           "display_text" : null,
           "guid" : "6e02fcf2-7e66-4a32-bded-1d98790a4397",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         },
         "entity" : {
           "display_text" : null,
           "guid" : "a970c4fb-ac97-4339-95e6-944912c58a2b",
           "relationship_attributes" : null,
           "relationship_guid" : null,
           "type_name" : null
         },
         "tags" : [ ]
       },
       "tags" : [ ],
       "type_name" : "BusinessLogicEntityColumn",
       "update_time" : 1661908450270,
       "updated_by" : "username"
     },
     "referred_entities" : { }
   }

Status Codes
------------

=========== =============
Status Code Description
=========== =============
200         ok.
400         Bad Request:
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== =============
