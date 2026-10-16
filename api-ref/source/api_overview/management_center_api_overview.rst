:original_name: apiOverview_Manager.html

.. _apiOverview_Manager:

Management Center API Overview
==============================

.. table:: **Table 1** Management Center API types

   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | Type                                                                                          | Description                           |
   +===============================================================================================+=======================================+
   | :ref:`Data Connection Management <apioverview_manager__section_tag_child_840359386458>`       | Data connection management APIs       |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Instance Purchase <apioverview_manager__section_tag_child_714116796186>`                | Instance purchase APIs                |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Workspace Management <apioverview_manager__section_tag_child_507433508448>`             | Workspace management APIs             |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Instance Management <apioverview_manager__section_tag_child_210289059871>`              | Instance management APIs              |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Workspace User Management <apioverview_manager__section_tag_child_459538342122>`        | Workspace user management APIs        |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Data Source Metadata Acquisition <apioverview_manager__section_tag_child_076507308752>` | Data source metadata acquisition APIs |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+
   | :ref:`Instance Specifications Change <apioverview_manager__section_tag_child_507081330218>`   | Instance specifications change APIs   |
   +-----------------------------------------------------------------------------------------------+---------------------------------------+

.. _apioverview_manager__section_tag_child_840359386458:

Data Connection Management
--------------------------

.. table:: **Table 2** Data connection management

   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | API                                                                      | Description                                                     |
   +==========================================================================+=================================================================+
   | :ref:`Querying the Data Connection List <listdataconnections>`           | This API is used to query the data connection list.             |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Creating a Data Connection <createconnections>`                    | This API is used to create a data connection.                   |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Testing a Data Connection <debugdataconnection>`                   | This API is used to test a data connection.                     |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Querying Information About a Data Connection <showdataconnection>` | This API is used to query information about a data connection.  |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Updating a Data Connection <updatedataconnection>`                 | This API is used to update information about a data connection. |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Deleting a Data Connection <deletedataconnection>`                 | This API is used to delete a data connection.                   |
   +--------------------------------------------------------------------------+-----------------------------------------------------------------+

.. _apioverview_manager__section_tag_child_714116796186:

Instance Purchase
-----------------

.. table:: **Table 3** Instance purchase

   +------------------------------------------------------------+-----------------------------------------------------+
   | API                                                        | Description                                         |
   +============================================================+=====================================================+
   | :ref:`Buying a DataArts Studio Instance <payfordgconekey>` | This API is used to buy a DataArts Studio instance. |
   +------------------------------------------------------------+-----------------------------------------------------+

.. _apioverview_manager__section_tag_child_507433508448:

Workspace Management
--------------------

.. table:: **Table 4** Workspace management

   +----------------------------------------------------------------+-----------------------------------------------------------+
   | API                                                            | Description                                               |
   +================================================================+===========================================================+
   | :ref:`Obtaining the Workspace List <listmanagerworkspaces>`    | This API is used to obtain the workspace list.            |
   +----------------------------------------------------------------+-----------------------------------------------------------+
   | :ref:`Creating a Workspace <createmanagerworkspace>`           | This API is used to create a workspace.                   |
   +----------------------------------------------------------------+-----------------------------------------------------------+
   | :ref:`Obtaining Information About a Workspace <showworkspace>` | This API is used to obtain information about a workspace. |
   +----------------------------------------------------------------+-----------------------------------------------------------+

.. _apioverview_manager__section_tag_child_210289059871:

Instance Management
-------------------

.. table:: **Table 5** Instance management

   +------------------------------------------------------------------+-----------------------------------------------+
   | API                                                              | Description                                   |
   +==================================================================+===============================================+
   | :ref:`Obtaining the Instance List <listdataartsstudioinstances>` | This API is used to obtain the instance list. |
   +------------------------------------------------------------------+-----------------------------------------------+

.. _apioverview_manager__section_tag_child_459538342122:

Workspace User Management
-------------------------

.. table:: **Table 6** Workspace user management

   +----------------------------------------------------------------------------+----------------------------------------------------------+
   | API                                                                        | Description                                              |
   +============================================================================+==========================================================+
   | :ref:`Obtaining Workspace User Roles <listworkspaceroles>`                 | This API is used to obtain workspace user roles.         |
   +----------------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Editing a Workspace User or User Group <updateworkspaceuserorgroup>` | This API is used to edit a workspace user or user group. |
   +----------------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Obtaining Workspace User Information <listworkspaceusers>`           | This API is used to obtain workspace user information.   |
   +----------------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Adding a Workspace User <addworkspaceusers>`                         | This API is used to add a workspace user.                |
   +----------------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Deleting a Workspace User <deleteworkspaceusers>`                    | This API is used to delete a user from a workspace.      |
   +----------------------------------------------------------------------------+----------------------------------------------------------+

.. _apioverview_manager__section_tag_child_076507308752:

Data Source Metadata Acquisition
--------------------------------

.. table:: **Table 7** Data source metadata acquisition

   +--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                          | Description                                                                                                                                                                           |
   +==============================================================+=======================================================================================================================================================================================+
   | :ref:`Obtaining the Database List <listdatabases>`           | This API is used to obtain the database list.                                                                                                                                         |
   +--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Schemas <listschemas>`                       | This API is used to obtain schemas. Only GaussDB(DWS) and RDS for PostgreSQL support schemas. Before calling this API, check whether the data source supports the \**schema*\* field. |
   +--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Tables in a Data Source <listdatatables>`    | This API is used to obtain tables in a data source.                                                                                                                                   |
   +--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Table Fields in a Data Source <listcolumns>` | This API is used to obtain table fields in a data source.                                                                                                                             |
   +--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _apioverview_manager__section_tag_child_507081330218:

Instance Specifications Change
------------------------------

.. table:: **Table 8** Instance specifications change

   +-------------------------------------------------+--------------------------------------------+
   | API                                             | Description                                |
   +=================================================+============================================+
   | :ref:`Changing Specifications <changeresource>` | This API is used to change specifications. |
   +-------------------------------------------------+--------------------------------------------+
