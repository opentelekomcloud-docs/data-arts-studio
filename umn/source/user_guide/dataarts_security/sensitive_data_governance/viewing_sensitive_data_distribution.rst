:original_name: dataartsstudio_01_1014.html

.. _dataartsstudio_01_1014:

Viewing Sensitive Data Distribution
===================================

This section describes how to view and modify the sensitive data discovery result.

-  View the result of a sensitive data discovery task.

-  Manual recovery: After sensitive data is discovered, you must perform manual recovery to confirm that the identification rule in the task is in valid state so that the identification rule takes effect for static masking tasks.

   If you selected **Manually synchronize the recognition result** for the sensitive data discovery task, you must click **Data Sync** to synchronize the discovered sensitive data to Data Map. (Before synchronizing data, ensure that a metadata collection task has been performed in DataArts Architecture. Otherwise, the synchronization will fail.)

Prerequisites
-------------

-  You have created and executed a sensitive data discovery task. For details, see :ref:`Creating a Sensitive Data Discovery Task <dataartsstudio_01_1013__en-us_topic_0000001676159741_section191138181>`.
-  Only the DARTS Administrator, Tenant Administrator, or data security administrator has the permission to synchronize sensitive data to Data Map.
-  Before synchronizing sensitive data, you have collected the metadata of the data connection in DataArts Catalog. For details, see :ref:`Metadata Collection Task <dataartsstudio_01_0804>`. Otherwise, the synchronization will fail and an error message will be displayed, indicating that no data connection is available.

Constraints
-----------

-  Currently, sensitive data can be synchronized only to Data Map. Sensitive data cannot be synchronized to DataArts Catalog, and sensitive data security levels and classifications cannot be added or edited in DataArts Catalog.
-  Sensitive data synchronization depends on metadata collection tasks. If the metadata of a data connection has not been collected, no data connection can be found.

Viewing and Modifying the Sensitive Data Discovery Result
---------------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the navigation pane on the left, choose **Sensitive Data Distribution**.


   .. figure:: /_static/images/en-us_image_0000002269123241.png
      :alt: **Figure 1** Sensitive Data Distribution page

      **Figure 1** Sensitive Data Distribution page

#. On the **Sensitive Data Distribution** page, you can use either of the following methods to view and modify the sensitive data discovery result. Method 1 is recommended. It allows you to view and modify the discovered sensitive data, change the data security level and classification, and perform batch operations without switching to other pages.

   -  (Recommended) Method 1: On the **Sensitive Data Distribution** tab page, click |image1| to expand data source details, view sensitive data, and change the data security level, classification, and status.

      -  **OK**: Confirm that the identification result is valid. You can confirm rules in unconfirmed or invalid state. Static masking tasks can be executed using valid identification rules.
      -  **Ignore**: Confirm that the identification result is invalid. You can ignore rules in valid state. Unconfirmed or invalid identification rules cannot be selected for static masking tasks.
      -  **Data Sync**: If you selected **Manually synchronize the recognition result** for the sensitive data discovery task, you must click **Data Sync** to synchronize the discovered sensitive data to Data Map. (Before synchronizing data, ensure that a metadata collection task has been performed in DataArts Architecture. Otherwise, the synchronization will fail.)
      -  **Delete**: Delete the discovered result.


      .. figure:: /_static/images/en-us_image_0000002269203249.png
         :alt: **Figure 2** Viewing and modifying the discovered sensitive data

         **Figure 2** Viewing and modifying the discovered sensitive data

   -  Method 2: Click the **Data Discovery** tab. Search for a data connection name to find the sensitive data you want and click **View** in the **Operation** column to view details of the sensitive data.


      .. figure:: /_static/images/en-us_image_0000002269123037.png
         :alt: **Figure 3** Data discovery

         **Figure 3** Data discovery


      .. figure:: /_static/images/en-us_image_0000002269203313.png
         :alt: **Figure 4** Viewing details

         **Figure 4** Viewing details

      Click the **Manual Recovery** tab, search for and locate a rule, and click **OK**, **Ignore**, or **Data Sync** in the **Operation** column to change the data status.

      -  **OK**: Confirm that the identification result is valid. You can confirm rules in unconfirmed or invalid state. Static masking tasks can be executed using valid identification rules.
      -  **Ignore**: Confirm that the identification result is invalid. You can ignore rules in valid state. Unconfirmed or invalid identification rules cannot be selected for static masking tasks.
      -  **Data Sync**: If you selected **Manually synchronize the recognition result** for the sensitive data discovery task, you must click **Data Sync** to synchronize the discovered sensitive data to Data Map. (Before synchronizing data, ensure that a metadata collection task has been performed in DataArts Architecture. Otherwise, the synchronization will fail.)


      .. figure:: /_static/images/en-us_image_0000002234243700.png
         :alt: **Figure 5** Modifying sensitive data

         **Figure 5** Modifying sensitive data

.. |image1| image:: /_static/images/en-us_image_0000002269203125.png
