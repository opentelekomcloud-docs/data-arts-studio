:original_name: ShowMetricAssets.html

.. _ShowMetricAssets:

Querying Metric Assets
======================

Function
--------

This API is used to query indicator assets.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v3/{project_id}/asset/metric-assets/search

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

   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type    | Description                                                                                                                                                                                                                          |
   +==========================+===========+=========+======================================================================================================================================================================================================================================+
   | architecture_guid        | No        | String  | Indicator asset ID.                                                                                                                                                                                                                  |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query                    | Yes       | String  | Indicates the query condition. If search_name_description is set to true, the query is performed by indicator name or description. If search_name_description is set to false, the query is performed by other indicator attributes. |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                    | No        | Integer | Number of requests at a time.                                                                                                                                                                                                        |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset                   | No        | Integer | Number of bytes to skip before starting to read data.                                                                                                                                                                                |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_name_description  | No        | Boolean | Indicates whether to search by name and description.                                                                                                                                                                                 |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | include_sub_architecture | No        | Boolean | Indicates whether to query sub-counters.                                                                                                                                                                                             |
   +--------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------------------------------+-------------------------------------+
   | Parameter | Type                                                                                   | Description                         |
   +===========+========================================================================================+=====================================+
   | count     | Integer                                                                                | Total number of indicator assets.   |
   +-----------+----------------------------------------------------------------------------------------+-------------------------------------+
   | entities  | Array of :ref:`OpenEntityHeader <showmetricassets__response_openentityheader>` objects | Indicates the indicator asset list. |
   +-----------+----------------------------------------------------------------------------------------+-------------------------------------+
   | scroll_id | String                                                                                 | scroll_Id                           |
   +-----------+----------------------------------------------------------------------------------------+-------------------------------------+

.. _showmetricassets__response_openentityheader:

.. table:: **Table 5** OpenEntityHeader

   +----------------------+--------------------------------------------------------------------------+---------------------+
   | Parameter            | Type                                                                     | Description         |
   +======================+==========================================================================+=====================+
   | attributes           | Object                                                                   | Attribute           |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | connection           | :ref:`Connection <showmetricassets__response_connection>` object         | Data connection.    |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | display_text         | String                                                                   | Displays documents. |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | guid                 | String                                                                   | Asset GUID.         |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | type_name            | String                                                                   | Type name.          |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | tags                 | Array of :ref:`TagHeader <showmetricassets__response_tagheader>` objects | List of tags        |
   +----------------------+--------------------------------------------------------------------------+---------------------+
   | classification_names | Array of strings                                                         | Category name list. |
   +----------------------+--------------------------------------------------------------------------+---------------------+

.. _showmetricassets__response_connection:

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

.. _showmetricassets__response_tagheader:

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

.. code-block::

   {
     "query" : "indicator",
     "search_name_description" : true
   }

Example Responses
-----------------

**Status code: 200**

metric assets.

.. code-block::

   {
     "count" : 1,
     "entities" : [ {
       "attributes" : {
         "owner" : "username",
         "path" : "/process_name_first/process_name_second",
         "create_time" : 1661910746000,
         "qualified_name" : "1014471843710640128.1014471946009714688.1014472726615900160@Business.0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8",
         "name" : "indicator",
         "description" : null,
         "definition" : "Indicator Example",
         "security_level" : null
       },
       "classification_names" : [ ],
       "connection" : null,
       "display_text" : "indicator",
       "guid" : "2fd90dc8-f130-47c2-b6a6-141761c4f9f4",
       "tags" : [ ],
       "type_name" : "BusinessMetric"
     } ],
     "scroll_id" : null
   }

Status Codes
------------

=========== ==============
Status Code Description
=========== ==============
200         metric assets.
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== ==============
