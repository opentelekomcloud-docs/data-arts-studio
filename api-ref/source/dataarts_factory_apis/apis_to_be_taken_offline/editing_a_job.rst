:original_name: dataartsstudio_02_0085.html

.. _dataartsstudio_02_0085:

Editing a Job
=============

Function
--------

This API is used to edit a job.

URI
---

-  URI format

   PUT /v1/{project_id}/jobs/{job_name}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                              |
      +============+===========+========+==========================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <dataartsstudio_02_0314>`. |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
      | job_name   | Yes       | String | Job name.                                                                                                                |
      +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

See :ref:`Request <dataartsstudio_02_0084__en-us_topic_0181281297_section10789431145710>`.

Example
-------

Modify the properties of job **dliJob1**.

-  Request

   .. code-block:: text

      PUT /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/dliJob1
      {
          "logPath":"obs://dlf-log-b384b9e9ab9b4ee8994c8633aabc9505",
          "name":"dliJob1",
          "nodes":[
              {
                  "failPolicy":"FAIL",
                  "location":{
                      "x":"385.0",
                      "y":"150.0"
                  },
                  "maxExecutionTime":60,
                  "name":"DIS_INPUT",
                  "pollingInterval":1,
                  "preNodeName":[],
                  "properties":[
                      {
                          "name":"streamName",
                          "value":"csinput"
                      }
                  ],
                  "resources":[],
                  "retryInterval":120,
                  "retryTimes":0,
                  "type":"DISStream"
              },
              {
                  "failPolicy":"FAIL",
                  "location":{
                      "x":"572.0",
                      "y":"151.0"
                  },
                  "maxExecutionTime":60,
                  "name":"CS_PROCESS",
                  "pollingInterval":10,
                  "preNodeName":[
                      "DIS_INPUT"
                  ],
                  "properties":[
                      {
                          "name":"scriptName",
                          "value":"CS_PROCESS_TRIP"
                      },
                      {
                          "name":"jobName",
                          "value":"CS_PROCESS"
                      },
                      {
                          "name":"jobType",
                          "value":"flink_sql_job"
                      },
                      {
                          "name":"spuNumber",
                          "value":"2"
                      },
                      {
                          "name":"parallelNumber",
                          "value":"1"
                      }
                  ],
                  "resources":[],
                  "retryInterval":120,
                  "retryTimes":0,
                  "type":"CSJob"
              },
              {
                  "failPolicy":"FAIL",
                  "location":{
                      "x":"718.0",
                      "y":"121.0"
                  },
                  "maxExecutionTime":60,
                  "name":"DIS_EVENT",
                  "pollingInterval":1,
                  "preNodeName":[
                      "CS_PROCESS"
                  ],
                  "properties":[
                      {
                          "name":"streamName",
                          "value":"dis-event"
                      }
                  ],
                  "resources":[],
                  "retryInterval":120,
                  "retryTimes":0,
                  "type":"DISStream"
              },
              {
                  "eventTrigger":{
                      "channel":"dis-event",
                      "concurrent":1,
                          "eventType:"DIS",
                      "readPolicy":"LAST"
                  },
                  "failPolicy":"FAIL",
                  "location":{
                      "x":"848.0",
                      "y":"167.0"
                  },
                  "maxExecutionTime":60,
                  "name":"TRIP_RAW_STANDARD",
                  "pollingInterval":10,
                  "preNodeName":[
                      "DIS_EVENT"
                  ],
                  "properties":[
                      {
                          "name":"scriptName",
                          "value":"TRIP_RAW_STANDARD"
                      },
                      {
                          "name":"database",
                          "value":"lixinlong"
                      },
                      {
                          "name":"queueName",
                          "value":"default"
                      }
                  ],
                  "resources":[],
                  "retryInterval":120,
                  "retryTimes":0,
                  "type":"DLISQL"
              }
          ],
          "params":[
              {
                  "name":"dis_channel",
                  "value":"dis_input"
              }
          ],
          "processType":"REAL_TIME",
          "resources":[],
          "schedule":{
              "type":"EXECUTE_ONCE"
          },
          "version":"1.0"
      }

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
