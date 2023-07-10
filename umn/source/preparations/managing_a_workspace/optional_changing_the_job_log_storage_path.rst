:original_name: dataartsstudio_01_0530.html

.. _dataartsstudio_01_0530:

(Optional) Changing the Job Log Storage Path
============================================

By default, job logs and Data Lake Insight (DLI) dirty data are stored in an Object Storage Service (OBS) bucket named **dlf-log-**\ {*Project ID*}. You can customize a log storage path. DataArts Factory allows you to configure an OBS bucket globally based on the workspace.

Constraints
-----------

This function depends on the OBS service.

Prerequisites
-------------

To change the job log storage path, either of the following conditions must be met:

-  You have administrator rights.
-  You have been assigned the **DAYU User** policy and you are the admin of the current workspace.

Procedure
---------

#. Log in to the DataArts Studio console using the **DAYU** **Administrator** or administrator account.
#. Click the **Workspaces** tab.

3. Click **Edit** in the **Operation** column.

4. On the **Workspace Information** page displayed, click **Edit** next to the workspace information.

   Click the **Select** button next to **OBS Bucket for Job Logs** to reselect a path.


   .. figure:: /_static/images/en-us_image_0000001373288913.png
      :alt: **Figure 1** Changing the log path

      **Figure 1** Changing the log path

5. Click **Save**.
