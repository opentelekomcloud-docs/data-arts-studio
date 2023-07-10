:original_name: dataartsstudio_02_0087.html

.. _dataartsstudio_02_0087:

Viewing Job Details
===================

Function
--------

This API is used to view job details.

URI
---

-  URI format

   GET /v1/{project_id}/jobs/{name}

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                              |
      +============+===========+========+==========================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | name       | Yes       | String | Job name.                                                                                                                |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

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

See the request parameters in :ref:`Creating a Job <dataartsstudio_02_0084>`.

Example
-------

View details about job **myJob**.

-  Request

   .. code-block:: text

      GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/myJob

-  Success response

   .. code-block::

      {
          "basicConfig": {
              "instanceTimeout": 0,
              "priority": 0
          },
          "logPath": "obs://dlf-log-b384b9e9ab9b4ee8994c8633aabc9505",
          "name": "myJob",
          "nodes": [{
              "failPolicy": "FAIL",
              "location": {
                  "x": "385.0",
                  "y": "150.0"
              },
              "maxExecutionTime": 60,
              "name": "DIS_INPUT",
              "pollingInterval": 1,
              "preNodeName": [],
              "properties": [{
                  "name": "streamName",
                  "value": "csinput"
              }],
              "resources": [],
              "retryInterval": 120,
              "retryTimes": 0,
              "type": "DISStream"
          },
          {
              "failPolicy": "FAIL",
              "location": {
                  "x": "572.0",
                  "y": "151.0"
              },
              "maxExecutionTime": 60,
              "name": "CS_PROCESS",
              "pollingInterval": 10,
              "preNodeName": ["DIS_INPUT"],
              "properties": [{
                  "name": "scriptName",
                  "value": "CS_PROCESS_TRIP"
              },
              {
                  "name": "jobName",
                  "value": "CS_PROCESS"
              },
              {
                  "name": "jobType",
                  "value": "flink_sql_job"
              },
              {
                  "name": "clusterName",
                  "value": "-1"
              },
              {
                  "name": "spuNumber",
                  "value": "2"
              },
              {
                  "name": "parallelNumber",
                  "value": "1"
              }],
              "resources": [],
              "retryInterval": 120,
              "retryTimes": 0,
              "type": "CSJob"
          },
          {
              "failPolicy": "FAIL",
              "location": {
                  "x": "718.0",
                  "y": "121.0"
              },
              "maxExecutionTime": 60,
              "name": "DIS_EVENT",
              "pollingInterval": 1,
              "preNodeName": ["CS_PROCESS"],
              "properties": [{
                  "name": "streamName",
                  "value": "dis-event"
              }],
              "resources": [],
              "retryInterval": 120,
              "retryTimes": 0,
              "type": "DISStream"
          },
          {
              "eventTrigger": {
                  "channel": "dis-event",
                  "concurrent": 1,
                  "engineType": "DIS",
                  "failPolicy": "CONTINUE",
                  "readPolicy": "LAST"
              },
              "failPolicy": "FAIL",
              "location": {
                  "x": "848.0",
                  "y": "167.0"
              },
              "maxExecutionTime": 60,
              "name": "TRIP_RAW_STANDARD",
              "pollingInterval": 10,
              "preNodeName": ["DIS_EVENT"],
              "properties": [{
                  "name": "scriptName",
                  "value": "TRIP_RAW_STANDARD"
              },
              {
                  "name": "database",
                  "value": "lixinlong"
              },
              {
                  "name": "queueName",
                  "value": "default"
              }],
              "resources": [],
              "retryInterval": 120,
              "retryTimes": 0,
              "type": "DLISQL"
          }],
          "params": [{
              "name": "dis_channel",
              "value": "dis_input"
          }],
          "processType": "REAL_TIME",
          "resources": [],
          "schedule": {
              "type": "EXECUTE_ONCE"
          },
          "version": "1.0"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
