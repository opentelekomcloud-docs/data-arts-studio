:original_name: dataartsstudio_01_1283.html

.. _dataartsstudio_01_1283:

Configuring a Scheduling Calendar
=================================

You can configure a scheduling calendar and specify the working days for scheduling a job.

Constraints
-----------

This function is available for batch processing jobs but not for real-time processing jobs.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane, choose **Configuration** > **Configure**.

#. Choose **Scheduling Calendars**.

#. Click **Add**. The **Create Scheduling Calendar** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000002270790404.png
      :alt: **Figure 1** Create Scheduling Calendar dialog box

      **Figure 1** Create Scheduling Calendar dialog box

#. Set parameters for the scheduling calendar.

   Set **Calendar Name**, **Owner**, **Default Working Days**, and **Description**.

   You can select **Mon to Fri** or **Mon to Sun** for **Default Working Days**. By default, **Mon to Fri** is selected.

#. Click **OK**.

   After creating the calendar, you can use it for jobs. Go to the DataArts Factory console, open a job, click **Scheduling Setup**, select **Run periodically** for **Scheduling Type**, and select the calendar you have created for **Scheduling Calendar**.

More Operations
---------------

-  Modify a calendar: Click **Modify** in the **Operation** column.

   -  **Batch Select**: Select all Mondays to Fridays of the current month.

   -  **Invert Selection**: Select all non-working days.

   -  **Clear**: Clear selected working days.


      .. figure:: /_static/images/en-us_image_0000002270790400.png
         :alt: **Figure 2** Modifying a scheduling calendar

         **Figure 2** Modifying a scheduling calendar

-  Delete a calendar: Click **Delete** in the **Operation** column.
