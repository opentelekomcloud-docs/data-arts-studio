:original_name: dataartsstudio_01_0614.html

.. _dataartsstudio_01_0614:

Creating Time Filters
=====================

Atomic metrics are standard definitions for computing logic. Time filters are standard definitions for conditional limits. To ensure that all statistical metrics are unified, standard, and unambiguous, time filters must be unique within a business domain and each filter can belong to a single source logic table. The computing logic is defined based on the fields of the source logic table model. A time filter may come from multiple logic tables that belong to different data domains. Therefore, a time filter may belong to multiple data domains as well.

.. _dataartsstudio_01_0614__en-us_topic_0169427442_section12931330310:

Creating and Publishing a Time Filter
-------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. (Optional) On the DataArts Architecture console, choose **Configuration Center** in the left navigation pane, click the **Functions** tab, and determine whether to enable **Time-Limited Generation Using Dynamic Expressions** (disabled by default).


   .. figure:: /_static/images/en-us_image_0000002234237744.png
      :alt: **Figure 1** Functions

      **Figure 1** Functions

#. On the DataArts Architecture page, choose **Metrics** > **Technical Metrics** in the left navigation pane. On the displayed page, click the **Time Filters** tab.

#. On the **Time Filters** tab page, click **Create**.

#. On the **Create Time Filter** page, set the parameters described in :ref:`Table 1 <dataartsstudio_01_0614__table18469131994611>` and click **Publish**.


   .. figure:: /_static/images/en-us_image_0000002269202037.png
      :alt: **Figure 2** Creating a time filter

      **Figure 2** Creating a time filter

   .. _dataartsstudio_01_0614__table18469131994611:

   .. table:: **Table 1** Parameters for creating a time filter

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================================================================================================+
      | \*Filter Name                     | Newline characters and the following characters are not allowed: \\ < > % " ' ;                                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Filter English name             | Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Time Settings                   | You can select **Year**, **Month**, **Day**, **Hour**, or **Minute**, and then select **Quick option** or **Custom** to set the time condition.                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                      |
      |                                   | If you select **Custom**, **+** and **-** form a time range, in which **+** indicates a later time and **-** indicates an earlier time. For example, if you want to set a time range from the past year to the next three years, set this parameter to **-1 to +3** or **+3 to -1**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the time filter to create. Up to 490 characters are supported.                                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the displayed dialog box, select a reviewer and click **OK** to submit an application.

   .. note::

      If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the request is approved, the status changes to **Published**.

      If you select multiple reviewers, the status changes to **Published** only after all reviewers have approved the publishing request. If any reviewer rejects the request, the status is **Rejected**.

#. Wait for the reviewer to approve the application.

   After the application is approved, the time filter is created.

Managing a Time Filter
----------------------

#. On the DataArts Architecture page, choose **Metrics** > **Technical Metrics** in the left navigation pane. On the displayed page, click the **Time Filters** tab.


   .. figure:: /_static/images/en-us_image_0000002234082764.png
      :alt: **Figure 3** Time Filters tab page

      **Figure 3** Time Filters tab page

#. Manage your time filters as required. Refer to the following table for details.

   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | Operation            | Helpful Link                                                                                                     |
   +======================+==================================================================================================================+
   | Create               | :ref:`Creating and Publishing a Time Filter <dataartsstudio_01_0614__en-us_topic_0169427442_section12931330310>` |
   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | Edit                 | :ref:`3 <dataartsstudio_01_0614__li367549172317>`                                                                |
   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | Publish              | :ref:`4 <dataartsstudio_01_0614__li186715497233>`                                                                |
   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | View Publish History | :ref:`5 <dataartsstudio_01_0614__li84726392483>`                                                                 |
   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | Suspend              | :ref:`6 <dataartsstudio_01_0614__li1767449102313>`                                                               |
   +----------------------+------------------------------------------------------------------------------------------------------------------+
   | Delete               | :ref:`7 <dataartsstudio_01_0614__li76712493237>`                                                                 |
   +----------------------+------------------------------------------------------------------------------------------------------------------+

#. .. _dataartsstudio_01_0614__li367549172317:

   Edit a time filter.

   a. Click **Edit** to the right of the target time filter.
   b. On the page displayed, edit the time filter as required.
   c. Click **Save** to save the time filter information, or click **Publish** to publish the edited time filter.

#. .. _dataartsstudio_01_0614__li186715497233:

   Publish a time filter.

   a. Click **Publish** to the right of the target time filter.
   b. In the **Submit for Publication** dialog box displayed, select a reviewer from the drop-down list box.
   c. Click **OK**.

#. .. _dataartsstudio_01_0614__li84726392483:

   View the publish history.

   a. Select the target time filter in the list and choose **More** > **View History**.
   b. On the page displayed, you can view the publish history and version comparison information of the time filter.

#. .. _dataartsstudio_01_0614__li1767449102313:

   Suspend a time filter.

   a. Select the target time filter in the list and choose **More** > **Suspend**.
   b. In the **Submit for Suspension** dialog box displayed, select a reviewer from the drop-down list box.
   c. Click **OK**.

      .. note::

         Time filters cannot be suspended or deleted if they are referenced by any derivative metrics.

#. .. _dataartsstudio_01_0614__li76712493237:

   Delete a time filter.

   a. Select the target time filter and click **Delete** above the list.
   b. In the dialog box displayed, confirm the information and click **Yes**.
