:original_name: dataartsstudio_01_1030.html

.. _dataartsstudio_01_1030:

Creating Data Classifications
=============================

If data security levels cannot meet the data classification requirements in the case of a large amount of data, you can create data classifications for data of different values to better manage and measure your data. Data of different classifications are parallel, equal, and mutually exclusive. This section describes how to create data classifications.

Data security levels, data classifications, and identification rules are DataArts Studio instance-level configurations and can be exchanged between workspaces. In this way, data can be managed based on unified standards in the Data Map component.

Prerequisites
-------------

Before importing preset data classifications, ensure that at least one security level has been created according to :ref:`Creating Data Security Levels <dataartsstudio_01_1010>`.

Constraints
-----------

-  A maximum of 1,000 data classifications at five layers are allowed.
-  Only the **DARTS** **Administrator**, Tenant Administrator, or data security administrator can create, modify, or delete data security levels, classifications, and identification rules. Other common users do not have permission to perform these operations.
-  Classifications with the same name can be created in different parent nodes but not in the same parent node.
-  Before importing preset data classifications, you must configure data security levels for all preset rules.
-  During the import of preset data classifications, their identification rules are also imported. Classifications and rules with the same name as existing classifications and rules cannot be imported.
-  If a parent classification contains sub-classifications, the parent classification can be deleted only after the sub-classifications have been deleted.
-  Data classifications that are referenced can be deleted only if the reference is canceled.

Creating a Classification
-------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Data Classification**.


   .. figure:: /_static/images/en-us_image_0000002269202909.png
      :alt: **Figure 1** Data Classification page

      **Figure 1** Data Classification page

#. Before creating your first classification, click |image1| above the classification directory to add at least one root classification. Then you can click |image2| or |image3| to add a classification of the same level or a sub-classification.

   After you click |image4| or |image5|, set parameters in the displayed dialog box by referring to :ref:`Table 1 <dataartsstudio_01_1030__en-us_topic_0000001630072420_table1125141919221>`.


   .. figure:: /_static/images/en-us_image_0000002234083500.png
      :alt: **Figure 2** Creating a data classification

      **Figure 2** Creating a data classification

   .. _dataartsstudio_01_1030__en-us_topic_0000001630072420_table1125141919221:

   .. table:: **Table 1** Parameters

      +-----------------------+--------------------------------------------------------+
      | Parameter             | Description                                            |
      +=======================+========================================================+
      | \*Classification Name | Only letters, digits, and underscores (_) are allowed. |
      +-----------------------+--------------------------------------------------------+
      | Description           | All characters are allowed.                            |
      +-----------------------+--------------------------------------------------------+

Importing Preset Classifications
--------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Data Classification**.


   .. figure:: /_static/images/en-us_image_0000002269202909.png
      :alt: **Figure 3** Data Classification page

      **Figure 3** Data Classification page

#. If no classification is available, click **Import Preset Data Classification**. If there are classifications, click |image6| to open the **Import Preset Data Classification** dialog box.

   In the **Import Preset Data Classification** dialog box, select the data classifications to import, set security levels for the rules to import, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234243376.png
      :alt: **Figure 4** Importing preset data classifications

      **Figure 4** Importing preset data classifications

Related Operations
------------------

-  Editing a classification: On the **Data Classification** page, select the classification to be modified and click |image7| above the classification directory to change the classification name or description.

-  Deleting a classification: On the **Data Classification** page, select the classification to be deleted and click |image8| above the classification directory to delete the classification.

   You can also delete classifications by editing the data classification directory. To be specific, you can click |image9| above the classification directory and delete classifications on the displayed **Edit Data Classification Directory** page.

   .. note::

      -  If a parent classification contains sub-classifications, the parent classification can be deleted only after the sub-classifications have been deleted.
      -  Data classifications that are referenced can be deleted only if the reference is canceled.
      -  The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Editing a classification directory: Click |image10| above the classification directory. On the **Edit Data Classification Directory** page, you can add sub-classifications or delete classifications.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002234083540.png
.. |image2| image:: /_static/images/en-us_image_0000002234083524.png
.. |image3| image:: /_static/images/en-us_image_0000002234243424.png
.. |image4| image:: /_static/images/en-us_image_0000002269122769.png
.. |image5| image:: /_static/images/en-us_image_0000002269122741.png
.. |image6| image:: /_static/images/en-us_image_0000002234083532.png
.. |image7| image:: /_static/images/en-us_image_0000002269122729.png
.. |image8| image:: /_static/images/en-us_image_0000002269122761.png
.. |image9| image:: /_static/images/en-us_image_0000002234083536.png
.. |image10| image:: /_static/images/en-us_image_0000002269122749.png
