:original_name: dataartsstudio_01_1164.html

.. _dataartsstudio_01_1164:

Synchronizing MRS Hive and Hetu Permissions
===========================================

If MRS Hetu is connected to MRS Hive and Ranger is used for permission control, the Ranger permissions of Hetu rather than of Hive are used to authenticate the access to Hive data from Hetu in the same cluster.

To avoid repeated configuration of Hive data permissions on Hetu, you can configure a Hetu permission synchronization policy so that Hive permissions can be automatically synchronized to Hetu. This improves permission management consistency and usability.

The Hetu permission synchronization policies configured for a DataArts Studio instance are visible to and take effect for all the workspaces of the instance.

Prerequisites
-------------

-  Ranger permission control has been enabled for MRS Hetu. For details, see "HetuEngine Permission Management Overview" in MapReduce Service (MRS) User Guide.
-  Before configuring a Hetu permission synchronization policy, you have created an MRS Hive connection and an MRS Hetu connection in Management Center. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.

Constraints
-----------

-  Only the DARTS Administrator, Tenant Administrator, or data security administrator can create, modify, or delete Hetu permission synchronization policies. Other common users do not have permission to perform these operations.
-  Hive permissions can be synchronized only to Hetu in the same MRS cluster.
-  When configuring a Hetu permission synchronization policy, you need to configure mappings between Hive and Hetu catalogs. If a Hive source is connected to multiple Hetu catalogs, you need to configure multiple synchronization policies.
-  After a Hetu permission synchronization policy is created, existing Hive permissions will not be automatically synchronized to Hetu. Instead, the permissions will be synchronized to Hetu only after a permission synchronization is triggered. This prolongs the permission synchronization duration.
-  Hive permission synchronization is not affected if permissions fail to be synchronized to Hetu.
-  After a Hetu permission synchronization policy is deleted, the permissions that have been synchronized to Hetu will not be revoked.
-  The names of Ranger policies for synchronizing permissions to Hetu are in the following format: **Catalog name**\ \_\ **Schema name**\ +\ **Table name**\ +\ **Column name**. If a policy with the same resource and name already exists on Hetu Ranger, permissions will fail to be synchronized to Hetu. In this case, you must manually clear that existing policy on Hetu Ranger.

Creating a Hetu Permission Synchronization Policy
-------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Hetu Permission Synchronization**.


   .. figure:: /_static/images/en-us_image_0000002269119593.png
      :alt: **Figure 1** Hetu Permission Synchronization page

      **Figure 1** Hetu Permission Synchronization page

#. Click **Create** and set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1164__en-us_topic_0000001678592057_table99188713455>`.


   .. figure:: /_static/images/en-us_image_0000002269199673.png
      :alt: **Figure 2** Setting parameters for a Hetu permission synchronization policy

      **Figure 2** Setting parameters for a Hetu permission synchronization policy

   The following table lists the parameters for a Hetu permission synchronization policy.

   .. _dataartsstudio_01_1164__en-us_topic_0000001678592057_table99188713455:

   .. table:: **Table 1** Policy parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                          |
      +===================================+======================================================================================================================================================================+
      | \*Policy Name                     | Name of the Hetu permission synchronization policy. It must be unique for each data table.                                                                           |
      |                                   |                                                                                                                                                                      |
      |                                   | You are advised to include the cluster name and catalog name in the policy name for easy management.                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Description                | A description of the Hetu permission synchronization policy to be created. It can contain a maximum of 255 characters.                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Permission Source**             |                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source Type                | Only **MRS Hive** is supported.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | If no data connection is available, create one by referring to :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cluster Name                      | The data source cluster in the data connection is automatically selected.                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Permission Target**             |                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source Type                | Only **MRS Hetu** is supported.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | If no data connection is available, create one by referring to :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                           |
      |                                   |                                                                                                                                                                      |
      |                                   | The cluster to which the selected Hetu connection belongs must be the same as that to which the Hive connection belongs.                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cluster Name                      | The data source cluster in the data connection is automatically selected.                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Catalog                         | Name of the Hetu data source, which is **hive** by default. Multiple Hetu catalogs can connect to the same Hive. You can also select another catalog of the cluster. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Submit**.

#. When Hive permission synchronization is triggered, permissions are synchronized to Ranger on Hetu. The policy is named in the following format: **Catalog name**\ \_\ **Schema name**\ +\ **Table name**\ +\ **Column name**. :ref:`Table 2 <dataartsstudio_01_1164__table576816235314>` shows the policy mapping between Hive and Hetu.

   .. _dataartsstudio_01_1164__table576816235314:

   .. table:: **Table 2** Policy mapping between Hive and Hetu

      ====================== ==========================
      Hive                   Hetu
      ====================== ==========================
      **Resource mapping**
      Hive data source       Hetu Catalog
      Hive database          Hetu Schema
      Hive table             Hetu table
      Hive column            Hetu column
      **Permission mapping**
      select                 select and use
      update                 insert, delete, and update
      create                 create
      drop                   drop
      alter                  alter
      all                    all
      ====================== ==========================

Related Operations
------------------

-  Editing a policy: On the **Hetu Permission Synchronization** page, locate a policy and click **Edit** in the **Operation** column to edit the policy.

-  Deleting policies: On the **Hetu Permission Synchronization** page, locate a policy and click **Delete** in the **Operation** column to delete the policy. To delete multiple policies, select them and click **Delete** above the policy list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Viewing policy details: On the **Hetu Permission Synchronization** page, locate a policy, and click **Details** in the **Operation** column to view details of the policy.


   .. figure:: /_static/images/en-us_image_0000002234080396.png
      :alt: **Figure 3** Viewing policy details

      **Figure 3** Viewing policy details
