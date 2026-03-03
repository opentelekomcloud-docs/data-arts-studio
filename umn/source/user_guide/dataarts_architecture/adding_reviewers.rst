:original_name: dataartsstudio_01_0623.html

.. _dataartsstudio_01_0623:

Adding Reviewers
================

In the DataArts Architecture module, all business processes must be approved. Therefore, add reviewers first before conducting any operations. Only the workspace admin has the permissions required to add reviewers.

.. _dataartsstudio_01_0623__en-us_topic_0190201557_section128061611164613:

Adding a Reviewer
-----------------

A reviewer must be a member who has the review permissions in the current workspace. You can edit and add workspace members in **Workspaces** on the DataArts Studio homepage.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. In the navigation pane, choose **Configuration Center**. On the displayed page, click **Reviewers**.

#. On the **Reviewer Management** tab page, click **Add**.

#. Select a reviewer, enter their mobile number and email address, and click **OK**.

   The reviewer must be admins and developers of the current workspace, because only admins and developers have the review permissions of the workspace.

   .. note::

      -  You can only select reviewers from the given list. To enable a user to be available in the given list, add the user as a workspace member in **Workspaces** on the DataArts Studio homepage.
      -  If you select **SMS** or **Email** for **Notification Type**, DataArts Studio automatically creates a topic in SMN after the reviewer is added.

         -  The topic name is in the following format: DataArts_Subject_Reviewer\_\ **Project** **name**\ \_\ **Project** **ID**-dlg_ds\_\ **Reviewer name**.


   .. figure:: /_static/images/en-us_image_0000002234245732.png
      :alt: **Figure 1** Adding a reviewer

      **Figure 1** Adding a reviewer

   .. note::

      You can add multiple reviewers if needed.

Related Operations
------------------

On the DataArts Architecture page, choose **Configuration Center** in the left navigation pane. On the displayed page, click the **Reviewers** tab to manage reviewers.


.. figure:: /_static/images/en-us_image_0000002269205169.png
   :alt: **Figure 2** Reviewer Management page

   **Figure 2** Reviewer Management page

-  **Searching for a reviewer**

   In the upper right corner of the reviewer list, enter the name of the reviewer you are looking for and click |image1|.

-  **Deleting a reviewer**

   In the reviewer list, select the reviewer you want to delete, and click **Delete**.

.. |image1| image:: /_static/images/en-us_image_0000002269125085.png
