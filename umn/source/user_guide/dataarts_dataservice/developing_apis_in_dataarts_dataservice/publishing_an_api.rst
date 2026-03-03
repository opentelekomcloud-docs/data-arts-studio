:original_name: dataartsstudio_01_0308.html

.. _dataartsstudio_01_0308:

Publishing an API
=================

This section describes how to publish APIs in DataArts DataService.

Scenario
--------

For the sake of security, APIs generated in DataArts DataService must be published before they can provide services.

Prerequisites
-------------

An API has been debugged.

Notes and Constraints
---------------------

If one or more users publish APIs to the same exclusive cluster at the same time, the system displays message "Operation in progress. Try again later."

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. In the navigation pane, choose **API Development** > **APIs**. Locate an API, click **More** in the **Operation** column, and select **Publish**.

4. In the displayed dialog box, select the target cluster.


   .. figure:: /_static/images/en-us_image_0000002234244312.png
      :alt: **Figure 1** Selecting a cluster

      **Figure 1** Selecting a cluster

   -  In DataArts DataService Exclusive, the API is published to a DataArts DataService Exclusive cluster by default and can be published by version. After the API is published, it can be called through the intranet or Internet.

5. APIs must be reviewed and approved before they can be published. APIs are reviewed in the following way:

   -  An API publisher who does not have the reviewer permission must submit the API to the reviewer for review.
   -  An API publisher who has the reviewer permission can publish an API without review or approval.

   An API submitted by a non-reviewer is published after it is approved by the reviewer.

   .. note::

      The data connection of an API in the pending review state cannot be changed. It can be changed only when the application is rejected by a user with the workspace administrator role.

      An admin, developer, or operator can be a reviewer. A viewer cannot be a reviewer.

      Regardless of whether they are added as reviewers, users with the admin role of the workspace have the reviewer permissions by default.

6. After the API is published, you can go to the **Service Catalogs** page to view the API information.

Related Operations
------------------

Publishing APIs in batches: On the **APIs** page, select APIs, click **Batch Operation** above the list, and select **Publish**.


.. figure:: /_static/images/en-us_image_0000002269195549.png
   :alt: **Figure 2** Batch operation

   **Figure 2** Batch operation
