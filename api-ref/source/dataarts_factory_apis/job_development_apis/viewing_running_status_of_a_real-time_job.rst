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
      | job_name   | Yes       | String | Job name                                                                                                              |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | name            | Yes             | String          | Solution name                              |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | nodes           | No              | List            | Node status list                           |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | status          | No              | String          | Job status                                 |
   |                 |                 |                 |                                            |
   |                 |                 |                 | -  **STARTING**: The job is starting.      |
   |                 |                 |                 | -  **NORMAL**: The job is normal.          |
   |                 |                 |                 | -  **EXCEPTION**: The job is abnormal.     |
   |                 |                 |                 | -  **STOPPING**: The job is being stopped. |
   |                 |                 |                 | -  **STOPPED**: The job is stopped.        |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | startTime       | Yes             | Date            | Start time                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | endTime         | No              | Date            | End time                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | lastUpdateTime  | No              | Date            | Last update time                           |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 4** Data structure description of **nodes**

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | name            | Yes             | String          | Node name                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | status          | No              | String          | Node status.                                                                                  |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  **STARTING**: The node is starting.                                                        |
   |                 |                 |                 | -  **NORMAL**: The node is normal.                                                            |
   |                 |                 |                 | -  **EXCEPTION**: The node is abnormal.                                                       |
   |                 |                 |                 | -  **STOPPING**: The node is being stopped.                                                   |
   |                 |                 |                 | -  **STOPPED**: The node is stopped.                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | logPath         | No              | String          | Path for storing node run logs.                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Node type                                                                                     |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  **Hive SQL**: runs Hive SQL scripts.                                                       |
   |                 |                 |                 | -  **Spark SQL**: runs Spark SQL scripts.                                                     |
   |                 |                 |                 | -  **DWS SQL**: runs DWS SQL scripts.                                                         |
   |                 |                 |                 | -  **DLI SQL**: runs DLI SQL scripts.                                                         |
   |                 |                 |                 | -  **Shell**: runs shell SQL scripts.                                                         |
   |                 |                 |                 | -  **CDM Job**: runs CDM jobs.                                                                |
   |                 |                 |                 | -  **DIS Transfer Task**: creates DIS dump tasks.                                             |
   |                 |                 |                 | -  **CS Job**: creates and starts CloudStream jobs.                                           |
   |                 |                 |                 | -  **CloudTable Manager**: manages CloudTable tables, including creating and deleting tables. |
   |                 |                 |                 | -  **OBS Manager**: manages OBS paths, including creating and deleting paths.                 |
   |                 |                 |                 | -  **RESTAPI**: sends REST API requests.                                                      |
   |                 |                 |                 | -  **SMN**: sends short messages or emails.                                                   |
   |                 |                 |                 | -  **MRS Spark**: runs Spark jobs of MRS.                                                     |
   |                 |                 |                 | -  **MapReduce**: runs MapReduce jobs of MRS.                                                 |
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
