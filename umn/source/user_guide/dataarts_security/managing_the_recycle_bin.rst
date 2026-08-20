:original_name: dataartsstudio_01_1183.html

.. _dataartsstudio_01_1183:

Managing the Recycle Bin
========================

The recycle bin allows you to restore key data of DataArts Security that has been deleted by mistake. The key data includes permission set-related resources (workspace permission sets, permission sets, and common roles), dynamic masking policies, and keys. The key data is determined by the importance, use frequency, and restoration difficulty of data.

Prerequisites
-------------

Permission set-related resources (workspace permission sets, permission sets, and common roles), dynamic masking policies, or keys have been deleted in the last 30 days.

Notes and Constraints
---------------------

-  Only the DARTS Administrator, Tenant Administrator, and data security administrator can restore data.
-  Managed MRS roles are existing roles in MRS data and are not defined in DataArts Security, so they will not be moved to the recycle bin when deleted.
-  After permission set-related resources and dynamic masking policies are deleted and moved to the recycle bin, their synchronization statuses will become unsynchronized. After they are restored from the recycle bin, they must be synchronized so that they can take effect.
-  Data in the recycle bin can be retained for a maximum of 30 days. Deleted data will be permanently cleared after a 30-day retention period.
-  A maximum of 1,000 permission sets, dynamic masking policies, or keys can be retained in the recycle bin of an instance. If that limit is exceeded, the oldest permission sets or dynamic masking policies will be automatically cleared first, on a first-in-first-out basis.
-  If **Name Conflict Strategy** is set to **Add a timestamp to each name** during data restoration and the name of the data to be restored already exists, a timestamp will be added to the name of the data to be restored. That is, the name of the restored data is in **Original name**\ \_\ **13-digit timestamp** format. If the name of the data to be restored with the timestamp contains more than 64 characters, the original name will be truncated to ensure that the name of the data to be restored contains no more than 64 characters.
-  When you restore a permission set that was deleted by mistake from the recycle bin, the association between permission sets will be checked. If certain conditions are not met, the permission set cannot be restored. For example, if the parent permission set of a permission set has been deleted, the permission set can be restored only after its parent permission set is restored.
-  A maximum of 20 data records can be restored at a time.

Restoring Data in the Recycle Bin
---------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Recycle Bin**.


   .. figure:: /_static/images/en-us_image_0000002269195621.png
      :alt: **Figure 1** Recycle Bin page

      **Figure 1** Recycle Bin page

#. On the **Recycle Bin** page, you can view and restore deleted permission set-related resources (workspace permission sets, permission sets, and common roles), dynamic masking policies, or keys.

   The operations for restoring different types of data are similar. In the following operations, permission sets are used as an example to describe how to restore data.

#. On the **Permission Sets** page, locate the permission set you want to restore and click **Restore** in the **Operation** column. Alternatively, select the permission sets you want to restore and click **Restore** above the list to restore the permission sets.


   .. figure:: /_static/images/en-us_image_0000002234236188.png
      :alt: **Figure 2** Restoring data

      **Figure 2** Restoring data

#. In the displayed dialog box, set **Name Conflict Strategy** to avoid a conflict between the restored data and existing data. Then click **Yes**.

   -  **Report an error**: If the name of the data to be restored already exists, an error will be reported and the data will not be restored.

   -  **Add a timestamp to each name**: If the name of the data to be restored already exists, a timestamp will be added to the name. That is, the name of the data to be restored is in **Original name**\ \_\ **13-digit timestamp** format. If the name of the data to be restored with the timestamp contains more than 64 characters, the original name will be truncated to ensure that the name of the data to be restored contains no more than 64 characters.


      .. figure:: /_static/images/en-us_image_0000002269195609.png
         :alt: **Figure 3** Setting Name Conflict Strategy

         **Figure 3** Setting Name Conflict Strategy

#. After restoring workspace permission sets, permission sets, common roles, or dynamic masking policies, check them on corresponding pages and synchronize them to make them take effect.
