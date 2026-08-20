:original_name: dataartsstudio_04_0010.html

.. _dataartsstudio_04_0010:

Step 8: View Data Assets
========================

In the DataArts Studio DataArts Catalog module, you can view data maps. For details, see chapter "DataArts Catalog" in *DataArts Studio User Guide*. A data map displays business assets and technical assets. Business assets refer to logical entities and business objects. Technical assets refer to data connections and database objects.

This topic describes how to view service assets and technical assets in the DataArts Catalog module of DataArts Studio. For example, in the fact table of a technical asset, you can view details such as data lineage. In the summary table of a technical asset, you can view details such as preview results.

.. _dataartsstudio_04_0010__en-us_topic_0181028494_section349327104110:

Viewing Logical Assets and Technical Assets
-------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

#. In the left navigation pane, choose **Data Map** > **Data Catalog**, click the **Logical Assets** tab, and select a business catalog under **Search Filters**. The logical assets that meet the filter criteria are displayed.

#. Click the **Technical Assets** tab, select a value for **Data Connections**, and select **Table** for **Types**. The metadata that meets the filter criteria is displayed on the right.


   .. figure:: /_static/images/en-us_image_0000002234232312.png
      :alt: **Figure 1** Technical assets

      **Figure 1** Technical assets

#. In the asset list, click the name of the target metadata to view its details.

   For example, click the name of the fact table **fact_stroke_order** in the asset list to view its details. On the details page, click the **Lineage** tab to view upstream and downstream information of the fact table.


   .. figure:: /_static/images/en-us_image_0000002234232320.png
      :alt: **Figure 2** Lineage

      **Figure 2** Lineage

   In the asset list, click the name of the summary table **dws_payment_type** to view its details. On the details page, click the **Data Preview** tab to preview the data in the summary table.


   .. figure:: /_static/images/en-us_image_0000002234232324.png
      :alt: **Figure 3** Data Preview

      **Figure 3** Data Preview
