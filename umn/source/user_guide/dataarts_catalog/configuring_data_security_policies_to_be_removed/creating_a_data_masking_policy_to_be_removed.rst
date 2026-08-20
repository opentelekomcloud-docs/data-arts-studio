:original_name: dataartsstudio_01_0825.html

.. _dataartsstudio_01_0825:

Creating a Data Masking Policy (To Be Removed)
==============================================

You can create a data masking policy and perform masking query in DataArts Catalog.

.. important::

   Data security capabilities are provided by DataArts Security, and no longer by DataArts Catalog in regions where DataArts Security is available. Currently, the data security function in DataArts Catalog is available only to existing users.

Prerequisites
-------------

-  A data classification rule has been created. For details on how to create a classification rule, see :ref:`Creating a Data Classification (To Be Removed) <dataartsstudio_01_0822>`.
-  A data connection and a data table have been created, and sensitive data has been collected by DataArts Catalog.

Creating a Masking Policy
-------------------------

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Catalog**.

2. Choose **DataArts Security** > **Masking Policies** from the left navigation bar, and click **Create** on the page displayed.

3. Set **Classification Rule**, **Masking Algorithm**, and **Algorithm Type**. The options for **Masking Algorithm** include **Mask**, **Truncate**, and **Hash**. Each masking algorithm has multiple algorithm types. Select an algorithm type as required. After the configuration, click **OK**.

   .. note::

      A data classification rule can be bound to only one masking algorithm.


   .. figure:: /_static/images/en-us_image_0000002234242548.png
      :alt: **Figure 1** Creating a masking policy

      **Figure 1** Creating a masking policy

4. After you configured the making algorithm, you can perform an online test. Enter the test data, and click **Test**. You can verify the result in the **Test Result** text box.

5. Enable or disable **Status**. The masking policy takes effect only when **Status** is enabled.

Viewing the Data Masking Effect
-------------------------------

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Catalog**.

2. Choose **Data Map** > **Catalog** from the left navigation bar.
3. In a list of asset results, click a table name to access its details page.
4. Click **Data Preview** to view the data masking effect.
