:original_name: dataartsstudio_01_0010.html

.. _dataartsstudio_01_0010:

Migrating Resources
===================

To migrate resources in one workspace to another, you can use the resource migration function provided by DataArts Studio.

The resources that can be migrated include the data connections created in Management Center.

Prerequisites
-------------

-  Resource import and export depend on the OBS service.
-  There are resources that can be migrated. For details on how to create data connections, see :ref:`Creating Data Connections <dataartsstudio_01_0009>`.

Constraints
-----------

-  Imported and exported resources are stored in JSON format.
-  For security concerns, passwords of connections are not exported when the connections are exported. You need to enter the passwords when importing the connections.

Exporting a Resource
--------------------

#. On the DataArts Studio console, locate a workspace and click **Management Center**.


   .. figure:: /_static/images/en-us_image_0000001373087833.png
      :alt: **Figure 1** Management Center

      **Figure 1** Management Center

#. In the navigation pane, choose **Migrate Resources**.


   .. figure:: /_static/images/en-us_image_0000001321928704.png
      :alt: **Figure 2** Migrating Resources

      **Figure 2** Migrating Resources

#. .. _dataartsstudio_01_0010__li7215285277:

   Click **Create Export Task** to configure the file name and the OBS path for saving the file. If OBS is unavailable, you only need to set the file name.


   .. figure:: /_static/images/en-us_image_0000001322248296.png
      :alt: **Figure 3** Export Task

      **Figure 3** Export Task

#. Click **Next** and select the resource to export.

#. Click **Next** and wait until the export is complete. The resource package is exported to the OBS path set in :ref:`3 <dataartsstudio_01_0010__li7215285277>`. If OBS is unavailable, you can click **Download** in the row of the corresponding migration task to download the exported resource package.


   .. figure:: /_static/images/en-us_image_0000001373408421.png
      :alt: **Figure 4** Export completed

      **Figure 4** Export completed

   If no result is displayed in 1 minute, the export fails. Try again. If the failure persists, contact the customer service or technical support.

Importing a Resource
--------------------

#. On the DataArts Studio console, locate a workspace and click **Management Center**.


   .. figure:: /_static/images/en-us_image_0000001373087833.png
      :alt: **Figure 5** Management Center

      **Figure 5** Management Center

2. In the navigation pane, choose **Migrate Resources**.


   .. figure:: /_static/images/en-us_image_0000001321928704.png
      :alt: **Figure 6** Migrating Resources

      **Figure 6** Migrating Resources

3. Click **Create Import Task** and configure the path for saving the resources to import. If no OBS bucket is available, select the resource package to be uploaded from a local path.


   .. figure:: /_static/images/en-us_image_0000001373169033.png
      :alt: **Figure 7** Configuring the path for saving the resources to import

      **Figure 7** Configuring the path for saving the resources to import

4. Click **Next** and select the resource to import.


   .. figure:: /_static/images/en-us_image_0000001373288737.png
      :alt: **Figure 8** Selecting the resource to import

      **Figure 8** Selecting the resource to import

5. If you select **DataSource**, click **Next** to configure a data connection. The number of data connections required is determined by the number of data sources. Each data connection requires a password.


   .. figure:: /_static/images/en-us_image_0000001322408284.png
      :alt: **Figure 9** Configuring a data connection

      **Figure 9** Configuring a data connection

6. Click **Next** and wait until the import is complete.


   .. figure:: /_static/images/en-us_image_0000001322088392.png
      :alt: **Figure 10** Import completed

      **Figure 10** Import completed

   If no result is displayed in 1 minute, the import fails. Try again. If the failure persists, contact the customer service or technical support.
