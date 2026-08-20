:original_name: dataartsstudio_01_0809.html

.. _dataartsstudio_01_0809:

Viewing Data Assets
===================

You can search for and filter assets, and view asset details on the **Data Catalog** page.

-  Logical assets include the logical entities and data tables defined and published in DataArts Architecture.
-  Technical assets include the data connections from Management Center, and the databases, tables, and columns obtained by metadata collection tasks in DataArts Catalog.
-  Metric assets come from the business metrics defined and published in DataArts Architecture.

Constraints
-----------

-  Logical assets and metric assets come from DataArts Architecture and are updated if data is synchronized from DataArts Architecture. However, they cannot be deleted directly in DataArts Architecture. Instead, you must locate and delete them in DataArts Catalog.
-  Data connections in technical assets come from Management Center and are updated if data is synchronized from Management Center. However, they cannot be deleted directly in Management Center. Instead, you must locate and delete them in DataArts Catalog.
-  Information such as databases, tables, and columns in technical assets come from metadata collection tasks. Whether to update and automatically delete such information depends on the parameter settings of metadata collection tasks. For details, see :ref:`Configuring a Metadata Collection Task <dataartsstudio_01_0804>`.
-  Data lineages in technical assets are updated by job scheduling. Data lineages are generated based on the latest job instances. To delete data lineages, you need to delete jobs or job metadata. Stopping jobs alone does not delete data lineages.

Searching for a Data Asset
--------------------------

An asset can be searched by its name, description, or attributes. Fuzzy search is supported.

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. In the left navigation pane, choose **Data Map** > **Data Catalog**. Click the **Logical Assets**, **Technical Assets**, and **Metric Assets** tabs as needed.
3. In the search box, enter a keyword to search for your desired assets.

   -  By their names and description
   -  By their attributes, which are displayed on the asset details page

      .. note::

         -  You can save the search criteria you set.
         -  You can import the search criteria you need.

Filtering an Asset
------------------

Technical assets can be filtered by the following criteria:

-  **Data Connections**: the data connection that your target asset uses.

-  **Types**: the type of your target asset.

-  **Tags**: the tags of data assets. The tags were configured in DataArts Catalog. For details, see :ref:`Managing Asset Tags <dataartsstudio_01_0810>`.

-  **Classifications**: the data asset classifications in DataArts Catalog

   In regions where DataArts Security is available:The data map capability is provided by the Data Map module, and the data security and permission capabilities are provided by the DataArts Security module. These capabilities are no longer evolved in the DataArts Catalog module. If DataArts Security and Data Map are available, related capabilities will be unavailable in DataArts Catalog. You cannot create classifications or configure classifications for assets in DataArts Catalog. Instead, you can create classifications or configure classifications for assets through DataArts Security and Data Map. For details, see :ref:`Creating Data Classifications <dataartsstudio_01_1030>`.

-  **Security Levels**: the data asset security levels in DataArts Security

   In regions where DataArts Security is available:The data map capability is provided by the Data Map module, and the data security and permission capabilities are provided by the DataArts Security module. These capabilities are no longer evolved in the DataArts Catalog module. If DataArts Security and Data Map are available, related capabilities will be unavailable in DataArts Catalog. You cannot create security levels or configure security levels for assets in DataArts Catalog. Instead, you can create security levels and configure security levels for assets through DataArts Security and Data Map. For details, see :ref:`Creating Data Security Levels <dataartsstudio_01_1010>`.

The following uses **type** as an example to demonstrate how to filter an asset.

#. Select **Table** under **Types**. Table assets are displayed.
#. In the **Types** area, **Table**, **Column**, **Database**, **Bucket**, and **ColumnFamily** are supported by default. If you select **All**, the system displays assets of all types.

Viewing the Details of an Asset
-------------------------------

This section describes how to view data table details on the **Technical Assets** page.

#. In the list of technical assets, select a table and click its name to access its details page.

#. On the **Details** tab page, view the basic attributes of the technical metadata, add or delete classifications, tags, and security levels for the table, table columns, or OBS objects, and edit the description.

   .. note::

      The sources of tags, classifications, and security levels are as follows:

      -  **Tags**: the tags of data assets. The tags were configured in DataArts Catalog. For details, see :ref:`Managing Asset Tags <dataartsstudio_01_0810>`.

      -  **Classifications**: the data asset classifications in DataArts Catalog

         In regions where DataArts Security is available:The data map capability is provided by the Data Map module, and the data security and permission capabilities are provided by the DataArts Security module. These capabilities are no longer evolved in the DataArts Catalog module. If DataArts Security and Data Map are available, related capabilities will be unavailable in DataArts Catalog. You cannot create classifications or configure classifications for assets in DataArts Catalog. Instead, you can create classifications or configure classifications for assets through DataArts Security and Data Map. For details, see :ref:`Creating Data Classifications <dataartsstudio_01_1030>`.

      -  **Security Levels**: the data asset security levels in DataArts Security

         In regions where DataArts Security is available:The data map capability is provided by the Data Map module, and the data security and permission capabilities are provided by the DataArts Security module. These capabilities are no longer evolved in the DataArts Catalog module. If DataArts Security and Data Map are available, related capabilities will be unavailable in DataArts Catalog. You cannot create security levels or configure security levels for assets in DataArts Catalog. Instead, you can create security levels and configure security levels for assets through DataArts Security and Data Map. For details, see :ref:`Creating Data Security Levels <dataartsstudio_01_1010>`.


   .. figure:: /_static/images/en-us_image_0000002234076640.png
      :alt: **Figure 1** Details tab page

      **Figure 1** Details tab page

#. On the **Permission** tab page, you can apply for data table permissions or grant permissions to other users.


   .. figure:: /_static/images/en-us_image_0000002234236492.png
      :alt: **Figure 2** Permissions tab page

      **Figure 2** Permissions tab page

#. On the **Column Attributes** tab page, view the column attributes of the table; add or delete classifications, tags, and security levels for the data columns; edit the description.


   .. figure:: /_static/images/en-us_image_0000002269195933.png
      :alt: **Figure 3** Managing column attributes

      **Figure 3** Managing column attributes

#. On the **Lineage** tab page, view table lineages and impacts. For details on how to set a data lineage, see :ref:`Viewing Data Lineages Through DataArts Catalog <dataartsstudio_01_0830>`. If a node that supports automatic lineage is configured for a data development job or the lineage of a node is manually configured, the data lineage can be automatically parsed during job execution and displayed in the data catalog.

#. On the **Profile** tab page, view the profile of the data table. (Currently, this function is available only for GaussDB(DWS) and DLI data tables. The profile sampling mode is subject to the :ref:`metadata collection <dataartsstudio_01_0804>` task configuration.)

   Click **Update** to update the table profile.

#. On the **Data Preview** tab page, preview the business data in the current table. The data can be masked in real time based on the column classification information and the configuration in :ref:`Creating a Data Masking Policy (To Be Removed) <dataartsstudio_01_0825>`.

   -  Data assets that use DWS, DLI, MRS Hive, and MySQL data connections can be previewed.
   -  Column classification information can be automatically set when a collection task is created or manually added in the data classification menu. Automatic classification setting is available only for DWS and DLI data collections.

#. On the **Change History** tab page, view the change history of the table.
