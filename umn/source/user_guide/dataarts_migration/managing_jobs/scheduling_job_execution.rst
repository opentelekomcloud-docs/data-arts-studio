:original_name: dataartsstudio_01_0082.html

.. _dataartsstudio_01_0082:

Scheduling Job Execution
========================

CDM supports scheduled execution of table/file migration jobs by minute, hour, day, week, and month. This section describes how to configure scheduled job parameters.

.. note::

   When configuring scheduled jobs, do not set the same scheduled time for different jobs. Instead, set different times to avoid exceptions.

Scheduling Job Execution by Minute
----------------------------------

CDM allows jobs to be executed every several minutes. It is recommended that the cycle be at least 5 minutes.

-  **Start Time**: indicates the time when the scheduled configuration takes effect, or the first time when the job is automatically executed.
-  **Cycle (minutes)**: indicates the interval when a job is executed starting from the start time.
-  **End Time**: This parameter is optional. If it is not set, the scheduled job keeps being automatically executed. If it is set, the scheduled job will be automatically stopped at the end time.

Scheduling Job Execution by Hour
--------------------------------

CDM allows jobs to be executed every several hours.

-  **Cycle (hours)**: indicates the interval when a job is automatically executed.

-  **Trigger Time (minute)**: indicates the exact time in each hour when a scheduled task is triggered. The value ranges from 0 to 59. You can set a maximum of 60 values and use commas (,) to separate these values. However, the values must be unique.

   If the trigger time is not within the validity period, the system selects a trigger time closest to the validity period for the scheduled job to be automatically executed at the first time. The following gives an example:

   -  **Start Time**: **1:20:00**
   -  **Cycle (hours)**: **3**
   -  **Trigger Time (minute)**: **10**

-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.

Scheduling Job Execution by Day
-------------------------------

CDM allows jobs to be executed every several days.

-  **Cycle (days)**: indicates the interval when a job is executed starting from the start time.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect, or the first time when the job is automatically executed.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.

Scheduling Job Execution by Week
--------------------------------

CDM allows jobs to be executed every several weeks.

-  **Cycle (weeks)**: indicates the interval when a scheduled job is executed starting from the start time.
-  **Trigger Time (day)**: You can specify the day of each week when the job is automatically executed. One or more days can be selected at a time.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.

Scheduling Job Execution by Month
---------------------------------

CDM allows jobs to be executed every several months.

-  **Cycle (months)**: indicates the interval when a scheduled job is executed starting from the start time.
-  **Trigger Time (day)**: indicates the day of each month when the job is executed. The value ranges from 1 to 31. You can set multiple values and use commas (,) to separate these values. However, the values must be unique.
-  **Validity Period**: includes **Start Time** and **End Time**.

   -  **Start Time**: indicates the time when the scheduled configuration takes effect. The automatic execution time is accurate to hour, minute, and second.
   -  **End Time**: This parameter is optional, which indicates the time when the scheduled job is automatically stopped. If this parameter is not set, the scheduled job keeps being automatically executed.
