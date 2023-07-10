:original_name: dataartsstudio_03_0041.html

.. _dataartsstudio_03_0041:

Why Is There a Large Difference Between Job Execution Time and Start Time of a Job?
===================================================================================

On the **Running History** page, there is a large difference between **Job Execution Time** and **Start Time**, as shown in the figure below. **Job Execution Time** is the time when the job is expected to be executed. **Start Time** is the time when the job starts to be executed.

In Data Development, a maximum of five instances can be concurrently executed in a job. If **Start Time** of a job is later than **Job Execution Time**, the job instances in the subsequent batch will be queued.

If you find that the difference between **Job Execution Time** and **Start Time** becomes large, adjust **Job Execution Time** accordingly.
