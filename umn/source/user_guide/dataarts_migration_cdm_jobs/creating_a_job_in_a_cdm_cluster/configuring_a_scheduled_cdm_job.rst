:original_name: dataartsstudio_01_0082.html

.. _dataartsstudio_01_0082:

Configuring a Scheduled CDM Job
===============================

CDM supports scheduled execution of table/file migration jobs by minute, hour, day, week, and month. This section describes how to configure scheduled job parameters.

.. note::

   -  When configuring scheduled jobs, do not set the same scheduled time for different jobs. Instead, set different times to avoid exceptions.

   -  If you use DataArts Studio DataArts Factory to schedule the CDM migration job and configure this parameter, both configurations take effect. To ensure unified service logic and avoid scheduling conflicts, enable job scheduling in DataArts Factory and do not configure a scheduled task for the job in DataArts Migration.

   -  The scheduled execution function uses the Java Quartz timer, which is similar to the Cron expression configuration. It parses the minute, hour, day, and month of the start time, and constructs a cronb expression.

      For example, in the daily scheduling mode where the interval is set to 1 day: if the current time is 2022-10-14 12:00 and the start time is set to 2022-10-14 00:00, the job is executed at 2022-10-15 00:00; if the current time is 2022-10-14 12:00 and the start time is set to 2022-10-14 00:00, the job is executed at 2022-10-15 00:00.

      In the daily scheduling mode where the interval is set to 2 days: if the current time is 2022-10-14 12:00 and the start time is set to 2022-10-14 00:00, the job is executed at 2022-10-16 00:00; if the current time is 2022-10-14 12:00 and the start time is set to 2022-10-14 00:00, the job is executed at 2022-10-16 00:00.

Scheduling Job Execution by Minute
----------------------------------

CDM allows jobs to be executed every several minutes. It is recommended that the cycle be at least 5 minutes.

-  **Start Time**: indicates the time when the scheduled configuration takes effect, or the first time when the job is automatically executed.
-  **Cycle (minutes)**: indicates the interval when a job is executed starting from the start time.
-  **End Time**: This parameter is optional. If it is not set, the scheduled job keeps being automatically executed. If it is set, the scheduled job will be automatically stopped at the end time.


.. figure:: /_static/images/en-us_image_0000002269120405.png
   :alt: **Figure 1** Scheduling job execution by minute

   **Figure 1** Scheduling job execution by minute

For example, the settings shown in the above figure mean that the job will be automatically executed at 00:00 on January 1, 2023 for the first time at a cycle of 30 minutes until 23:59 on December 31, 2023.

Scheduling Job Execution by Hour
--------------------------------

CDM allows jobs to be executed every several hours.

-  **Cycle (hours)**: indicates the interval when a job is automatically executed.

-  **Trigger Time (minute)**: indicates the exact time in each hour when a scheduled task is triggered. The value ranges from 0 to 59. You can set a maximum of 60 values and use commas (,) to separate these values. However, the values must be unique.

   If the trigger time is not within the validity period, the system selects a trigger time closest to the validity period for the scheduled job to be automatically executed at the first time. The following gives an example:

   -  **Start Time**: **1:20**
   -  **Cycle (hours)**: **3**
   -  **Trigger Time (minute)**: **10**

-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.


.. figure:: /_static/images/en-us_image_0000002234241012.png
   :alt: **Figure 2** Scheduling job execution by hour

   **Figure 2** Scheduling job execution by hour

For example, the settings shown in the above figure mean that the job will be automatically executed at 00:10 on January 1, 2023 for the first time, at 00:30 for the second time, and at 00:50 for the third time. It will be executed three times every two hours until 23:59 on December 31, 2023.

Scheduling Job Execution by Day
-------------------------------

CDM allows jobs to be executed every several days.

-  **Cycle (days)**: indicates the interval when a job is executed starting from the start time.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect, or the first time when the job is automatically executed.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.


.. figure:: /_static/images/en-us_image_0000002234241072.png
   :alt: **Figure 3** Scheduling job execution by day

   **Figure 3** Scheduling job execution by day

For example, the settings shown in the above figure mean that the job will be automatically executed at 00:00 on January 1, 2023 for the first time, and will be executed once every three days. The configuration is valid permanently.

Scheduling Job Execution by Week
--------------------------------

CDM allows jobs to be executed every several weeks.

-  **Cycle (weeks)**: indicates the interval when a scheduled job is executed starting from the start time.
-  **Trigger Time (day)**: You can specify the day of each week when the job is automatically executed. One or more days can be selected at a time.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.


.. figure:: /_static/images/en-us_image_0000002234241004.png
   :alt: **Figure 4** Scheduling job execution by week

   **Figure 4** Scheduling job execution by week

For example, the settings shown in the above figure mean that the job will be automatically executed at 00:00 every Tuesday, Saturday, and Sunday every two weeks starting from 00:00 on January 1, 2023 until 23:59 on December 31, 2023.

Scheduling Job Execution by Month
---------------------------------

CDM allows jobs to be executed every several months.

-  **Cycle (months)**: indicates the interval when a scheduled job is executed starting from the start time.
-  **Trigger Time (day)**: indicates the day of each month when the job is executed. The value ranges from 1 to 31. You can set multiple values and use commas (,) to separate these values. However, the values must be unique.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect. The automatic execution time is accurate to hour, minute, and second.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.


.. figure:: /_static/images/en-us_image_0000002234081196.png
   :alt: **Figure 5** Scheduling job execution by month

   **Figure 5** Scheduling job execution by month

For example, the settings shown in the above figure mean that the job will be automatically executed at 00:00 on the 5th and 25th days of each month starting from 00:00 on January 1, 2023 until 23:59 on December 31, 2023.
