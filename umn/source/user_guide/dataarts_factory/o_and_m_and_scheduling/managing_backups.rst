:original_name: dataartsstudio_01_0516.html

.. _dataartsstudio_01_0516:

Managing Backups
================

You can back up all jobs, scripts, resources, and environment variables at a specified interval.

You can also restore assets that have been backed up, including jobs, scripts, resources, and environment variables.

Constraints
-----------

-  This function depends on OBS.
-  Backup files cannot be automatically aged. You need to manually delete backup files on a regular basis.

Prerequisites
-------------

OBS has been enabled and a folder has been created in OBS.

.. _dataartsstudio_01_0516__en-us_topic_0169685606_section381611818613:

Backing Up Assets
-----------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation tree on the left, choose **Manage Backup**.
#. Click **Start Daily Backup**. In the **Browse OBS File** dialog box, select an OBS folder.

   .. note::

      -  Daily Backup starts at 00:00 every day to back up all jobs, scripts, resources, and environment variables of the previous day. The jobs, scripts, resources, and environment variables of the previous day are not backed up on the current day.
      -  If you select only the bucket name as the OBS storage path, the backup object is automatically stored in the folder named after the backup date. Environment variables, resources, scripts, and jobs are stored in the **1_env**, **2_resources**, **3_scripts**, and **4_jobs** folders, respectively.
      -  After the backup is successful, the **backup.json** file is automatically generated in the folder named after the backup date. The file stores job information based on the node type and can be modified before job restoration.
      -  To stop daily backup, click **Stop Daily Backup**.

Restoring Assets
----------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation tree of the DataArts Factory console, choose **Manage Backup**.

#. On the **Manage Restoration** tab, click **Restore Backup**.

   In the **Restore Backup** dialog box, select the storage path of the asset to be restored from the OBS bucket and set the duplicate name policy.

   .. note::

      -  The storage path is the file path generated in :ref:`Backing Up Assets <dataartsstudio_01_0516__en-us_topic_0169685606_section381611818613>`.
      -  Before restoring assets, you can modify the **backup.json** file in the backup path. You can change the connection name (connectionName), database name (database), and cluster name (clusterName).


   .. figure:: /_static/images/en-us_image_0000002269199621.png
      :alt: **Figure 1** Restoring assets

      **Figure 1** Restoring assets

#. Click **OK**.
