:original_name: dataartsstudio_01_0530.html

.. _dataartsstudio_01_0530:

(Optional) Changing the Job Log Storage Path
============================================

By default, job logs and DLI dirty data are stored in an OBS bucket named **dlf-log-**\ {*project ID*}. You can customize a log storage path. You can configure an OBS bucket globally based on the workspace.

Constraints
-----------

-  This function depends on the OBS service.
-  The OBS path is only supported for OBS buckets and not for parallel file systems.

Prerequisites
-------------

You have changed your account to either of the following:

-  **DARTS** **Administrator** or **Tenant Administrator**
-  **DARTS User**, which is the workspace administrator

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002305437605.png
      :alt: **Figure 1** Workspace Information dialog box

      **Figure 1** Workspace Information dialog box

#. In the **Workspace Information** dialog box, click **Select** next to **Job Log Path** and **Dirty Data Path** to select the path for storing logs and DLI dirty data. You can select a specific directory.


   .. figure:: /_static/images/en-us_image_0000002305404553.png
      :alt: **Figure 2** Changing the path for storing logs and DLI dirty data

      **Figure 2** Changing the path for storing logs and DLI dirty data

#. Click **OK**.
