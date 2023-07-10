:original_name: dataartsstudio_03_0063.html

.. _dataartsstudio_03_0063:

Why Does a Job Scheduled by Month Start Running Before the Job Scheduled by Day Is Complete?
============================================================================================

Jobs scheduled by month depend on jobs scheduled by day. Why does a job scheduled by month start running before the job scheduled by day is complete?


.. figure:: /_static/images/en-us_image_0000001373289613.png
   :alt: **Figure 1** Viewing the job scheduling period and dependency attributes

   **Figure 1** Viewing the job scheduling period and dependency attributes

Although jobs scheduled by month depend on jobs scheduled by day, whether jobs scheduled by month in the current month are executed depends on whether all jobs scheduled by day in the previous month are complete, not the jobs scheduled by day in the current month.

For example, whether the monthly scheduled jobs run in November depends on whether the daily scheduled jobs were complete in October.
