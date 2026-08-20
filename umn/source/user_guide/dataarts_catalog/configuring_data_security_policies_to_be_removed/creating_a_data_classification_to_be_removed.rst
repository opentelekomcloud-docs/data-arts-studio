:original_name: dataartsstudio_01_0822.html

.. _dataartsstudio_01_0822:

Creating a Data Classification (To Be Removed)
==============================================

You can create data classification rules.

.. important::

   Data security capabilities are provided by DataArts Security, and no longer by DataArts Catalog in regions where DataArts Security is available. Currently, the data security function in DataArts Catalog is available only to existing users.

You can create a data masking policy to mask data only after you have created a data classification rule.

Prerequisites
-------------

A data security level has been created. For details, see :ref:`Creating a Data Security Level (To Be Removed) <dataartsstudio_01_0823>`.

Creating a Data Classification Rule
-----------------------------------

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Catalog**.

2. Choose **DataArts Security** > **Classifications** from the left navigation bar. On the **Classification Rule** tab page, click **Create**.

   On the page displayed, set the parameters to create a data classification rule. You can either create a rule by using a system template or custom template.


   .. figure:: /_static/images/en-us_image_0000002234242860.jpg
      :alt: **Figure 1** Creating a data classification rule

      **Figure 1** Creating a data classification rule

   .. table:: **Table 1** Parameters for creating a data classification rule

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Classification Type               | The category to which a rule belongs. You can either create a rule by using a system template or custom template.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confidentiality                   | Classify the configured data into different levels. If the existing confidentiality does not meet the requirements, go to the confidentiality management page to set security levels. For details, see :ref:`Creating a Data Security Level (To Be Removed) <dataartsstudio_01_0823>`. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Classification Template           | This parameter is available when **Classification Type** is set to **Built-in**. You can select a system sensitive data identification template based on service requirements, for example, **Time**, **Mobile number**, and **License plate number**.                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Classification Name               | -  If **Classification Type** is set to **Built-in**, a classification name is automatically generated based on the classification template selected.                                                                                                                                  |
      |                                   | -  If **Classification Type** is set to **Custom**, you can customize a classification name.                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   |    .. note::                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   |       The name of a data classification rule must be unique.                                                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rule Recognition                  | This parameter is available when **Classification Type** is set to **Custom**. Regular expressions are supported.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Regular Expression                | -  **Content recognition**: You can customize a regular expression.                                                                                                                                                                                                                    |
      |                                   | -  **Column name recognition**: Both exact match and fuzzy match are supported. Multiple fields can be matched.                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the data classification rule to create.                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Creating a Group
----------------

#. On the DataArts Studio console, locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Catalog**.

2. Choose **DataArts Security** > **Classifications** from the left navigation bar. On the **Groups** tab page, click **Create**.

   In the **Create Group** dialog box, set the parameters and click **OK**.

   Set the parameters by referring to :ref:`Table 2 <dataartsstudio_01_0822__table8554125143016>` and select classification rules in the list.

   The selected rules are displayed in the list on the right.

   .. _dataartsstudio_01_0822__table8554125143016:

   .. table:: **Table 2** Parameters for creating a group

      +-------------+------------------------------------------------------------------------------+
      | Parameter   | Description                                                                  |
      +=============+==============================================================================+
      | Name        | The name of a group. Only letters, numbers, and underscores (_) are allowed. |
      +-------------+------------------------------------------------------------------------------+
      | Description | Information to better identify the group. It cannot exceed 4,096 characters. |
      +-------------+------------------------------------------------------------------------------+
