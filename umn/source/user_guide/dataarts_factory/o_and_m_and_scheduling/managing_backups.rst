:original_name: dataartsstudio_01_0516.html

.. _dataartsstudio_01_0516:

Managing Backups
================

You can back up all jobs, scripts, resources, and environment variables on a daily basis.

You can also restore assets that have been backed up, including jobs, scripts, resources, and environment variables.

Constraints
-----------

This function depends on OBS.

Prerequisites
-------------

OBS has been enabled and a folder has been created in OBS.

.. _dataartsstudio_01_0516__en-us_topic_0169685606_section381611818613:

Backing Up Assets
-----------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the navigation tree on the left, choose **Manage Backup**.

#. Click **Start Daily Backup**. In the **Browse OBS File** dialog box, select an OBS folder.

   .. note::

      -  Daily Backup starts at 00:00 every day to back up all jobs, scripts, resources, and environment variables of the previous day. The jobs, scripts, resources, and environment variables of the previous day are not backed up on the current day.
      -  If you select only the bucket name as the OBS storage path, the backup object is automatically stored in the folder named after the backup date. Environment variables, resources, scripts, and jobs are stored in the **1_env**, **2_resources**, **3_scripts**, and **4_jobs** folders, respectively.
      -  After the backup is successful, the **backup.json** file is automatically generated in the folder named after the backup date. The file stores job information based on the node type and can be modified before job restoration.
      -  To stop daily backup, click **Stop Daily Backup**.

Restoring Assets
----------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the navigation tree of the DataArts Factory console, choose **Manage Backup**.

#. On the **Manage Restoration** tab, click **Restore Backup**.

   In the **Restore Backup** dialog box, select the storage path of the asset to be restored from the OBS bucket and set the duplicate name policy.

   .. note::

      -  The storage path is the file path generated in :ref:`Backing Up Assets <dataartsstudio_01_0516__en-us_topic_0169685606_section381611818613>`.
      -  Before restoring assets, you can modify the **backup.json** file in the backup path. You can change the connection name (connectionName), database name (database), and cluster name (clusterName).


   .. figure:: /_static/images/en-us_image_0000001322408416.jpg
      :alt: **Figure 3** Restoring assets

      **Figure 3** Restoring assets

#. Click **OK**.
