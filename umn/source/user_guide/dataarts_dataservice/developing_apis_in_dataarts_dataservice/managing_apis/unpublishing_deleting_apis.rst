:original_name: dataartsstudio_01_0319.html

.. _dataartsstudio_01_0319:

Unpublishing/Deleting APIs
==========================

Scenario
--------

If you want to stop an API that has been published from providing services, you can unpublish the API. For details, see :ref:`Unpublishing an API <dataartsstudio_01_0319__section10625151911552>`.

-  If you want to continue to use an API that has been unpublished, you need to publish it again. Note that the original authorization information of the API will not be retained once the API is unpublished.
-  If you no longer need the API, you can delete it. For details, see :ref:`Deleting APIs <dataartsstudio_01_0319__section13314153775512>`.

.. note::

   The unpublished API cannot be accessed in the specified time, which may affect the applications or users who are using the API. Ensure that users have been notified of this consequence.

Prerequisites
-------------

-  An API has been created.
-  The API has been published.

.. _dataartsstudio_01_0319__section10625151911552:

Unpublishing an API
-------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. Choose **API Development** > **APIs**.
4. Locate the row that contains the target API, choose **More** > **Unpublish**.
5. In the displayed dialog box, select the time period where the API needs to be unpublished and click **OK**.

   .. note::

      The API unpublishing time must be later than its minimum retention period. Authorized users will be notified of the unpublishing. If all authorized users process the notifications in the review center or unbind the API from their apps, the API will be directly unpublished. Otherwise, the API will be forcibly unpublished when the minimum retention period ends.

.. _dataartsstudio_01_0319__section13314153775512:

Deleting APIs
-------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. Choose **API Development** > **API Catalogs**. On the page displayed, select the API you want to delete and click **Delete**.

   .. note::

      -  Only APIs in an unpublished state can be deleted. APIs in suspended or published state cannot be deleted.
      -  A maximum of 1,000 APIs can be deleted at a time.

4. Click **OK** to delete the API.

Related Operations
------------------

Suspending APIs in batches: On the **APIs** page, select APIs, click **Batch Operation** above the list, and select **Suspend**.


.. figure:: /_static/images/en-us_image_0000002269195549.png
   :alt: **Figure 1** Batch operation

   **Figure 1** Batch operation
