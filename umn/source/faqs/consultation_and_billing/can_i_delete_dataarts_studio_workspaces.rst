:original_name: dataartsstudio_03_0222.html

.. _dataartsstudio_03_0222:

Can I Delete DataArts Studio Workspaces?
========================================

Yes. The procedure is as follows.

.. note::

   To prevent service loss caused by mis-deletion, the system allows only the **DARTS** **Administrator** or **Tenant Administrator** to delete workspaces. Before deleteing a workspace, ensure that no resource is available in any of the following modules:

   -  Management Center: data connections
   -  DataArts Migration: CDM clusters
   -  DataArts Factory: jobs, job directories, scripts, script directories, and resources

   If any component of a workspace has any service resource, deleting the workspace will fail.

#. Log in to the DataArts Studio console and go to the **Workspaces** page.

#. On the **Workspaces** page, locate the target workspace, click **More** in the **Operation** column, and select **Delete**.

#. In the **Delete Workspace** dialog box, click **OK**.

   If any module has resources, delete the resources as prompted and try again.


   .. figure:: /_static/images/en-us_image_0000002305405869.png
      :alt: **Figure 1** Message indicating that the workspace cannot be deleted

      **Figure 1** Message indicating that the workspace cannot be deleted
