:original_name: dataartsstudio_01_5103.html

.. _dataartsstudio_01_5103:

Deployer Operations
===================

-  The deployer reviews the tasks to be released. This section describes related operations.
-  The deployer reviews the release tasks submitted by the developer. Modified jobs can be synchronized to the production environment only after the corresponding release tasks are approved.

In enterprise mode, when a developer submits a script or job version, the system generates a release task. After the developer confirms the release and the deployer approves the release request, the modified job is synchronized to the production environment.

Prerequisites
-------------

The developer has completed the operations in :ref:`Releasing a Script Task <dataartsstudio_01_1902>` or :ref:`Releasing a Job Task <dataartsstudio_01_1903>`.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane, choose **Data Development** > **Task Release**.

#. Click the **Packages** tab. You can click **View Details** in the **Operation** column to view the changes of the task compared with its previous version.

   -  If there is any issue, click **Revoke** to reject the release task. After the developer modifies and submits the release task again, you can review it again.
   -  After confirming that the release task has no remaining issue, click **Release** to approve the task.


   .. figure:: /_static/images/en-us_image_0000002305406837.png
      :alt: **Figure 1** Reviewing and releasing a task

      **Figure 1** Reviewing and releasing a task

#. After the task is released, you can view its status. The developer's modification is synchronized to the production environment.


   .. figure:: /_static/images/en-us_image_0000002305439889.png
      :alt: **Figure 2** Viewing the task status

      **Figure 2** Viewing the task status
