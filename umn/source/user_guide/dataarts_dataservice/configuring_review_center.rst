:original_name: dataartsstudio_01_0312.html

.. _dataartsstudio_01_0312:

Configuring Review Center
=========================

On the **Review Center** page, API developers and callers can review the requests for operations such as publishing APIs.

APIs must be reviewed and approved before they can be published. APIs are reviewed in the following way:

-  An API publisher who does not have the reviewer permission must submit the API to the reviewer for review.
-  An API publisher who has the reviewer permission can publish an API without review or approval.

Requests can also be withdrawn on the **Review Center** page.

.. note::

   An admin, developer, or operator can be a reviewer. A viewer cannot be a reviewer.

   Regardless of whether they are added as reviewers, users with the admin role of the workspace have the reviewer permissions by default.

Managing a Reviewer
-------------------

You can create and delete reviewers. The following procedure describes how to create a reviewer.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

3. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

4. Choose **Operation Management** > **Review Center** from the left navigation pane. On the page displayed, choose **Reviewer Management** and click **Add**.


   .. figure:: /_static/images/en-us_image_0000002269118965.png
      :alt: **Figure 1** Adding reviewers

      **Figure 1** Adding reviewers

5. Select a reviewer (workspace member), enter a correct phone number and email address, and click **OK**.

6. Add more reviewers, if required.

Reviewing API Applications
--------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **Operation Management** > **Review Center** in the left navigation bar and click the **Pending Review** tab.

4. Locate a task and click **Review** in the **Operation** column, or click an API name to access the API details page to review the API application. You can also select multiple tasks and click **Batch Review** above the task list to review them. APIs take effect immediately upon approval.


   .. figure:: /_static/images/en-us_image_0000002234244412.png
      :alt: **Figure 2** Review

      **Figure 2** Review

Canceling an API Application
----------------------------

DataArts DataService provides the function of canceling applications to be reviewed. You can cancel applications to be reviewed on the **Applications** tab page on the **Review Center** page.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. Choose **Operations Management** > **Review Center** in the left navigation pane and click the **Applications** tab.
4. Locate the row that contains the API to be canceled, and click **Cancel** in the **Operation** column.
