:original_name: dataartsstudio_02_0094.html

.. _dataartsstudio_02_0094:

Viewing a Job Instance List
===========================

Function
--------

This API is used to view a job instance list.

A job instance is generated each time you run a batch job for which periodic scheduling or event-based scheduling is configured. If a real-time job contains a node for which periodic scheduling or event-based scheduling is configured, you can call this API to view the instance list of the subjobs associated with the node. The format of the **jobName** parameter is *real-time job name*\ \_\ *node name*.

URI
---

-  URI format

   GET /v1/{project_id}/jobs/instances/detail?jobName={jobName}&minPlanTime={minPlanTime}&maxPlanTime={maxPlanTime}&limit={limit}&offset={offset}&status={status}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                            |
      +=================+=================+=================+========================================================================================================================================+
      | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`.               |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | jobName         | No              | String          | Job name.                                                                                                                              |
      |                 |                 |                 |                                                                                                                                        |
      |                 |                 |                 | -  If you want to query the instance list of a specific batch job, jobName is the batch job name.                                      |
      |                 |                 |                 | -  If you want to query sub-jobs associated with a node in a real-time job, the jobName format is *real-time job name* \_ *node name*. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | minPlanTime     | No              | Long            | Minimum planned job execution time in milliseconds. Job instances whose planned execution time is longer than this time are returned.  |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | maxPlanTime     | No              | Long            | Maximum planned job execution time in milliseconds. Job instances whose planned execution time is shorter than this time are returned. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | int             | The maximum number of records on each page.                                                                                            |
      |                 |                 |                 |                                                                                                                                        |
      |                 |                 |                 | The parameter value ranges from 1 to 1000.                                                                                             |
      |                 |                 |                 |                                                                                                                                        |
      |                 |                 |                 | Default value: **10**                                                                                                                  |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | int             | Start page of the paging list. The default value is **0**. The value must be greater than or equal to **0**.                           |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
      | status          | No              | String          | Job instance status.                                                                                                                   |
      |                 |                 |                 |                                                                                                                                        |
      |                 |                 |                 | -  waiting                                                                                                                             |
      |                 |                 |                 | -  running                                                                                                                             |
      |                 |                 |                 | -  success                                                                                                                             |
      |                 |                 |                 | -  fail                                                                                                                                |
      |                 |                 |                 | -  running-exception                                                                                                                   |
      |                 |                 |                 | -  pause                                                                                                                               |
      |                 |                 |                 | -  manual-stop                                                                                                                         |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                             |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default. |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response
--------

.. table:: **Table 3** Response parameters

   +-----------+-----------+----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type           | Description                                                                                                               |
   +===========+===========+================+===========================================================================================================================+
   | total     | Yes       | int            | Total number of records.                                                                                                  |
   +-----------+-----------+----------------+---------------------------------------------------------------------------------------------------------------------------+
   | instances | Yes       | List<Instance> | Job instance status. For details, see :ref:`Table 4 <dataartsstudio_02_0094__en-us_topic_0181281341_table4361191610322>`. |
   +-----------+-----------+----------------+---------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0094__en-us_topic_0181281341_table4361191610322:

.. table:: **Table 4** instances parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================================================================+
   | jobName         | Yes             | String          | Job name. When you view the instance list of a specified batch job, **jobName** is the name of the batch job. When you view the subjobs associated with a node in a real-time job, **jobName** is in format of *real-time job name*\ \_\ *node name*. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | jobInstanceName | Yes             | String          | Name of a job instance recorded by the log, rather than the name defined during job creation                                                                                                                                                          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | Yes             | String          | Job instance status.                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  waiting                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  running                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  success                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  fail                                                                                                                                                                                                                                               |
   |                 |                 |                 | -  running-exception                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  pause                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  manual-stop                                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | planTime        | Yes             | Long            | Planned execution time of the job instance.                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | startTime       | Yes             | Long            | Actual execution start time of the job instance.                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | endTime         | No              | Long            | Actual execution end time of the job instance.                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | executeTime     | No              | Long            | Execution duration in milliseconds.                                                                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instanceId      | Yes             | Long            | Job instance ID.                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | submitTime      | Yes             | Long            | Time when a job is submitted.                                                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example 1
---------

View the instance list of batch job **job_batch**.

-  Request

   .. code-block:: text

      GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/instances/detail?jobName=job_batch

-  Success response

   .. code-block::

      {
          "total": 2,
          "instances": [{
              "endTime": 1551671598000,
              "executeTime": 0.3,
              "instanceId": 34765,

              "jobName": "job_batch",
                      "jobInstanceName": "job_batch",
              "planTime": 1551671580000,
              "startTime": 1551671580000,
              "status": "success",
              "submitTime": 1550910278706
          },
          {
              "endTime": 1551671538000,
              "executeTime": 0.3,
              "instanceId": 34764,

              "jobName": "job_batch",
                      "jobInstanceName": "job_batch",
              "planTime": 1551671520000,
              "startTime": 1551671521000,
              "status": "success",
              "submitTime": 1550910278706
          }]
      }
