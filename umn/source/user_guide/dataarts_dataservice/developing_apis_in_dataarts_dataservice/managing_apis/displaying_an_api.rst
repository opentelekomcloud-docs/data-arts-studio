:original_name: dataartsstudio_01_0323.html

.. _dataartsstudio_01_0323:

Displaying an API
=================

Scenario
--------

If you want to change the visibility scope of an API in the service catalog, you can use the **Display** function or set the **Display Scope** parameter for the API.

Prerequisites
-------------

An API has been created.

Changing the API Visibility Scope Using the **Display** Function
----------------------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Development** > **API Catalogs** or **API Development** > **APIs**. Locate an API, click **More** in the **Operation** column, and select **Display**.

4. In the displayed dialog box, click **Add**, enter a project ID, and click **OK** to make the API visible to users in the project.

   To obtain the project ID, perform the following steps:

   a. Register with and log in to the management console.
   b. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
   c. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.


   .. figure:: /_static/images/en-us_image_0000002269204269.png
      :alt: **Figure 1** Display API

      **Figure 1** Display API

Changing the API Visibility Scope by Setting the **Display Scope** Parameter
----------------------------------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. Choose **API Development** > **API Catalogs** or **API Development** > **APIs**. Locate an API and click **Edit** in the **Operation** column. An API cannot be edited if it is in the pending review or execution state after published, unpublished, suspended, or resumed.
4. On the **Configure Basic Details** page, select a value for the **Display Scope** parameter. The value can be **Current workspace's APIs**, **Current project's APIs**, or **Current tenant's APIs**. Then save the modification.
5. Restore or publish the API again to change the visibility scope of the API in the service catalog.
