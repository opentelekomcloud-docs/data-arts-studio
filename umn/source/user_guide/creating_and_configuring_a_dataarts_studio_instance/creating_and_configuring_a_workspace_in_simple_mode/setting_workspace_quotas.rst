:original_name: dataartsstudio_01_0021.html

.. _dataartsstudio_01_0021:

Setting Workspace Quotas
========================

Before using DataArts Studio, you need to set quotas for the current workspace. Currently, only the API quota of DataArts DataService Exclusive can be set. If the used quota of the current workspace exceeds the allocated quota or the total used quota exceeds the total allocated quota, some functions will be unavailable. For example, you cannot create APIs in DataArts DataService Exclusive.

-  Used quota: quota that has been used in the current workspace. It is automatically calculated by the system.
-  Allocated quota: quota allocated to the current workspace by the administrator
-  Total used quota: quota that has been used in the current instance. It is automatically calculated by the system.
-  Total allocated quota: quota that has been allocated to all workspaces in the current instance. It is automatically calculated by the system.
-  Total quota: quota of the current instance. It is a fixed value and cannot be changed.

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

#. Locate **API Quota of DataArts DataService Exclusive** and click **Edit** in the **Operation** column to set it. Click **OK** to save the change.

   The allocated quota indicates the quota that can be used in the current workspace. It cannot be less than the used quota or greater than the unallocated quota (total quota minus total allocated quota).


   .. figure:: /_static/images/en-us_image_0000002269195137.png
      :alt: **Figure 2** Setting the allocated quota

      **Figure 2** Setting the allocated quota

#. In the **Workspace Information** dialog box, click **OK**.
