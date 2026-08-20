:original_name: dataartsstudio_01_1010.html

.. _dataartsstudio_01_1010:

Creating Data Security Levels
=============================

To facilitate data management, you need to create data security levels and describe data confidentiality, for example, you can specify the application scope of your data. This section describes how to define data security levels and configure the default security level.

Data security levels, data classifications, and identification rules are DataArts Studio instance-level configurations and can be exchanged between workspaces. In this way, data can be managed based on unified standards in the Data Map component.

Prerequisites
-------------

At least one security level has been created based on :ref:`Creating a Security Level <dataartsstudio_01_1010__en-us_topic_0000001676039817_section06876409418>`.

Constraints
-----------

-  According to the industry common practice, a larger number indicates a higher security level. A maximum of 10 security levels can be created.

-  Only the DARTS Administrator, Tenant Administrator, or data security administrator can create, modify, or delete data security levels, classifications, and identification rules. Other common users do not have permission to perform these operations.

-  After the default security level is configured, it applies to all the data tables and fields (including inventory and incremental data) that have no security levels in MRS Hive and GaussDB(DWS) data sources. The default security level can be displayed in Data Map and can be used to control permissions for data preview based on :ref:`Managing Sensitive Data <dataartsstudio_01_1015>`.

   .. note::

      The security levels displayed during permission requests are from Data Map and include the default security level. The security levels displayed during static and dynamic masking are from sensitive data discovery tasks and do not include the default security level.

-  Data security levels that are referenced can be deleted only if the reference is canceled.

.. _dataartsstudio_01_1010__en-us_topic_0000001676039817_section06876409418:

Creating a Security Level
-------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Data Confidentiality**.


   .. figure:: /_static/images/en-us_image_0000002269120173.png
      :alt: **Figure 1** Data Confidentiality page

      **Figure 1** Data Confidentiality page

#. On the displayed page, click **Create** and set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1010__en-us_topic_0000001676039817_table1125141919221>`.


   .. figure:: /_static/images/en-us_image_0000002234240816.png
      :alt: **Figure 2** Creating a data security level

      **Figure 2** Creating a data security level

   .. _dataartsstudio_01_1010__en-us_topic_0000001676039817_table1125141919221:

   .. table:: **Table 1** Parameters

      +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                                                                   |
      +=============+===============================================================================================================================================+
      | \*Name      | The security level name can include only letters, numbers, and underscores (_). After a security level is created, its name cannot be edited. |
      +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Description | All characters can be entered in a security level description. After a security level is created, you can edit its description.               |
      +-------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      By default, security levels are displayed in ascending order. You can also move a security level up or down as required.

Configuring the Default Security Level
--------------------------------------

You can configure the default security level for the assets in MRS Hive and GaussDB(DWS) data sources.

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Data Confidentiality**.


   .. figure:: /_static/images/en-us_image_0000002234240840.png
      :alt: **Figure 3** Data Confidentiality page

      **Figure 3** Data Confidentiality page

#. Select a security level from the **Default Security Level** drop-down list box in the upper right corner as the default security level.

   After the default security level is configured, it applies to all the data tables and fields (including inventory and incremental data) that have no security levels in MRS Hive and GaussDB(DWS) data sources. The default security level can be displayed in Data Map and can be used to control permissions for data preview based on :ref:`Managing Sensitive Data <dataartsstudio_01_1015>`.

   .. note::

      The security levels displayed during permission requests are from Data Map and include the default security level. The security levels displayed during static and dynamic masking are from sensitive data discovery tasks and do not include the default security level.


   .. figure:: /_static/images/en-us_image_0000002234240832.png
      :alt: **Figure 4** Creating a data security level

      **Figure 4** Creating a data security level

Related Operations
------------------

-  Adjusting a security level: On the **Data Confidentiality** page, locate a security level, click **More** in the **Operation** column, and select **Up** or **Down**.
-  Editing a security level: On the **Data Confidentiality** page, locate a security level and click **Edit** in the **Operation** column to change the description of the security level.
-  Deleting one or more security levels: On the **Data Confidentiality** page, locate a security level and click **Delete** in the **Operation** column to delete the security level. To delete multiple security levels, select them and click **Delete** above the list.

   .. note::

      -  Data security levels that are referenced can be deleted only if the reference is canceled.
      -  The deletion operation cannot be undone. Exercise caution when performing this operation.
