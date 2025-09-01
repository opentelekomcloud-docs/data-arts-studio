:original_name: dataartsstudio_01_1820.html

.. _dataartsstudio_01_1820:

Review Center
=============

For a workspace in simple mode, you can set the reviewer for the scripts and jobs you submit. In the review center, you can manage applications and configure and maintain reviewers for workspaces.

Constraints
-----------

-  Only the administrator of the current workspace or users with the DARTS Administrator or Tenant Administrator permissions can create, modify, and delete reviewers.
-  The reviewer must be the admin of the current workspace or a user with the DARTS Administrator or Tenant Administrator permission.
-  If the current workspace is in enterprise mode, you can publish tasks for approval, but cannot submit scripts or jobs for approval.
-  If the review function is enabled, the reviewer attribute must be added to the request body of related APIs. For details, see "Job Development APIs" in *DataArts Studio Usage Guide*.
-  You can only set whether to enable the review function and review jobs and scripts on the console.
-  If there are real-time pipeline jobs, review cannot be enabled.
-  If the review function is enabled, the review center is visible to both reviewers and request submitters. If the review function is disabled, the review center is visible only to the administrator of the current workspace or users with the DARTS Administrator or Tenant Administrator permissions.
-  The administrator of the current workspace or users with the DARTS Administrator or Tenant Administrator permissions cannot review their own service tickets.

.. _dataartsstudio_01_1820__section1416816392412:

Review Settings
---------------

Only the administrator of the current workspace or users with the DARTS Administrator or Tenant Administrator permissions can set review options. When the review function is enabled, you can configure review options for jobs or scripts.


.. figure:: /_static/images/en-us_image_0000002234238980.png
   :alt: **Figure 1** Review Settings tab

   **Figure 1** Review Settings tab

#. In the left navigation pane, choose **Review Center**. In the right pane, click the **Review Configuration** tab.
#. Enable **Review**. Only the administrator of the current workspace or users with the DARTS Administrator or Tenant Administrator permissions can enable or disable the review function.

   .. note::

      -  If you enable this function, you must specify a reviewer when submitting a job or script. If you disable this function, no jobs or scripts will need reviewing.
      -  If the current workspace has applications that have not been reviewed, the review function cannot be disabled.

#. You can set **Review Configuration** to any of the following:

   -  **All jobs/scripts**: Review is enabled for all the jobs and scripts in the workspace.

   -  **Custom jobs/scripts**: You need to add the jobs or scripts that need to be reviewed.

      Click the **Jobs** tab and click **Add**. On the displayed page, select the jobs for which you want to enable review. When a job is added, its associated scripts are automatically added. If you select a directory, only existing jobs in the directory are added. If you want to enable review for newly created jobs in the directory, you need to add them. Click **OK**.

      You can delete the jobs that you have added.

      Click the **Scripts** tab and click **Add**. In the displayed dialog box, select the scripts for which you want to enable review. If you select a directory, only existing scripts in the directory are added. If you want to enable review for newly created scripts in the directory, you need to add them. Click **OK**.

      You can delete scripts that you have added.

   -  **Baseline task jobs**: Add jobs to be reviewed from baseline tasks.

      Click the **Jobs** tab and then **Add**. On the displayed page, select the priority jobs of the baseline task as the jobs that require review. Then click **OK**. The upstream jobs of the baseline task also need to be reviewed.

      Click the **Scripts** tab and select the jobs corresponding to the baseline. The scripts associated with the jobs will be displayed on this page.

#. In the **Review Information** area, you can configure the reviewer information on condition that you are the administrator of the current workspace or have the DARTS Administrator or Tenant Administrator permissions.

   a. Click **Manage Reviewer**.
   b. Locate the current workspace and click **Edit** in the **Operation** column.
   c. Next to **Workspace Members**, click **Add**.
   d. Search for and select a member account and select the **admin** role for it.
   e. Click **OK**. The configured reviewer information is automatically displayed.

Review Management
-----------------

-  If you have submitted a review application, you can view the review progress on the **Review Center** page.

   #. In the left navigation pane, choose **Review Center**. In the right pane, click the **My Applications** tab.
   #. Click **View Details** in the **Operation** column to view details about an application.
   #. Click **Withdraw** in the **Operation** column to withdraw an application. You can submit the application again after modifying it.

-  You can view the applications pending your review.

   #. In the left navigation pane, choose **Review Center**. In the right pane, click the **Pending Review** tab. On this page, you can view the applications that need to be reviewed.
   #. Click **Review** in the **Operation** column to view the application details and review the application.
   #. Enter comments and approve or reject the application.

-  You can view the applications that you have reviewed.

   #. In the left navigation pane, choose **Review Center**. In the right pane, click the **Reviewed** tab. On this page, you can view the applications that you have reviewed.
   #. Click **View Details** in the **Operation** column to view the review history and content of an application.
