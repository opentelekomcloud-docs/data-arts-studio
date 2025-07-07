:original_name: dataartsstudio_01_1903.html

.. _dataartsstudio_01_1903:

Releasing a Job Task
====================

In enterprise mode, when a developer submits a job version, the system generates a job release task. After the developer confirms the release task and the admin, deployer, a user with the DARTS Administrator or Tenant Administrator permission approves the package release request, the modified job is synchronized to the production environment.

.. important::

   -  When the admin selects **Submitted** for **Job Status** during job import, a release task is generated.
   -  When the admin imports jobs in released state, no release task is generated.
   -  When a developer creates a real-time single-task job, a release task is generated for the job, and no release task is generated for the subjobs of the job.

Prerequisites
-------------

You have submitted a version. For details, see :ref:`Submitting a Version <dataartsstudio_01_0902>`.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane, choose **Data Development** > **Task Release**.

#. On the **Tasks** page, the tasks generated for version submission are displayed. You can click **View** in the **Operation** column to view the modifications of a script compared with its previous version. After confirming that the modifications are correct, click **Release** to release the task.

   You can filter release tasks by name or submitter. and perform fuzzy search using a task name.

   .. note::

      -  If you have only the developer permission, the script will be synchronized to the production environment only when the task is approved by the admin or deployer.
      -  After clicking **Release**, set the reviewer. The reviewer must be a workspace admin, deployer, or a user with the DARTS Administrator or Tenant Administrator permission. Set at least one reviewer and do not set yourself as the reviewer. Click **Reviewer Management** to go to the **WorkSpaces** page. Click **Edit** to configure reviewers.
      -  You can release a maximum of 100 tasks at a time. The tasks are released asynchronously. You can view the task release process.
      -  After you click **Release**, the following message is displayed: "Execute jobs in the package immediately after it is released."
      -  You can revoke tasks not to be released as a developer, deployer, or admin.


   .. figure:: /_static/images/en-us_image_0000002305439645.png
      :alt: **Figure 1** Clicking Release

      **Figure 1** Clicking Release

#. After the task is released, you can view the release status of the task on the **Packages** tab page. After approved, the task is released successfully.

   You can filter release tasks by **Applicant**, **Application Time**, **Release At**, or **Released By**, and perform fuzzy search using a package name.


   .. figure:: /_static/images/en-us_image_0000002305406573.png
      :alt: **Figure 2** Viewing the task status

      **Figure 2** Viewing the task status

   .. note::

      You can revoke tasks not to be released as a developer, deployer, or admin.

   After the task is released, you can click **View Details** in the **Operation** column to view the release status and startup status of the task. You can also click **Compare Version** in the **Operation** column to view the differences between different versions of release packages.


   .. figure:: /_static/images/en-us_image_0000002305406569.png
      :alt: **Figure 3** Viewing release package details

      **Figure 3** Viewing release package details
