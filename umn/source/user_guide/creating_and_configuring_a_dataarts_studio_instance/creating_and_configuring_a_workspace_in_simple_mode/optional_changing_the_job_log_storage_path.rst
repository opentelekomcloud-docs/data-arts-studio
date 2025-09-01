:original_name: dataartsstudio_01_0530.html

.. _dataartsstudio_01_0530:

(Optional) Changing the Job Log Storage Path
============================================

By default, job logs and DLI dirty data are stored in an OBS bucket named **dlf-log-**\ {*project ID*}. You can customize a storage path for logs and one for DLI dirty data. You can also configure an OBS bucket globally based on the workspace.

Notes and Constraints
---------------------

-  This function depends on the OBS service.
-  The OBS path is only supported for OBS buckets and not for parallel file systems.

Prerequisites
-------------

You are using either of the following accounts:

-  **DARTS** **Administrator** or **Tenant Administrator**
-  **DARTS User**, which is the administrator of the current workspace

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002234235668.png
      :alt: **Figure 1** Workspace Information dialog box

      **Figure 1** Workspace Information dialog box

#. In the **Workspace Information** dialog box, click **Select** next to **Job Log Path** and **Dirty Data Path** and select a path.


   .. figure:: /_static/images/en-us_image_0000002234239032.png
      :alt: **Figure 2** Changing the job log path and DLI dirty data path

      **Figure 2** Changing the job log path and DLI dirty data path

#. Click **OK**.
