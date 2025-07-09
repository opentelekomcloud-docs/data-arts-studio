:original_name: dataartsstudio_01_0010.html

.. _dataartsstudio_01_0010:

Migrating Resources
===================

To migrate resources in one workspace to another, you can use the resource migration function provided by DataArts Studio.

Resources that can be migrated include the data connections in Management Center.

Prerequisites
-------------

-  Resources can be imported from OBS or a local path.
-  There are resources that can be migrated. For details on how to create data connections, see :ref:`Managing Data Connections <dataartsstudio_01_0009>`.

Constraints
-----------

-  Only an exported .zip file can be imported. During the import, the system verifies the resources in the file.
-  For security concerns, passwords of connections are not exported when the connections are exported. You need to enter the passwords when importing the connections.
-  The size of the file to be imported from an OBS bucket or local path cannot exceed 10 MB.

Exporting a Resource
--------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. In the navigation pane, choose **Migrate Resources**.


   .. figure:: /_static/images/en-us_image_0000002305439969.png
      :alt: **Figure 1** Migrating Resources

      **Figure 1** Migrating Resources

#. Click **Create Export Task** to configure the file name and the OBS path for saving the file. If OBS is unavailable, you only need to set the file name.


   .. figure:: /_static/images/en-us_image_0000002305406933.png
      :alt: **Figure 2** Export Task

      **Figure 2** Export Task

#. Click **Next** and select the resources to export.

#. Click **Next** and wait until the export is complete. The resource package is exported to the OBS path you have set.


   .. figure:: /_static/images/en-us_image_0000002305406921.png
      :alt: **Figure 3** Export completed

      **Figure 3** Export completed

   If no result is displayed in 1 minute, the export fails. Try again. If the failure persists, contact the customer service or technical support.

#. After the export is complete, you can click **Download** in the row of the corresponding migration task to download the exported resource package.


   .. figure:: /_static/images/en-us_image_0000002305406917.png
      :alt: **Figure 4** Downloading the exported result

      **Figure 4** Downloading the exported result

Importing a Resource
--------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. In the navigation pane, choose **Migrate Resources**.


   .. figure:: /_static/images/en-us_image_0000002305439969.png
      :alt: **Figure 5** Migrating Resources

      **Figure 5** Migrating Resources

#. Click **Create Import Task**. On the displayed page, select an import mode and set the OBS bucket and path or local path that stores resources. The resource to be imported must be a .zip file exported from the console.


   .. figure:: /_static/images/en-us_image_0000002270847054.png
      :alt: **Figure 6** Configuring the path that stores the resources to be imported

      **Figure 6** Configuring the path that stores the resources to be imported

#. Click **Create Import Task** and upload a .zip resource file that you have exported.

#. Click **Next** and select the resources to import.

#. If you select **DataSource**, click **Next** to configure a data connection.


   .. figure:: /_static/images/en-us_image_0000002305406925.png
      :alt: **Figure 7** Configuring a data connection

      **Figure 7** Configuring a data connection

#. Click **Next** and wait until the import task is delivered. When the import task is delivered successfully, the system displays message "Import task started."


   .. figure:: /_static/images/en-us_image_0000002305439965.png
      :alt: **Figure 8** Import task started

      **Figure 8** Import task started

#. Click **OK**. You can view the import result in the resource migration task list.

   Subtasks that fail are marked in red. You can click their names to view the failure causes.


   .. figure:: /_static/images/en-us_image_0000002305406929.png
      :alt: **Figure 9** Viewing the import result

      **Figure 9** Viewing the import result
