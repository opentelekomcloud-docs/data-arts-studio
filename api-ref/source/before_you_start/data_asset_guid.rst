:original_name: dataartsstudio_02_0351.html

.. _dataartsstudio_02_0351:

Data Asset GUID
===============

Each logical, technical, or metric asset has a GUID, which is the unique identifier of the asset. Some URIs in the calls to DataArts Catalog or Data Map APIs require the GUID.

You can obtain the asset GUID using the corresponding API (recommended) or from the console.

Obtaining the asset GUID from the console is complex. To obtain the asset GUID from the console, perform the following steps:

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, click **Data Map** or locate a workspace and click **DataArts Catalog**.

#. Press **F12** to open the developer debugging tool and click the **Network** tab.


   .. figure:: /_static/images/en-us_image_0000002234266710.png
      :alt: **Figure 1** Network

      **Figure 1** Network

#. On the **Home** or **Data Search** page of the Data Map console, or on the **Dashboard** or **Data Catalog** page of the DataArts Catalog console, locate an asset and click its name to access its details page.

   a. In the network request, search for a long string whose name is similar to **09318f28-939f-4ab6-a374-9e621096652c**.


      .. figure:: /_static/images/en-us_image_0000002269146069.png
         :alt: **Figure 2** Searching for a long string

         **Figure 2** Searching for a long string

   b. Click the string and obtain the GUID from **Request URL**.


      .. figure:: /_static/images/en-us_image_0000002525832086.png
         :alt: **Figure 3** Obtaining the GUID

         **Figure 3** Obtaining the GUID
