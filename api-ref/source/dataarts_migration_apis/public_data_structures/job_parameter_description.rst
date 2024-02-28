:original_name: job_parameter.html

.. _job_parameter:

Job Parameter Description
=========================

When you create a job in a specified cluster by following the instructions in :ref:`Creating a Job in a Specified Cluster <createjob_0>` or create and execute a job in a random cluster by following the instructions in :ref:`Creating and Executing a Job in a Random Cluster <createandstartrandomclusterjob_0>`, the **driver-config-values** parameter specifies the job configuration, which includes the following functions:

-  **Retry upon Failure**: If a job fails to be executed, you can choose whether to automatically restart the job.
-  **Job Group**: CDM allows you to group jobs. You can filter, delete, start, or export jobs by group.
-  **Schedule Execution**: Specify whether to execute scheduled jobs.
-  **Concurrent Extractors**: Enter the number of concurrent extractors.
-  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link.
-  **Delete Job After Completion**: Specify whether to delete a job after the job is executed.

Sample JSON File
----------------

.. code-block::

   "driver-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "throttlingConfig.numExtractors",
                   "value": "1"
                 },
                 {
                   "name": "throttlingConfig.numLoaders",
                   "value": "1"
                 },
                 {
                   "name": "throttlingConfig.recordDirtyData",
                   "value": "false"
                 }
               ],
               "name": "throttlingConfig"
             },
             {
               "inputs": [],
               "name": "jarConfig"
             },
             {
               "inputs": [
                 {
                   "name": "schedulerConfig.isSchedulerJob",
                   "value": "false"
                 },
                 {
                   "name": "schedulerConfig.disposableType",
                   "value": "NONE"
                 }
               ],
               "name": "schedulerConfig"
             },
             {
               "inputs": [],
               "name": "transformConfig"
             },
             {
               "inputs": [
                 {
                   "name": "retryJobConfig.retryJobType",
                   "value": "NONE"
                 }
               ],
               "name": "retryJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                           | Mandatory       | Type            | Description                                                                                                                                                                                                                                         |
+=====================================+=================+=================+=====================================================================================================================================================================================================================================================+
| throttlingConfig.numExtractors      | No              | Integer         | Maximum number of concurrent extraction jobs. For example, **20**.                                                                                                                                                                                  |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| groupJobConfig.groupName            | No              | Enumeration     | Group to which a job belongs. The default group is **DEFAULT**.                                                                                                                                                                                     |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.numLoaders         | No              | Integer         | This parameter is available only when HBase or Hive serves as the destination data source.                                                                                                                                                          |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | Maximum number of loading jobs. For example, **5**.                                                                                                                                                                                                 |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.recordDirtyData    | No              | Boolean         | Whether to write dirty data. For example, **true**.                                                                                                                                                                                                 |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.writeToLink        | No              | String          | Link to which dirty data is written. Currently, dirty data can be written only to OBS or HDFS. For example, **obslink**.                                                                                                                            |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.obsBucket          | No              | String          | Name of the OBS bucket to which dirty data is written. This parameter is valid only when dirty data is written to OBS. For example, **dirtyData**.                                                                                                  |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.dirtyDataDirectory | No              | String          | Directory to which dirty data is written                                                                                                                                                                                                            |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  To write dirty data to HDFS, set this parameter to the specified HDFS directory.                                                                                                                                                                 |
|                                     |                 |                 | -  To write dirty data to OBS, set this parameter to the directory in the OBS bucket. For example, **/data/dirtydata/**.                                                                                                                            |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| throttlingConfig.maxErrorRecords    | No              | String          | Maximum number of error records in a single shard. When the number of error records of a map exceeds the upper limit, the task automatically ends. The imported data will not be rolled back.                                                       |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.isSchedulerJob      | No              | Boolean         | Whether to enable a scheduled task. For example, **true**.                                                                                                                                                                                          |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.cycleType           | No              | String          | Cycle type of a scheduled task. The options are as follows:                                                                                                                                                                                         |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  **minute**: minute                                                                                                                                                                                                                               |
|                                     |                 |                 | -  **hour**: hour                                                                                                                                                                                                                                   |
|                                     |                 |                 | -  **day**: day                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  **week**: week                                                                                                                                                                                                                                   |
|                                     |                 |                 | -  **month**: month                                                                                                                                                                                                                                 |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.cycle               | No              | Integer         | Cycle of a scheduled task. If **cycleType** is set to **minute** and **cycle** is set to **10**, the scheduled task is executed every 10 minutes.                                                                                                   |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.runAt               | No              | String          | Time when a scheduled task is triggered in a cycle. This parameter is valid only when **cycleType** is set to **hour**, **week**, or **month**.                                                                                                     |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  If **cycleType** is set to **month**, **cycle** is set to **1**, and **runAt** is set to **15**, the scheduled task is executed on the 15th day of each month. You can set **runAt** to multiple values and separate the values with commas (,). |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 |    For example, if **runAt** is set to **1,2,3,4,5**, the scheduled task is executed on the first day, second day, third day, fourth day, and fifth day of each month.                                                                              |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  If **cycleType** is set to **week** and **runAt** is set to **mon,tue,wed,thu,fri**, the scheduled task is executed on Monday to Friday.                                                                                                         |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  If **cycleType** is set to **hour** and **runAt** is set to **27,57**, the scheduled task is executed at the 27th and 57th minute in the cycle.                                                                                                  |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.startDate           | No              | String          | Start time of a scheduled task. For example, **2018-01-24 19:56:19**.                                                                                                                                                                               |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.stopDate            | No              | String          | End time of a scheduled task. For example, **2018-01-27 23:59:00**.                                                                                                                                                                                 |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | If you do not set the end time, the scheduled task is always executed and will never stop.                                                                                                                                                          |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schedulerConfig.disposableType      | No              | Enumeration     | Whether to delete a job after the job is executed. The options are as follows:                                                                                                                                                                      |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  **NONE**: A job will not be deleted after it is executed.                                                                                                                                                                                        |
|                                     |                 |                 | -  **DELETE_AFTER_SUCCEED**: A job will be deleted only after it is successfully executed. It is applicable to massive one-time jobs.                                                                                                               |
|                                     |                 |                 | -  **DELETE**: A job will be deleted after it is executed, regardless of the execution result.                                                                                                                                                      |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| retryJobConfig.retryJobType         | No              | Enumeration     | Whether to automatically retry if a job fails to be executed. The options are as follows:                                                                                                                                                           |
|                                     |                 |                 |                                                                                                                                                                                                                                                     |
|                                     |                 |                 | -  **NONE**: Do not retry.                                                                                                                                                                                                                          |
|                                     |                 |                 | -  **RETRY_TRIPLE**: Retry three times.                                                                                                                                                                                                             |
+-------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
