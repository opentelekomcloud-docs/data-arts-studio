:original_name: ShowTechnicalAssetsStatistic.html

.. _ShowTechnicalAssetsStatistic:

Obtaining Technical Asset Statistics
====================================

Function
--------

This API is used to obtain technology asset statistics.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v3/{project_id}/asset/statistic/assets/technical-assets

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                |
   +===========+===========+=========+============================================================================================================+
   | tag       | No        | String  | Tag name of the technical assets                                                                           |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+
   | offset    | No        | Integer | Specifies the query offset. By default, all records are queried. This parameter is a pagination parameter. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+
   | limit     | No        | Integer | Specifies the number of records on each page. By default, all records are queried.                         |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                   | Description                       |
   +=======================+========================================================================================+===================================+
   | count                 | Integer                                                                                | Total number of data connections. |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | datasource_statistics | Array of :ref:`DataSource <showtechnicalassetsstatistic__response_datasource>` objects | Data connection statistics.       |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+

.. _showtechnicalassetsstatistic__response_datasource:

.. table:: **Table 5** DataSource

   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter                 | Type                                                                                 | Description                       |
   +===========================+======================================================================================+===================================+
   | datasource_name           | String                                                                               | Data connection name              |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | datasource_type           | String                                                                               | Data connection type.             |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | datasource_guid           | String                                                                               | GUID of the data connection.      |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | datasource_qualified_name | String                                                                               | Unique ID of a data connection.   |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | obs_folder_count          | Integer                                                                              | Number of OBS directories.        |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | obs_file_count            | Integer                                                                              | Number of OBS files.              |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | css_index_count           | Integer                                                                              | Number of CSS indexes.            |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | css_index_field_count     | Integer                                                                              | Number of CSS index fields.       |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | namespace_count           | Integer                                                                              | Number of namespaces.             |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | ges_vertex_count          | Integer                                                                              | Total number of ges points.       |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | ges_edge_count            | Integer                                                                              | Total number of ges edges.        |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | database_count            | Integer                                                                              | Total number of databases.        |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | stream_count              | Integer                                                                              | Total number of channels.         |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | table_count               | Integer                                                                              | Total number of tables.           |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | data_size                 | Double                                                                               | Data size                         |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | databases                 | Array of :ref:`Database <showtechnicalassetsstatistic__response_database>` objects   | Database statistics.              |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | folders                   | Array of :ref:`ObsFolder <showtechnicalassetsstatistic__response_obsfolder>` objects | Top-level directory statistics.   |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | css_indices               | Array of :ref:`CssIndex <showtechnicalassetsstatistic__response_cssindex>` objects   | CSS index statistics.             |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | namespaces                | Array of :ref:`Namespace <showtechnicalassetsstatistic__response_namespace>` objects | Namespace statistics.             |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | dis_streams               | Array of :ref:`DisStream <showtechnicalassetsstatistic__response_disstream>` objects | Indicates the channel statistics. |
   +---------------------------+--------------------------------------------------------------------------------------+-----------------------------------+

.. _showtechnicalassetsstatistic__response_database:

.. table:: **Table 6** Database

   ======================= ======= =================================
   Parameter               Type    Description
   ======================= ======= =================================
   database_name           String  Database name
   database_guid           String  Database GUID.
   database_qualified_name String  Unique name of the database.
   table_count             Integer Number of tables in the database.
   data_size               Double  Data volume.
   ======================= ======= =================================

.. _showtechnicalassetsstatistic__response_obsfolder:

.. table:: **Table 7** ObsFolder

   ===================== ======= =========================
   Parameter             Type    Description
   ===================== ======= =========================
   folder_name           String  Category name.
   folder_guid           String  GUID of the directory.
   folder_qualified_name String  Unique name of a catalog.
   object_count          Integer Number of objects.
   data_size             Double  Data Volume
   ===================== ======= =========================

.. _showtechnicalassetsstatistic__response_cssindex:

.. table:: **Table 8** CssIndex

   ==================== ======= =======================================
   Parameter            Type    Description
   ==================== ======= =======================================
   index_name           String  Specifies the index name.
   index_guid           String  GUID of an index.
   index_qualified_name String  Unique name of an index.
   index_doc_count      Integer Total number of documents in the index.
   index_data_size      Double  Size of the index data.
   ==================== ======= =======================================

.. _showtechnicalassetsstatistic__response_namespace:

.. table:: **Table 9** Namespace

   +--------------------------+---------+------------------------------------------+
   | Parameter                | Type    | Description                              |
   +==========================+=========+==========================================+
   | namespace_name           | String  | Name of the namespace                    |
   +--------------------------+---------+------------------------------------------+
   | namespace_guid           | String  | GUID of the namespace.                   |
   +--------------------------+---------+------------------------------------------+
   | namespace_qualified_name | String  | Uniquely identifies a namespace.         |
   +--------------------------+---------+------------------------------------------+
   | table_count              | Integer | Total number of tables in the namespace. |
   +--------------------------+---------+------------------------------------------+

.. _showtechnicalassetsstatistic__response_disstream:

.. table:: **Table 10** DisStream

   ===================== ======= =========================
   Parameter             Type    Description
   ===================== ======= =========================
   stream_name           String  Stream name
   stream_guid           String  Channel GUID.
   stream_qualified_name String  Unique name of a channel.
   partition_count       Integer Number of the partitions.
   app_count             Integer Number of DIS apps.
   task_count            Integer Number of dump tasks.
   ===================== ======= =========================

**Status code: 400**

.. table:: **Table 11** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 12** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 13** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 14** Response body parameters

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

Technical assets statistic.

.. code-block::

   {
     "count" : 1,
     "datasource_statistics" : [ {
       "datasource_name" : "dli",
       "datasource_type" : "dli",
       "datasource_guid" : "0fff4057-c206-4dc3-a4ac-73ffc332bc9a",
       "datasource_qualified_name" : "dli@0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8",
       "obs_folder_count" : 0,
       "obs_file_count" : 0,
       "css_index_count" : 0,
       "css_index_field_count" : 0,
       "namespace_count" : 0,
       "ges_vertex_count" : 0,
       "ges_edge_count" : 0,
       "database_count" : 1,
       "stream_count" : 0,
       "table_count" : 1,
       "data_size" : 5478,
       "databases" : [ {
         "data_size" : 5478,
         "database_guid" : "e2b12c35-48ee-441f-a357-e338a85f5d00",
         "database_name" : "cbu_training",
         "database_qualified_name" : "cbu_training@dli.0833a5737480d53b2f25c010dc1a7b88-workspace-61aa10df45e54431a1901cb3527adab8",
         "table_count" : 1
       } ],
       "folders" : null,
       "css_indices" : null,
       "namespaces" : null,
       "dis_streams" : null
     } ]
   }

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         Technical assets statistic.
400         Bad Request:
401         Unauthorized:
403         Forbidden.
404         Not found.
=========== ===========================
