:original_name: dataartsstudio_01_0663.html

.. _dataartsstudio_01_0663:

Data Warehouse Planning
=======================

Data warehouse planning enables you to manage data warehouse layers and models in a unified manner. The system provides four default data warehouse layers, including Source Data Integration (SDI), Data Warehouse Integration (DWI), Data Warehouse Report (DWR), and Data Mart (DM). You can also customize data warehouse layers.

-  ER modeling consists of the SDI and DWI layers. Physical models belong to one of the two layers.

   -  SDI stands for Source Data Integration and is the source data layer. SDI is a simple implementation of source system data.
   -  DWI stands for Data Warehouse Integration, also called the data consolidation layer. DWI integrates and cleans data from multiple source systems, and implements entity relationship modeling based on the three normal forms.

      .. note::

         When designing physical models, take the following aspects into consideration:

         -  Physical models must ensure that the required functions are available and their performance is as good as expected.
         -  Physical models must ensure data consistency and quality.
         -  Few or no changes are made to the physical models when new services or functions are added.

-  In dimensional modeling, DWR-layer models are created based on dimensions, and data is aggregated into DM-layer models.

   -  Data Warehouse Report (DWR) is based on the multi-dimensional model and its data granularity is the same as that of the DWI layer.

-  DM: Multiple types of data are summarized and displayed.

   -  DM is where multiple types of data are summarized. DM is designed to display the summarized data.

The administrator can rename the four default data warehouse layers by clicking |image1| next to the names of the layers. The model name can contain only letters, digits, and underscores (_), and must start with a letter.

Physical models, dimensional models, and data marts are managed in a unified manner in data warehouse planning.

Creating a Data Warehouse Layer
-------------------------------

You can create data warehouse layers that suit your business scenarios. The procedure is as follows:

#. Access the DataArts Architecture console.

#. In the left navigation pane, choose **Models** > **Data Warehouse Layer**.

#. On the right of a data warehouse layer, click **Create** and select **Add to front** or **Add to Back**.

   .. note::

      **Add to front** or **Add to Back** indicates that the new data warehouse layer is in front of or after the current data warehouse layer.


   .. figure:: /_static/images/en-us_image_0000002234076168.png
      :alt: **Figure 1** Creating a data warehouse layer

      **Figure 1** Creating a data warehouse layer

#. Set parameters for the data warehouse layer.


   .. figure:: /_static/images/en-us_image_0000002234236016.png
      :alt: **Figure 2** Setting parameters for the data warehouse layer

      **Figure 2** Setting parameters for the data warehouse layer

   .. table:: **Table 1** Parameters for the data warehouse layer

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                      |
      +===================================+==================================================================================================================================================================+
      | \*Name                            | Name of the data warehouse layer. It must start with a letter and can contain only letters, digits, and underscores (_). A maximum of 10 characters are allowed. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Type                            | Type of the layer. It cannot be changed after the layer is created.                                                                                              |
      |                                   |                                                                                                                                                                  |
      |                                   | -  **ER Modeling**                                                                                                                                               |
      |                                   | -  **ER Modeling**                                                                                                                                               |
      |                                   | -  **ER Modeling**                                                                                                                                               |
      |                                   |                                                                                                                                                                  |
      |                                   |    .. note::                                                                                                                                                     |
      |                                   |                                                                                                                                                                  |
      |                                   |       a. ER modeling is used for service systems, the SDI layer, and DWI layer.                                                                                  |
      |                                   |       b. Dimensional modeling is used for the data warehouse public layer or DWR layer.                                                                          |
      |                                   |       c. Data mart is used for modeling summary tables and application tables.                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the data warehouse layer. A maximum of 200 characters are allowed.                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Disable Custom Items              | Whether to disable custom items. If there is no custom item, no custom item can be disabled.                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. You can perform the following operations on the created data warehouse layer:

   -  Click **Edit** to modify its parameters except **Type**.
   -  Click **Delete** to delete it. If the layer contains models, it cannot be deleted.

Creating a Model
----------------

#. Access the DataArts Architecture console.

#. In the left navigation pane, choose **Models** > **Data Warehouse Layer**.

#. Locate a data warehouse layer and click **Create**.

#. In the displayed **Create Model** dialog box, set required parameters.


   .. figure:: /_static/images/en-us_image_0000002234076180.png
      :alt: **Figure 3** Creating a model

      **Figure 3** Creating a model

   .. table:: **Table 2** Model parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================================================================================================================================================+
      | \*Model Name                      | Name of the model. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Connection Type              | Data connection type                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   | -  **Unlimited**                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  Select a data connection.                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Warehouse Layer            | -  To create the model at the DWI layer, SDI layer, or a custom ER modeling data warehouse layer, you can select **DWI**, **SDI**, or a custom data warehouse layer.                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   |    .. note::                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   |       -  **SDI** stands for Source Data Integration and is the source data layer. SDI is a simple implementation of source system data.                                                                                                                                                                                              |
      |                                   |       -  **DWI** stands for Data Warehouse Integration, also called the data consolidation layer. DWI integrates and cleans data from multiple source systems, and implements entity relationship modeling based on the three normal forms.                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   | -  To create the model at the DWR layer or a custom dimensional modeling data warehouse layer, you can select **DWR** or a custom data warehouse layer.                                                                                                                                                                              |
      |                                   | -  To create the model at the DM layer or a custom DM data warehouse layer, you can select **DM** or a custom data warehouse layer.                                                                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prefix                            | Verification prefix. It must start with letters. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                      |
      |                                   |    When you create, modify, or import a physical (relational) table in ER modeling, fact table in dimensional modeling, or summary table in the data mart, the system checks whether there is a prefix. If there is no prefix, the verification fails. When a reversing operation is performed, the system also checks for a prefix. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the data warehouse model. A maximum of 600 characters are allowed.                                                                                                                                                                                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. You can perform the following operations on the created model:

   -  Click **Edit** to modify its parameters except **Data Connection Type**.
   -  Click **Delete** to delete it. Deleted models cannot be recovered. Exercise caution when performing this operation. The model cannot be deleted if it contains tables.
   -  Click **Tables**, **Fields**, or **Standard Coverage** to go to the corresponding data warehouse layer page. For example, if you click **Tables** of a DWI model, you will be redirected to the **ER Modeling** page.
   -  Click **Expand More** to view more data warehouse models and click **Collapse More** to collapse them.
   -  Unlayered data warehouse models are displayed in the upper area of the page. You can edit or delete them.

      -  Click **Edit** to modify the parameters of a data warehouse model. For example, you can set **Data Warehouse Layer** of a model to **DWI**, **SDI**, or a custom data warehouse layers. **Data Connection Type** cannot be modified.
      -  Click **Delete** to delete a data warehouse model. Deleted models cannot be recovered. Exercise caution when performing this operation. The model cannot be deleted if it contains tables.

.. |image1| image:: /_static/images/en-us_image_0000002269195481.png
