:original_name: dataartsstudio_01_1155.html

.. _dataartsstudio_01_1155:

Configuring Workspace Permission Sets
=====================================

In data access permission management, permissions are usually classified into multiple levels of permissions, such as those for level-1, level-2, and level-3 departments. DataArts Security provides a top-down hierarchical mode for data permission management. You can configure the maximum permissions in the workspace through a workspace permission set. Then, you can split the workspace permission set into permission sets for refined permission management.

A workspace permission set contains all the permissions for users in a DataArts Studio workspace. This permission set is created by the DARTS Administrator, Tenant Administrator, or data security administrator. A permission set contains only part of the permissions in a workspace.

Both a workspace permission set and a permission set directly associate users with permissions, but they differ in the following aspects:

-  A workspace permission set is a top-level permission set that has no parent permission set. Generally, you only need to create one workspace permission set for each workspace. However, a permission set must be associated with a parent permission set, which can be a workspace permission set or another permission set. You can create multiple permission sets to associate users with different permissions in different scenarios.
-  A workspace permission set mainly determines the permissions of a workspace, while a permission set is mainly used to manage permissions. A workspace permission set does not require permission synchronization and cannot be associated with roles. A permission set supports permission synchronization, which can be used for permission management, though associating a permission set with roles for permission management is more recommended.

This section describes how to :ref:`create <dataartsstudio_01_1155__en-us_topic_0000001629752664_section131605267507>` and :ref:`configure <dataartsstudio_01_1155__en-us_topic_0000001629752664_section149532211172>` a workspace permission set to define the permissions for a workspace.

Prerequisites
-------------

-  A DWS connection, DLI connection, MRS Hive connection, and MRS Ranger connection have been created in Management Center based on :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.
-  Permissions have been configured for the **dlg_agency** based on :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.
-  User information has been synchronized from IAM to the data source based on :ref:`Synchronizing IAM Users to the Data Source <dataartsstudio_01_1154>`.
-  Metadata of tables has been collected in DataArts Catalog through a :ref:`metadata collection task <dataartsstudio_01_0804>` if you want to view the metadata of databases, tables, and fields in data connections during permission configuration.

Constraints
-----------

-  Only the DARTS Administrator, Tenant Administrator, or security administrator can create, modify, or synchronize workspace permission sets. The permission set administrator can synchronize workspace permission sets. Other common users cannot perform these operations.

-  Workspace permission sets can only be used to define permissions for MRS Hive, DLI, and GaussDB(DWS).

-  After a workspace permission set is configured, permission management does not take effect immediately. Instead, you need to synchronize the workspace permission set to the data source for permission management to take effect.

   Because workspace permission sets are mainly used to determine the permissions of workspaces rather than manage permissions, generally workspace permission sets do not need to be synchronized. You are advised to configure roles based on :ref:`Configuring Roles <dataartsstudio_01_1157>` to manage permissions. If you need to synchronize workspace permission sets, pay attention to the following restrictions:

   -  During authorization, the name of the object to be authorized (database, table, or column name) can contain only digits, letters, underscores (_), hyphens (-), and wildcards (*).

   -  GaussDB(DWS) permission sets are used only to determine the permission scope. Only role permissions can be synchronized. Permissions of user groups and users cannot be synchronized. To make GaussDB(DWS) permissions take effect, you must configure roles. For details, see :ref:`Configuring Roles <dataartsstudio_01_1157>`.

   -  GaussDB(DWS) permission sets can be used to grant permissions of a specified database or schema. The asterisk (*) cannot be used as a wildcard character. Wildcard characters are supported for tables or columns. For example, if you want to grant permissions to all tables in a schema, enter **\*** for the data tables.

   -  If a GaussDB(DWS) permission set is used to grant a user the permissions of all tables in a schema of the GaussDB(DWS) data source (that is, the data tables are set to \*), the user has permissions on all tables in the schema. Due to the restrictions of GaussDB(DWS) permissions, these permissions are applicable only to the current table. This user has no permissions on the tables (future tables) created after permission synchronization. In this case, the administrator must manually synchronize permissions of the role or permission set so that the user has permissions on future tables.

      To avoid manually synchronizing the permissions on future tables, you can configure the users for creating future tables in a specified schema. When these users create future tables in the specified schema, all the users that have full table permissions on the schema in the current instance automatically obtain the permissions on the created future tables.

   -  During DLI permission set synchronization, the custom policies created in IAM are associated with users or user groups. A maximum of 200 custom policies can be created in IAM. Before synchronization, ensure that the quotas are sufficient.

   -  During permission synchronization, you need to configure required permissions for the **dlg_agency**. For details, see :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.

-  The current data permission control uses the allowlist mechanism, which adds operation conditions to the users to be authorized without affecting the permissions the users already have. If you only want to make the permissions granted by the data permission control take effect, you need to revoke the original permissions of the users to be authorized. For details, see :ref:`Data Permission Management <dataartsstudio_01_1151__en-us_topic_0000001678748550_section47668147310>`.

-  Deleted workspace permission sets are moved to the recycle bin. You can restore them within 30 days. After 30 days, they will be deleted permanently. For details, see :ref:`Managing the Recycle Bin <dataartsstudio_01_1183>`.

-  During script execution and job testing in DataArts Factory, the MRS or GaussDB(DWS) data source uses the account of the data connection for authentication by default. Therefore, permission management still does not take effect during data development. You need to enable fine-grained authentication so that the current user is used for authentication during script execution and job testing in DataArts Factory. In this way, different users have different data permissions, and permission management for roles and permission sets takes effect.

.. _dataartsstudio_01_1155__en-us_topic_0000001629752664_section131605267507:

Creating a Workspace Permission Set
-----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Workspace Permission Sets**.

#. On the displayed page, click **Create**.


   .. figure:: /_static/images/en-us_image_0000002269197397.png
      :alt: **Figure 1** Creating a workspace permission set

      **Figure 1** Creating a workspace permission set

#. Configure parameters based on :ref:`Table 1 <dataartsstudio_01_1155__en-us_topic_0000001629752664_table1125141919221>` and click **OK**.

   .. _dataartsstudio_01_1155__en-us_topic_0000001629752664_table1125141919221:

   .. table:: **Table 1** Parameters for creating a workspace permission set

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================+
      | \*Name                            | Permission set name, which is unique in the instance.                                                                                                                                              |
      |                                   |                                                                                                                                                                                                    |
      |                                   | You should include the meaning of the permission set and avoid meaningless descriptions in the name so that the permission set can be quickly identified.                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Administrator                   | Select up to five administrators of the user or user group type.                                                                                                                                   |
      |                                   |                                                                                                                                                                                                    |
      |                                   | The administrators are the owners of the permission set and can configure the permissions in the permission set. The administrators can perform the following operations:                          |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  Permission configuration: Assign data source permissions to the workspace permission set.                                                                                                       |
      |                                   | -  User configuration: Assign permissions in the workspace permission set to users, user groups, or workspace roles.                                                                               |
      |                                   | -  Permission set creation: Create permission sets and roles based on the workspace permission set. The created permission sets do not contain more permissions than the workspace permission set. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Information to make the workspace permission set easier to be identified                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002269197389.png
      :alt: **Figure 2** Creating a workspace permission set

      **Figure 2** Creating a workspace permission set

.. _dataartsstudio_01_1155__en-us_topic_0000001629752664_section149532211172:

Configuring the Workspace Permission Set
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Workspace Permission Sets**.

#. Locate a workspace permission set and click its name to go to the details page.


   .. figure:: /_static/images/en-us_image_0000002234237960.png
      :alt: **Figure 3** Going to the workspace permission set details page

      **Figure 3** Going to the workspace permission set details page

#. In the **Basic Information** area, you can view the name, ID, and administrator of the workspace permission set. For details, see :ref:`Figure 4 <dataartsstudio_01_1155__en-us_topic_0000001629752664_fig495516216713>`.

   .. _dataartsstudio_01_1155__en-us_topic_0000001629752664_fig495516216713:

   .. figure:: /_static/images/en-us_image_0000002234237964.png
      :alt: **Figure 4** Basic information about the workspace permission set

      **Figure 4** Basic information about the workspace permission set

#. On the **Permission Configuration** tab page, **By data** is selected by default. You can select **By permissions**. The configured permissions are the same for **By data** and **By permissions**, and the only difference lies in how the permissions are displayed. You are advised to select **By permissions** for batch authorization.

   -  **By data**: The system allows you to configure permissions for data. Currently, only MRS data sources are supported. The configured permissions will be automatically synchronized.


      .. figure:: /_static/images/en-us_image_0000002269197381.png
         :alt: **Figure 5** Configuring permissions on the By data page

         **Figure 5** Configuring permissions on the By data page

      When configuring permissions, you can select **Entire DB**, **Entire table**, or **Entire column**, and select the corresponding levels in the data source information to perform a batch authorization. You can also click **Authorization** in the **Operation** column of a data record in the expanded navigation pane to authorize access to the data.

      **Fast mode** and **Show data this role has no permission to** are supported. If **Fast mode** is enabled, metadata of databases, tables, and columns is obtained from DataArts Catalog. Otherwise, metadata is obtained from the data source. If metadata has been collected, you are advised to enable **Fast mode**.

      .. note::

         -  Note that the permissions of databases, tables, and columns are managed by layer. For example, a user who has been granted database permissions does not have the permissions of tables and columns. Table and column permissions must be granted separately.

            For example, if you enter a table name or an asterisk (``*``) as a wildcard during database authorization, you are authorizing the table. If you enter a column name or an asterisk (``*``) as a wildcard character, you are authorizing the column.

         -  During authorization, the name of the object to be authorized (database, table, or column name) can contain only digits, letters, underscores (_), hyphens (-), and wildcards (*).


      .. figure:: /_static/images/en-us_image_0000002234237936.png
         :alt: **Figure 6** Authorization on the By data page

         **Figure 6** Authorization on the By data page

   -  **By permissions**: The system allows you to configure permissions.

      To configure permissions, click **Add** and select data levels in sequence. You cannot select multiple objects at the same level (such as database, table, and column) for batch authorization. **Permission Type** cannot be set to **DENY**.

      .. note::

         -  Note that the permissions of databases, tables, and columns are managed by layer. For example, a user who has been granted database permissions does not have the permissions of tables and columns. Table and column permissions must be granted separately.

            For example, if you enter a table name or an asterisk (``*``) as a wildcard during database authorization, you are authorizing the table. If you enter a column name or an asterisk (``*``) as a wildcard character, you are authorizing the column.

         -  During authorization, the name of the object to be authorized (database, table, or column name) can contain only digits, letters, underscores (_), hyphens (-), and wildcards (*).

         -  When you select **HIVE** for **Data Source Type**, you can change **Database** to **URL** to authorize an OBS path in the storage-compute decoupling scenario. In this scenario, the following URL permissions are required for using Hive:

            -  **write**: creating a database
            -  **read**: creating a table, writing data, and deleting a table

         -  When you select **DWS** for **Data Source Type**, you can change **Database** to **Logical Clusters** to authorize logical DWS clusters. The following logical cluster permissions are required:

            -  **create**: allows the creation of tables in sub-clusters.
            -  **usage**: allows access to tables in sub-clusters.
            -  **compute**: allows users with compute permissions to perform elastic computing in sub-clusters.

      After configuring permissions, you can edit, synchronize, or delete them.


      .. figure:: /_static/images/en-us_image_0000002234078128.png
         :alt: **Figure 7** Configuring permissions on the By permissions page

         **Figure 7** Configuring permissions on the By permissions page

#. **User Configuration**: On the permission set details page, click the **User Configuration** tab.

   On this page, you can associate the permissions configured on the **Permission Configuration** page with users. Click **Add** and select **User** or **User group** (**Workspace role** is unavailable currently) to add users to the permission set. You can select users or user groups that have been added to the workspace.


   .. figure:: /_static/images/en-us_image_0000002269117297.png
      :alt: **Figure 8** User Configuration

      **Figure 8** User Configuration

#. **Child Permission Sets**: On the permission set details page, click the **Child Permission Sets** tab.

   On this page, you can view the child permission sets of the current permission set.


   .. figure:: /_static/images/en-us_image_0000002234237948.png
      :alt: **Figure 9** View child permission sets

      **Figure 9** View child permission sets

#. **Log**: On the permission set details page, click the **Log** tab.

   On this page, you can view the log details if permission synchronization fails. The system deletes logs generated 30 days ago at 00:00 every day.


   .. figure:: /_static/images/en-us_image_0000002234237952.png
      :alt: **Figure 10** Viewing logs

      **Figure 10** Viewing logs

#. After the permission set is configured, permission management does not take effect immediately. You need to manually synchronize permissions to the data source for permission management to take effect. For details, see :ref:`Synchronizing Permission Sets <dataartsstudio_01_1155__en-us_topic_0000001629752664_section11218546133410>`.

   Because workspace permission sets are mainly used to determine the permissions of workspaces rather than manage permissions, generally workspace permission sets do not need to be synchronized. You are advised to configure roles based on :ref:`Configuring Roles <dataartsstudio_01_1157>` to manage permissions.

.. _dataartsstudio_01_1155__en-us_topic_0000001629752664_section11218546133410:

Related Operations
------------------

-  Synchronizing workspace permission sets: Workspace permission sets take effect only after they are manually synchronized to the data source. Because workspace permission sets are mainly used to determine the permissions of workspaces rather than manage permissions, generally workspace permission sets do not need to be synchronized. You are advised to configure roles based on :ref:`Configuring Roles <dataartsstudio_01_1157>` to manage permissions.

   To synchronize a workspace permission set, click **Synchronize** in the **Operation** column of the permission set on the **Workspace Permission Sets** page. To synchronize multiple permission sets, select them and click **Synchronize** above the list.

-  Editing a workspace permission set: On the **Workspace Permission Sets** page, click **Edit** in the **Operation** column of a permission set. You can change the name, administrator, and description of the permission set.

-  Deleting workspace permission sets: On the **Workspace Permission Sets** page, click **Delete** in the **Operation** column of a permission set. In the displayed dialog box, confirm the permission set to delete and click **Yes**. To delete multiple permission sets, select them and click **Delete** above the list.

   Workspace permission sets for which permissions, users, or child permission sets have been configured cannot be deleted. To delete such workspace permission sets, delete the configurations first.

   .. note::

      Deleted workspace permission sets are moved to the recycle bin. You can restore them within 30 days. After 30 days, they will be deleted permanently. For details, see :ref:`Managing the Recycle Bin <dataartsstudio_01_1183>`.
