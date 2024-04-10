:original_name: dataartsstudio_02_0093.html

.. _dataartsstudio_02_0093:

Viewing Running Status of a Real-Time Job
=========================================

Function
--------

This API is used to view running status of a real-time job.

URI
---

-  URI format

   GET /v1/{project_id}/jobs/{job_name}/status

-  Parameter description

   .. table:: **Table 1** URI parameters

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | job_name   | Yes       | String | Job name.                                                                                                             |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                             |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default. |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Response parameters

   +-----------------+-----------------+-----------------+---------------------+
   | Parameter       | Mandatory       | Type            | Description         |
   +=================+=================+=================+=====================+
   | name            | Yes             | String          | Name of a solution. |
   +-----------------+-----------------+-----------------+---------------------+
   | nodes           | No              | List            | Node status list.   |
   +-----------------+-----------------+-----------------+---------------------+
   | status          | No              | String          | Job status.         |
   |                 |                 |                 |                     |
   |                 |                 |                 | -  STARTING         |
   |                 |                 |                 | -  NORMAL           |
   |                 |                 |                 | -  EXCEPTION        |
   |                 |                 |                 | -  STOPPING         |
   |                 |                 |                 | -  STOPPED          |
   +-----------------+-----------------+-----------------+---------------------+
   | startTime       | Yes             | Date            | Start time.         |
   +-----------------+-----------------+-----------------+---------------------+
   | endTime         | No              | Date            | End time.           |
   +-----------------+-----------------+-----------------+---------------------+
   | lastUpdateTime  | No              | Date            | Last update time.   |
   +-----------------+-----------------+-----------------+---------------------+

.. table:: **Table 4** Data structure description of **nodes**

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | name            | Yes             | String          | Node name.                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | status          | No              | String          | Node status.                                                                                  |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  STARTING                                                                                   |
   |                 |                 |                 | -  NORMAL                                                                                     |
   |                 |                 |                 | -  EXCEPTION                                                                                  |
   |                 |                 |                 | -  STOPPING                                                                                   |
   |                 |                 |                 | -  STOPPED                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | logPath         | No              | String          | Path for storing node run logs.                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Node type.                                                                                    |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  **Hive SQL**: Runs Hive SQL scripts.                                                       |
   |                 |                 |                 | -  **Spark SQL**: Runs Spark SQL scripts.                                                     |
   |                 |                 |                 | -  **DWS SQL**: Runs DWS SQL scripts.                                                         |
   |                 |                 |                 | -  **DLI SQL**: Runs DLI SQL scripts.                                                         |
   |                 |                 |                 | -  **Shell**: Runs shell SQL scripts.                                                         |
   |                 |                 |                 | -  **CDM Job**: Runs CDM jobs.                                                                |
   |                 |                 |                 | -  **DIS Transfer Task:** Creates DIS dump tasks.                                             |
   |                 |                 |                 | -  **CS Job**: Creates and starts CloudStream jobs.                                           |
   |                 |                 |                 | -  **CloudTable Manager**: Manages CloudTable tables, including creating and deleting tables. |
   |                 |                 |                 | -  **OBS Manager**: Manages OBS paths, including creating and deleting paths.                 |
   |                 |                 |                 | -  **RESTAPI:** Sends REST API requests.                                                      |
   |                 |                 |                 | -  **SMN**: Sends short messages or emails.                                                   |
   |                 |                 |                 | -  **MRS Spark**: Runs Spark jobs of MRS.                                                     |
   |                 |                 |                 | -  **MapReduce**: Runs MapReduce jobs of MRS.                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

Example Request
---------------

View running status of real-time job **job_sms** and the running status of each node in the job.

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/job_sms/status

Example Response
----------------

-  Success response

   .. code-block::

      {
          "name": "job_sms",
          "nodes": [
              {
                  "bufferRecords": 0,
                  "jobInstanceId": 0,
                  "LastInstanceStatus": "waiting",
                  "name": "MRS_Flink_Job_8635",
                  "speed": 0,
                  "totalGetBytes": 0,
                  "totalGetRecords": 0,
                  "totalPutBytes": 0,
                  "totalPutRecords": 0
              }
          ],
          "status": "NORMAL"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
