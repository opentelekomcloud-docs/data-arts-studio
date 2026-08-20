:original_name: dataartsstudio_01_1012.html

.. _dataartsstudio_01_1012:

Creating Identification Rule Groups
===================================

A sensitive data identification rule group has service logic and contains scattered rules. A rule group is the prerequisite for running a sensitive data discovery task.

Prerequisites
-------------

Identification rules have been created. For details, see :ref:`Creating Identification Rules <dataartsstudio_01_1011>`.

Constraints
-----------

-  During sensitive data identification, if a field matches multiple identification rules in an identification rule group, the highest security level of the identification rules is used as the security level of the field, and multiple field classifications are allowed.
-  A maximum of 100 identification rule groups can be created.
-  Data identification rule groups that are referenced can be deleted only if the reference is canceled.

Creating a Sensitive Data Identification Rule Group
---------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Data Identification Rules** from the left navigation bar.

#. Click the **Rule Groups** tab in the upper part of the displayed page.


   .. figure:: /_static/images/en-us_image_0000002269200045.png
      :alt: **Figure 1** Creating a sensitive data identification rule group

      **Figure 1** Creating a sensitive data identification rule group

#. Click **Create**, set the group name and description based on :ref:`Table 1 <dataartsstudio_01_1012__en-us_topic_0000001627559982_table12131512192419>`, select identification rules, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234080780.png
      :alt: **Figure 2** Parameters for creating an identification rule group

      **Figure 2** Parameters for creating an identification rule group

   The selected rules are displayed in the list on the right. You can click to deselect the selected rules.

   .. _dataartsstudio_01_1012__en-us_topic_0000001627559982_table12131512192419:

   .. table:: **Table 1** Parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                    |
      +===================================+================================================================================================================================================================+
      | \*Group                           | Group names can include only letters, numbers, and underscores (_).                                                                                            |
      |                                   |                                                                                                                                                                |
      |                                   | You are advised to include the rule group meaning into the name and avoid meaningless descriptions so that the rule group can be quickly located and selected. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Information to better identify the group                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

-  Editing a rule group: On the **Rule Groups** page, locate a group and click **Edit** in the **Operation** column to change the name, description, and rules of the group.
-  Deleting a rule group: On the **Rule Groups** page, locate a group and click **Delete** in the **Operation** column. To delete rule groups in a batch, select them and click **Delete** above the list.

   .. note::

      -  Data identification rule groups that are referenced can be deleted only if the reference is canceled.
      -  The deletion operation cannot be undone. Exercise caution when performing this operation.
