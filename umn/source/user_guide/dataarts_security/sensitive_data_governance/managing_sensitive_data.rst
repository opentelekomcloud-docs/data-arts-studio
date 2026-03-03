:original_name: dataartsstudio_01_1015.html

.. _dataartsstudio_01_1015:

Managing Sensitive Data
=======================

With DataArts Security, you can manage Data Map assets by security level and control users' access to metadata. After you configure a security level for a specified user or user group, the user or user group can only preview the fields whose security levels are lower than or equal to the configured security level.

The security level-based permission control policies configured for a DataArts Studio instance are visible to and take effect for all the workspaces of the instance. If no security level-based permission control policy is configured, DataArts Security provides a default policy. This policy grants the permission to access data of the highest security level to all users by default. After the administrator configures a policy, the default policy can be deleted.

Prerequisites
-------------

A sensitive data discovery task has been performed and discovered sensitive data has been automatically or manually synchronized to Data Map. For details, see :ref:`Discovering Sensitive Data <dataartsstudio_01_1013>` or :ref:`Viewing Sensitive Data Distribution <dataartsstudio_01_1014>`.

Constraints
-----------

-  Only the DARTS Administrator, Tenant Administrator, or data security administrator can create, modify, or delete security level-based permission control policies. Other common users do not have permission to perform these operations.
-  Security level-based permission control is available only for the fields with security levels in Data Map and unavailable for tables with security levels.
-  A user/user group and a security level uniquely identify a security level-based permission control policy. A policy for the same user, user group, or security level cannot be created.
-  If a user or user group corresponds to multiple security levels, the highest security level prevails.

Creating a Sensitive Data Control Policy
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the navigation pane on the left, choose **Sensitive Data Governance**.

   A default policy is displayed on the page. This policy grants all users the permission to access data with the highest security level.


   .. figure:: /_static/images/en-us_image_0000002234076456.png
      :alt: **Figure 1** Sensitive Data Governance page

      **Figure 1** Sensitive Data Governance page

#. Click **Create** and set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1015__en-us_topic_0000001678592057_table99188713455>`.


   .. figure:: /_static/images/en-us_image_0000002234236288.png
      :alt: **Figure 2** Setting parameters for a security level-based permission control policy

      **Figure 2** Setting parameters for a security level-based permission control policy

   The following table lists the parameters for the security level-based permission control policy.

   .. _dataartsstudio_01_1015__en-us_topic_0000001678592057_table99188713455:

   .. table:: **Table 1** Policy parameters

      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                                                                 |
      +===================+=============================================================================================================================================================================================+
      | \*User Type       | Select **User** or **User Group**.                                                                                                                                                          |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Username        | Select a user or user group from all workspace members of the current instance.                                                                                                             |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Confidentiality | Select a security level for the specified user or user group. The user or user group can only access assets whose security levels are lower than or equal to the configured security level. |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Permission Type | Only **PREVIEW** in Data Map is available.                                                                                                                                                  |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save**.

   .. note::

      After creating the policy, delete the default policy to make the created policy take effect.

Related Operations
------------------

-  Editing a security level-based permission control policy: On the **Sensitive Data Governance** page, locate a policy and click **Edit** in the **Operation** column to change the user/user group, confidentiality, or permission type.
-  Deleting security level-based permission control policies: On the **Sensitive Data Governance** page, locate a policy and click **Delete** in the **Operation** column to delete the policy. To delete multiple policies, select them and click **Delete** above the policy list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.
