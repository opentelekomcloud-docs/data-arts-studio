:original_name: dataartsstudio_01_0580.html

.. _dataartsstudio_01_0580:

Job Dependency
==============

You can set a job that meets the scheduling period conditions as the dependency jobs for a job that is scheduled periodically. For details about how to set a dependency job, see **DataArts Factory** > **Job Development** > **Setting Up Scheduling for a Job** in *DataArts Studio User Guide*.

For example, you can set a dependency job (job B) for job A which is scheduled periodically. In this case, job A will be executed only when all the instances of job B are executed successfully within a specified period.

.. note::

   -  The specified period is calculated as follows (see :ref:`How a Job Runs After a Dependency Job Is Set for It <dataartsstudio_01_0580__section1995195213720>` for details):

      -  Same-cycle dependency: If the scheduling periods of the two jobs are accurate to the same level (for example, minute, hour, or day), the specified period is **(Execution time of job A - Recurrence of job A, Execution time of job A]**.
      -  Cross-cycle dependency: If the scheduling periods of the two jobs are accurate to different levels, the specified period is **[Natural start time of the previous recurrence of job A, Natural start time of the current recurrence of job A)**.

   -  Parameter **Policy for Current job If Dependency job Fails** determines whether job A will check the status of job B's instances.

      -  If this parameter is set to **Suspend** or **Terminate**, job A will be suspended or terminated if instances of job B fail during a specified time period.
      -  If this parameter is set to **Continue**, job A will be executed only if all the instances of job B are executed (regardless of whether the execution is successful or not).


.. figure:: /_static/images/en-us_image_0000001373088265.png
   :alt: **Figure 1** Job dependency attributes

   **Figure 1** Job dependency attributes

This section describes :ref:`how to set the conditions of a dependency job <dataartsstudio_01_0580__section2277112401713>` and :ref:`how a job runs after a dependency job is set for it <dataartsstudio_01_0580__section1995195213720>`.

.. _dataartsstudio_01_0580__section2277112401713:

Setting Conditions of a Dependency Job
--------------------------------------

The recurrence of a periodically scheduled job can be minute, hour, day, week, or month. If job A and job B are both periodically scheduled jobs, and you want to set job B as the dependency job of job A, their recurrences must meet the following requirements:

-  The recurrence of job A cannot be shorter than that of job B. For example, if both job A and job B are scheduled by minute or hour and the interval of job A is shorter than that of job B, then job B cannot be set as the dependency job of job A. If job A is scheduled by minute and job B is scheduled by hour, job B cannot be set as the dependency job of job A.
-  The recurrence of neither job A nor job B can be week. For example, if the recurrence of job A or job B is week, job B cannot be set as the dependency job of job A.
-  A job whose recurrence is month can depend only on a job whose recurrence is day. For example, if the recurrence of job A is month, job B can be set as the dependency job of job A only if job B's recurrence is day.

:ref:`Figure 2 <dataartsstudio_01_0580__fig14790350131320>` shows the requirements of the recurrences of the jobs that can function as the dependency jobs of other jobs

.. _dataartsstudio_01_0580__fig14790350131320:

.. figure:: /_static/images/en-us_image_0000001373169069.png
   :alt: **Figure 2** Job dependency

   **Figure 2** Job dependency

.. _dataartsstudio_01_0580__section1995195213720:

How a Job Runs After a Dependency Job Is Set for It
---------------------------------------------------

It varies depending on whether a job and its dependency job has the same recurrence. In this example, assume that the **Policy for Current job If Dependency job Fails** parameter is set to **Continue**, and job A does not check the running statuses of job B's instances. If this parameter is set to **Suspend** or **Terminate**, job A will also check whether there are failed instances in job B.

-  **Same-cycle dependency**: Job A and its dependency job B have the same recurrence, for example, minute, hour, or day.

   After job B is set as the dependency job of job A, job A checks whether instances of job B are running within a specified time range **(Execution time of job A - Recurrence of job A, Execution time of job A)**. Job A will be executed only if all the instances of job B are executed.

   Example 1: Job A depends on job B and they are both scheduled by minute. Job A starts at 10:00 and the interval is 20 minutes. Job B starts at 10:00 and the interval is 10 minutes. The following table lists how the two jobs run.

   .. table:: **Table 1** Example 1: dependency between jobs with the same recurrence

      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+
      | Time Point | Job B (Starting at 10:00 and Scheduled Every 10 Minutes) | Job A (Starting at 10:00 and Scheduled Every 20 Minutes)                            |
      +============+==========================================================+=====================================================================================+
      | 10:00      | Executed                                                 | Executed after job B's instances are executed in the **(09:40, 10:00]** time period |
      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+
      | 10:10      | Executed                                                 | ``-``                                                                               |
      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+
      | 10:20      | Executed                                                 | Executed after job B's instances are executed in the **(10:00, 10:20]** time period |
      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+
      | 10:30      | Executed                                                 | ``-``                                                                               |
      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+
      | ...        | ...                                                      | ...                                                                                 |
      +------------+----------------------------------------------------------+-------------------------------------------------------------------------------------+

   Example 2: Job A depends on job B and they are both scheduled by day. Job A starts at 09:00 on August 1, and job B starts at 10:00 on August 1. The following table lists how the two jobs run.

   .. table:: **Table 2** Example 2: dependency between jobs with the same recurrence

      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | Time Point        | Job B (Starting at 10:00 on August 1 and Scheduled by Day) | Job A (Starting at 09:00 on August 1 and Scheduled by Day)                                                   |
      +===================+============================================================+==============================================================================================================+
      | 09:00 on August 1 | ``-``                                                      | Not executed if no instance of job B is running in the **(09:00 on July 31, 09:00 on August 1]** time period |
      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | 10:00 on August 1 | Executed                                                   | ``-``                                                                                                        |
      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | 09:00 on August 2 | ``-``                                                      | Executed after job B's instances are executed in the **(09:00 on August 1, 09:00 on August 2]** time period  |
      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | 10:00 on August 2 | Executed                                                   | ``-``                                                                                                        |
      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | ...               | ...                                                        | ...                                                                                                          |
      +-------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

-  **Cross-cycle dependency**: Job A and its dependency job B have different recurrences.

   After job B is set as the dependent job of job A, job A checks whether any instance of job B is running in the time range **(Natural start time of the previous recurrence of job A, Natural start time of the current recurrence of job A)**. Job A will be executed only after all the instances of job B are executed.

   .. note::

      The natural start time of a recurrence is defined as follows:

      -  If the recurrence is hour, the **natural start time of the previous recurrence** is 00:00 of the previous hour, and the **natural start time of the current recurrence** is 00:00 of the current hour.
      -  If the recurrence is day, the **natural start time of the previous recurrence** is 00:00:00 of the previous day, and the **natural start time of the current recurrence** is 00:00:00 of the current day.
      -  If the recurrence is month, the **natural start time of the previous recurrence** is 00:00:00 on 1st of the previous month, and the **natural start time of the current recurrence** is 00:00:00 on 1st of the current month.

   Example 3: Job A depends on job B. Job A is scheduled by day, and job B is scheduled by hour. Job A is executed at 02:00 every day. Job B starts at 00:00 and is executed at an interval of 10 hours. The following table lists how the two jobs run.

   .. table:: **Table 3** Example 3: dependency between jobs with different recurrences

      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | Time Point              | Job B (Starting at 00:00 at an Interval of 10 hours and Scheduled by Hour) | Job A (Scheduled at 02:00 Every Day)                                                                          |
      +=========================+============================================================================+===============================================================================================================+
      | 00:00 on the first day  | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 02:00 on the first day  | ``-``                                                                      | Not executed if no instance of job B is running in the **[00:00:00 on day 0, 00:00:00 on day 1)** time period |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 10:00 on the first day  | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 20:00 on the first day  | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 00:00 on the second day | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 02:00 on the second day | ``-``                                                                      | Executed if instances of job B are executed in the **[00:00:00 on day 1, 00:00:00 on day 2)** time period     |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 10:00 on the second day | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | 20:00 on the second day | Executed                                                                   | ``-``                                                                                                         |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
      | ...                     | ...                                                                        | ...                                                                                                           |
      +-------------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

   Example 4: Job A depends on job B. Job A is scheduled by month, and job B is scheduled by day. Job A is executed at 02:00 on the first and second days of each month. Job B is executed at 00:00 on August 1. The following table lists how the two jobs run.

   .. table:: **Table 4** Example 4: dependency between jobs with different recurrences

      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Time Point           | Job B (Scheduled by Day and Executed at 00:00 on August 1) | Job A (Scheduled by Month and Executed at 02:00 on the First and Second Days of Each Month)                        |
      +======================+============================================================+====================================================================================================================+
      | 00:00 on August 1    | Executed                                                   | ``-``                                                                                                              |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 02:00 on August 1    | ``-``                                                      | Not executed if no instance of job B is running in the **[00:00:00 on July 1, 00:00:00 on August 1)** time period  |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 00:00 on August 2    | Executed                                                   | ``-``                                                                                                              |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 02:00 on August 2    | ``-``                                                      | Not executed if no instance of job B is running in the **[00:00:00 on July 1, 00:00:00 on August 1)** time period  |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | ...                  | ``-``                                                      | ...                                                                                                                |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 00:00 on September 1 | Executed                                                   | ``-``                                                                                                              |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 02:00 on September 1 | ``-``                                                      | Executed if instances of job B are executed in the **[00:00:00 on August 1, 00:00:00 on September 1)** time period |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 00:00 on September 2 | Executed                                                   | ``-``                                                                                                              |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | 02:00 on September 2 | ``-``                                                      | Executed if instances of job B are executed in the **[00:00:00 on August 1, 00:00:00 on September 1)** time period |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | ...                  | ...                                                        | ...                                                                                                                |
      +----------------------+------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
