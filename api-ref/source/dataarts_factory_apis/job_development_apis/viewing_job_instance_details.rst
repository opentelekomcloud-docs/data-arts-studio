:original_name: dataartsstudio_02_0095.html

.. _dataartsstudio_02_0095:

Viewing Job Instance Details
============================

Function
--------

This API is used to view job instance details, including the execution information about each node in a job instance.

URI
---

-  URI format

   GET /v1/{project_id}/jobs/{job_name}/instances/{instance_id}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                                                          |
      +=============+===========+========+======================================================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+
      | job_name    | Yes       | String | Job name                                                                                                                                             |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | string | Job instance ID. For details about how to obtain the ID, see the response parameters in :ref:`Viewing a Job Instance List <dataartsstudio_02_0094>`. |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                            |
   +=================+=================+=================+========================================================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                                                          |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default.                              |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                                                     |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 |    .. note::                                                                                                           |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 |       -  You need to specify a workspace for multiple DataArts Studio instances.                                       |
   |                 |                 |                 |       -  This parameter is mandatory if no default workspace is available. If you do not set it, an error is reported. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | jobName         | Yes             | String          | Job name                                                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | instanceId      | Yes             | Long            | Job instance ID                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | status          | Yes             | String          | Job instance status.                                                                                                       |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | -  waiting                                                                                                                 |
   |                 |                 |                 | -  running                                                                                                                 |
   |                 |                 |                 | -  success                                                                                                                 |
   |                 |                 |                 | -  fail                                                                                                                    |
   |                 |                 |                 | -  running-exception                                                                                                       |
   |                 |                 |                 | -  pause                                                                                                                   |
   |                 |                 |                 | -  manual-stop                                                                                                             |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | planTime        | Yes             | Long            | Planned execution time of the job instance                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | startTime       | Yes             | Long            | Actual execution start time of the job instance                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | endTime         | No              | Long            | Actual execution end time of the job instance                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | executeTime     | No              | Long            | Execution duration in milliseconds                                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | total           | Yes             | Integer         | Total number of node records                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | nodes           | Yes             | List<Node>      | Node instance status. For details, see :ref:`Table 4 <dataartsstudio_02_0095__en-us_topic_0181281301_table4361191610322>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | instanceType    | Yes             | Integer         | Job scheduling modes.                                                                                                      |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | -  0: General scheduling                                                                                                   |
   |                 |                 |                 | -  2: Manual scheduling                                                                                                    |
   |                 |                 |                 | -  5: PatchData                                                                                                            |
   |                 |                 |                 | -  6: Subjob scheduling                                                                                                    |
   |                 |                 |                 | -  7: Schedule once                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | forceSuccess    | No              | boolean         | Whether the job instance status is forcibly successful                                                                     |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Default value: **false**                                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | ignoreSuccess   | No              | boolean         | Whether the job instance status is failure ignored                                                                         |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | Default value: **false**                                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0095__en-us_topic_0181281301_table4361191610322:

.. table:: **Table 4** Node parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | nodeName        | Yes             | String          | Node name                                                                                    |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | status          | Yes             | String          | Node status.                                                                                 |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | -  waiting                                                                                   |
   |                 |                 |                 | -  running                                                                                   |
   |                 |                 |                 | -  success                                                                                   |
   |                 |                 |                 | -  fail                                                                                      |
   |                 |                 |                 | -  skip                                                                                      |
   |                 |                 |                 | -  pause                                                                                     |
   |                 |                 |                 | -  manual-stop                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | queue           | Yes             | String          | DLI resource queue name                                                                      |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | .. note::                                                                                    |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 |    Only the DLI SQL or DLI SPARK operator returns the DLI queue name in the response.        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | planTime        | Yes             | Long            | Planned execution time of the job instance                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | startTime       | Yes             | Long            | Actual execution start time of the node                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | endTime         | No              | Long            | Actual execution end time of the node                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Node type.                                                                                   |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | -  **Hive SQL**: runs Hive SQL scripts.                                                      |
   |                 |                 |                 | -  **Spark SQL**: runs Spark SQL scripts.                                                    |
   |                 |                 |                 | -  **DWS SQL**: runs DWS SQL scripts.                                                        |
   |                 |                 |                 | -  **DLI SQL**: runs DLI SQL scripts.                                                        |
   |                 |                 |                 | -  **Shell**: runs shell SQL scripts.                                                        |
   |                 |                 |                 | -  **CDM Job**: runs CDM jobs.                                                               |
   |                 |                 |                 | -  **CloudTableManager**: manages CloudTable tables, including creating and deleting tables. |
   |                 |                 |                 | -  **OBS Manager**: manages OBS paths, including creating and deleting paths.                |
   |                 |                 |                 | -  **RestClient**: sends REST API requests.                                                  |
   |                 |                 |                 | -  **SMN**: sends short messages or emails.                                                  |
   |                 |                 |                 | -  **MRS Spark**: runs Spark jobs of MRS.                                                    |
   |                 |                 |                 | -  **MapReduce**: Runs MapReduce jobs of MRS.                                                |
   |                 |                 |                 | -  **MRSFlinkJob**: runs FlinkJob jobs of MRS.                                               |
   |                 |                 |                 | -  **MRS HetuEngine**: runs HetuEngine jobs of MRS.                                          |
   |                 |                 |                 | -  **DLI Spark**: runs Spark jobs of DLF.                                                    |
   |                 |                 |                 | -  **RDSSQL**: transfers SQL statements to RDS for execution.                                |
   |                 |                 |                 | -  **ModelArts Train**: executes workflow jobs of ModelArts.                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | retryTimes      | No              | Integer         | Number of attempts upon a failure                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | instanceId      | Yes             | Long            | Job instance ID                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | inputRowCount   | No              | Long            | Rows of input data                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | speed           | No              | number          | Write speed (row/second)                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | logPath         | No              | String          | Path for storing node execution logs                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

Example Request
---------------

View details about the instance whose ID is 34765 in job **job_batch**.

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/job_batch/instances/34765

Example Response
----------------

-  Success response

   .. code-block::

      {
          "jobName":"job_batch",
          "instanceId":34765,
          "instanceType": 2,
          "status":"fail",
          "planTime":1551425326540,
          "startTime":1551425327000,
          "endTime":1551425387000,
          "executeTime":1,
          "forceSuccess":false,
          "ignoreSuccess":false,
          "total":2,
          "nodes":[
              {
                  "endTime":1551671590000,
                  "inputRowCount":0,
                  "instanceId":34765,
                  "nodeName":"Dummy_8556",
                  "queue":"dlf_notdelete",
                  "planTime":1551671580000,
                  "retryTimes":0,
                  "startTime":1551671584000,
                  "status":"success",
                  "type":"Dummy"
              },
              {
                  "endTime":1551671598000,
                  "inputRowCount":0,
                  "instanceId":34765,
                  "logPath":"obs://dlf-test-log/job_batch/2019-03-04 11_53_00.000/error/error.job",
                  "nodeName":"error",
                  "planTime":1551671580000,
                  "retryTimes":0,
                  "startTime":1551671594000,
                  "status":"success",
                  "type":"DWS SQL"
              }
          ]
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0137",
          "error_msg":"Job instance does not exist."
      }
