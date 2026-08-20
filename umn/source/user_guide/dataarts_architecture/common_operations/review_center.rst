:original_name: dataartsstudio_01_0619.html

.. _dataartsstudio_01_0619:

Review Center
=============

After the modeling and data processing tasks generated in the development environment are submitted, they are stored in the review center. After the tasks are approved on the **Review Center** page, these tasks are available in the production environment.

Reviewer's Audit Objects
------------------------

If you are a reviewer, use the reviewer account with caution.

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. Choose **Metrics** > **Review Center** in the left navigation bar, click the **Pending Review** tab, find the object to be reviewed in the list, and click **Review** on the right.

   You can also select multiple objects to be reviewed and click **Review** in the upper left corner to review them in batches.


   .. figure:: /_static/images/en-us_image_0000002234238252.png
      :alt: **Figure 1** Pending Review tab page

      **Figure 1** Pending Review tab page

#. On the page displayed, confirm the information and click **Accept**. In the dialog box displayed, enter the review comments and click **OK**.

   If the information is incorrect, click **Reject**. In the dialog box displayed, enter the reasons for rejecting the application and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234078388.png
      :alt: **Figure 2** Review Information area

      **Figure 2** Review Information area

Pending Review, Reviewed, and My Applications Tab Pages
-------------------------------------------------------

-  **Pending Review** tab page

   On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane and click the **Pending Review** tab. On the page displayed, you can view the applications to be reviewed.

-  **Reviewed** tab

   On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane and click the **Reviewed** tab. On the page displayed, you can view the applications that have been approved.

-  **My Applications** tab

   On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane and click the **My Applications** tab. On the page displayed, you can view the applications that you have submitted.

Pending Review
--------------

#. On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane. The **Pending Review** tab page is displayed by default.


   .. figure:: /_static/images/en-us_image_0000002269117581.png
      :alt: **Figure 3** Pending Review tab page

      **Figure 3** Pending Review tab page

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Function Area                     | Description                                                                                                                    |
   +===================================+================================================================================================================================+
   | 1                                 | Batch Review                                                                                                                   |
   |                                   |                                                                                                                                |
   |                                   | a. Select multiple pieces of information to be reviewed.                                                                       |
   |                                   | b. Click **Review Application**.                                                                                               |
   |                                   | c. In the dialog box displayed, enter the valid review comments.                                                               |
   |                                   | d. Click **Accept** to approve the selected targets in batches, or click **Reject** to reject the selected targets in batches. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | 2                                 | Single Review                                                                                                                  |
   |                                   |                                                                                                                                |
   |                                   | a. Click **Review** in the **Operation** column. The page for reviewing the information is displayed.                          |
   |                                   | b. Select the review result (approved or rejected) and enter valid review comments.                                            |
   |                                   | c. Click **OK**.                                                                                                               |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | 3                                 | -  |image1| allows you to specify a time range during which the information to be viewed is displayed.                         |
   |                                   | -  |image2| allows you to query the to-be-reviewed information about objects and creators.                                     |
   |                                   | -  |image3| allows you to set the headers of tables to be reviewed.                                                            |
   |                                   | -  |image4| allows you to refresh the current page.                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

My Applications
---------------

#. On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane.

#. Click **My Applications**.


   .. figure:: /_static/images/en-us_image_0000002516627416.png
      :alt: **Figure 4** My Applications tab page

      **Figure 4** My Applications tab page

   You can perform the following operations:

   -  Click **View** in the **Operation** column to view information about a specified row.
   -  Click **Withdraw** in the **Operation** column to withdraw the application.

Notification
------------

#. On the DataArts Architecture console, choose **Metrics** > **Review Center** in the left navigation pane.

#. On the displayed page, click the **Notifications** tab.


   .. figure:: /_static/images/en-us_image_0000002234078420.png
      :alt: **Figure 5** Notification page

      **Figure 5** Notification page

   You can perform the following operations:

   -  Click **Confirm** in the **Operation** column to confirm a notification. You can also confirm multiple notifications at a time. When a data standard changes, the owner of the object (logical model, physical model, dimension table, fact table, or summary table) associated with the data standard will receive a notification of the change.
   -  You can filter notifications by attribute or query notifications using a keyword.

.. |image1| image:: /_static/images/en-us_image_0000002234078416.png
.. |image2| image:: /_static/images/en-us_image_0000002269117577.png
.. |image3| image:: /_static/images/en-us_image_0000002269117609.png
.. |image4| image:: /_static/images/en-us_image_0000002269117589.png
