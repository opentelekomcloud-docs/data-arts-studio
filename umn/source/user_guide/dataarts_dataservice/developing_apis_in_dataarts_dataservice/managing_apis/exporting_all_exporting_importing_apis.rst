:original_name: dataartsstudio_01_0320.html

.. _dataartsstudio_01_0320:

Exporting All/Exporting/Importing APIs
======================================

Operation Scenario
------------------

DataArts DataService allows you to import and export (including exporting all) APIs to quickly copy or migrate existing APIs.

Constraints
-----------

-  To export all APIs, you must have the permissions of the DARTS Administrator or Tenant Administrator.
-  All the APIs of a workspace can be exported only once, and only one such export task can be executed within a minute.

Exporting All APIs
------------------

You can export all APIs based on the current filter criteria. You must have the permissions of the DARTS Administrator or Tenant Administrator.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Choose **API Development** > **APIs**.

#. Above the API list, choose **More** > **Export All**.

   .. note::

      -  To export all APIs, you must have the permissions of the DARTS Administrator or Tenant Administrator.
      -  All the APIs of a workspace can be exported only once, and only one such export task can be executed within a minute.

   In the displayed dialog box, click **Yes** to export all the APIs to an Excel file.


   .. figure:: /_static/images/en-us_image_0000002234079032.png
      :alt: **Figure 1** Exporting all APIs

      **Figure 1** Exporting all APIs

#. Open the downloaded Excel file to view the exported APIs. APIs of different types are exported to different sheets.

Exporting APIs
--------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Choose **API Development** > **APIs**.

#. Select the target APIs, click **More** above the API list, and select **Export**.

#. In the displayed dialog box, confirm the APIs to export and click **Yes** to export the APIs to an Excel file.


   .. figure:: /_static/images/en-us_image_0000002269198301.png
      :alt: **Figure 2** Exporting APIs

      **Figure 2** Exporting APIs

#. Open the downloaded Excel file to view the exported APIs. APIs of different types are exported to different sheets.

Importing APIs
--------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Choose **API Development** > **APIs**.

#. Click **More** above the API list and select **Import**.

#. On the **Import API** page, set parameters and click **Select**. Select the API file to be imported and click **Import**. The import status is displayed in the **Import Result** area.

   .. table:: **Table 1** Parameters for importing APIs

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                         |
      +===================================+=====================================================================================================================+
      | Overwrite                         | Whether to overwrite APIs with the same names as the APIs to be imported. By default, APIs are not overwritten.     |
      |                                   |                                                                                                                     |
      |                                   | -  **No**: If there is an API with the same name as an API to be imported, the API will not be imported.            |
      |                                   | -  **Yes**: If there is already an API with the same name, the API definition is updated based on the imported API. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Import File                       | The API file can be one exported from another project or an Excel file edited based on the template specifications. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002234079020.png
      :alt: **Figure 3** Importing APIs

      **Figure 3** Importing APIs

#. After the APIs are imported successfully, you can view them in the API list.
