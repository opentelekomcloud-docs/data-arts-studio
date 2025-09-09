:original_name: dataartsstudio_03_0061.html

.. _dataartsstudio_03_0061:

What Should I Do If a User Cannot View Workspaces After I Have Assigned the Required Policy to the User?
========================================================================================================

Possible Causes
---------------

If you assign only the DARTS User system role but not a workspace role to a user, the user cannot access a workspace and an error message is displayed.

Solution
--------

Check whether the user has been added to the workspace. If not, perform the following steps to add the user:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate a workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002269116513.png
      :alt: **Figure 1** Workspace Information dialog box

      **Figure 1** Workspace Information dialog box

#. Click **Add** under **Workspace Members**. In the displayed **Add Member** dialog box, select **Add User** or **Add Group**, select a member account from the drop-down list, and select a role for it.


   .. figure:: /_static/images/en-us_image_0000002234077296.png
      :alt: **Figure 2** Adding a member

      **Figure 2** Adding a member

#. Click **OK**. You can view or modify the members and roles in the member list, or remove members from the workspace.
