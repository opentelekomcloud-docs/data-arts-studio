:original_name: dataartsstudio_03_0111.html

.. _dataartsstudio_03_0111:

Why Is There No Job Running Scheduling Record After Daily Scheduling Is Configured for the Job?
===============================================================================================

Symptom
-------

Daily scheduling is configured for the job, but there is no job scheduling record in the instance.

Cause Analysis
--------------

Cause 1: Check whether the job scheduling is started. If not, the job will not be scheduled.

Cause 2: The instance query time range is too long. If a dependent or self-dependent job is configured, check whether the historical job instance is waiting for running due to the dependency failure. As a result, no new job instance is generated.

Solutions
---------

Configure Job exception alarms and instance timeout duration. When the waiting time exceeds the instance timeout duration, the system sends an alarm notification.
