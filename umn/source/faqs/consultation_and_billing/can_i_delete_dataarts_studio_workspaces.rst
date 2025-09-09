:original_name: dataartsstudio_03_0222.html

.. _dataartsstudio_03_0222:

Can I Delete DataArts Studio Workspaces?
========================================

Yes. The procedure is as follows.

.. note::

   Mis-deletion may result in service loss. To delete a workspace, you must use the **DARTS** **Administrator** or **Tenant Administrator** account and ensure that the workspace does not contain any of the following resources:

   -  Management Center: data connections
   -  DataArts Migration: CDM clusters
   -  DataArts Factory: jobs, job directories, scripts, script directories, and resources

   If any module has resources, a message is displayed, indicating that the workspace cannot be deleted.

#. Log in to the DataArts Studio console and go to the **Workspaces** page.

#. On the **Workspaces** page, locate the target workspace, click **More** in the **Operation** column, and select **Delete**.

#. In the **Delete Workspace** dialog box, click **OK**.

   If any module has resources, delete the resources as prompted and try again.


   .. figure:: /_static/images/en-us_image_0000002234076600.png
      :alt: **Figure 1** Message indicating that the workspace cannot be deleted

      **Figure 1** Message indicating that the workspace cannot be deleted
