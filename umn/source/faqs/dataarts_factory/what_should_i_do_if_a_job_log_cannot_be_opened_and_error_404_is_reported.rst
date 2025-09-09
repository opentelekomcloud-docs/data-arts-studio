:original_name: dataartsstudio_03_0050.html

.. _dataartsstudio_03_0050:

What Should I Do If a Job Log Cannot Be Opened and Error 404 Is Reported?
=========================================================================

Possible Causes
---------------

You do not have the required permissions.

Solution
--------

Job logs are stored in OBS buckets. You must configure the bucket directory for storing job logs in the workspace and check whether your account has the OBS read permission by checking the OBS permission and OBS bucket policy in IAM.

.. note::

   The OBS path is only supported for OBS buckets and not for parallel file systems.

You are using either of the following accounts:

-  **DARTS** **Administrator** or **Tenant Administrator**
-  **DARTS User**, which is the administrator of the current workspace

To configure the bucket directory for storing job logs, perform the following steps:

#. Log in to the DataArts Studio console.

#. On the **Workspaces** page, locate a workspace and click **Edit** in the **Operation** column.

#. In the displayed **Workspace Information** dialog box, click the **Select** button next to **Job Log Path** and select a path.


   .. figure:: /_static/images/en-us_image_0000002234236924.png
      :alt: **Figure 1** Changing the job log path

      **Figure 1** Changing the job log path

#. Click **OK**.

.. note::

   When you create a job, a bucket named **dlf-log-{projectID}** will be created by default. If the bucket exists, you do not need to create a bucket again.
