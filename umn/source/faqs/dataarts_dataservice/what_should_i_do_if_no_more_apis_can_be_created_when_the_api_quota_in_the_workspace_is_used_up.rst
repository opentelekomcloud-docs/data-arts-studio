:original_name: dataartsstudio_03_0237.html

.. _dataartsstudio_03_0237:

What Should I Do If No More APIs Can Be Created When the API Quota in the Workspace Is Used Up?
===============================================================================================

By default, the total API quota for a DataArts DataService Exclusive cluster in a DataArts Studio instance is 5,000 by default. If the API quota for a workspace is not used up, you can allocate more quotas to the current workspace.

#. Log in to the DataArts Studio console.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002269116229.png
      :alt: **Figure 1** Workspace Information dialog box

      **Figure 1** Workspace Information dialog box

#. Locate **API Quota of DataArts DataService Exclusive** and click **Edit** in the **Operation** column to set it. Click **OK** to save the change.

   The allocated quota indicates the quota that can be used in the current workspace. It cannot be less than the used quota or greater than the unallocated quota (total quota minus total allocated quota).


   .. figure:: /_static/images/en-us_image_0000002234236888.png
      :alt: **Figure 2** Setting the allocated quota

      **Figure 2** Setting the allocated quota

#. In the **Workspace Information** dialog box, click **OK**.
