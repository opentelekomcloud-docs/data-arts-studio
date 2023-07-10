:original_name: dataartsstudio_03_0116.html

.. _dataartsstudio_03_0116:

What Should I Do If a Job Fails to Be Executed After Being Submitted for Scheduling and an Error Displayed: Depend Job [XXX] Is Not Running Or Pause?
=====================================================================================================================================================

Symptom
-------

After a job is submitted for scheduling, the job fails to be executed and the following error is displayed "depend job [XXX] is not running or pause".

Cause Analysis
--------------

The upstream dependency job is not in the running state.

Solutions
---------

Check the upstream dependency jobs. If the upstream dependency jobs are not in the running state, re-schedule these jobs.
