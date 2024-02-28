:original_name: dataartsstudio_02_0090.html

.. _dataartsstudio_02_0090:

Importing a Job
===============

Function
--------

This API is used to import one or more job files from OBS to DLF.

.. note::

   Before using this API, store job files in OBS buckets.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/import

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                       |
   +=================+=================+====================+===================================================================================================================================================================================================================+
   | path            | Yes             | String             | If OBS is deployed, it refers to the OBS path for storing the job definition file. For the format of the job definition file, see the response message of the exported job, for example, obs://myBucket/jobs.zip. |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | params          | No              | Map<String,String> | Public job parameter.                                                                                                                                                                                             |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sameNamePolicy  | No              | String             | Policy for specifying how to handle duplicate names. The options are as follows:                                                                                                                                  |
   |                 |                 |                    |                                                                                                                                                                                                                   |
   |                 |                 |                    | -  SKIP                                                                                                                                                                                                           |
   |                 |                 |                    | -  OVERWRITE                                                                                                                                                                                                      |
   |                 |                 |                    |                                                                                                                                                                                                                   |
   |                 |                 |                    | Default value: **SKIP**                                                                                                                                                                                           |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | jobsParam       | No              | List<JobParam>     | Job parameter. For details, see :ref:`Table 3 <dataartsstudio_02_0090__en-us_topic_0181281374_table5837184718449>`.                                                                                               |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | executeUser     | No              | String             | User that executes the job.                                                                                                                                                                                       |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | targetStatus    | No              | String             | This parameter is required if the review function is enabled. It indicates the target status of the job. The value can be **SAVED**, **SUBMITTED**, or **PRODUCTION**.                                            |
   |                 |                 |                    |                                                                                                                                                                                                                   |
   |                 |                 |                    | -  **SAVED** indicates that the job is saved but cannot be scheduled or executed. It can be executed only after submitted and approved.                                                                           |
   |                 |                 |                    | -  **SUBMITTED** indicates that the job is automatically submitted after it is saved and can be executed after it is approved.                                                                                    |
   |                 |                 |                    | -  **PRODUCTION** indicates that the job can be directly executed after it is created. Note: Only the workspace administrator can create jobs in the **PRODUCTION** state.                                        |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | approvers       | No              | List<JobApprover>  | Job approver. This parameter is required if the review function is enabled. For details, see :ref:`Table 5 <dataartsstudio_02_0090__table943565132314>`.                                                          |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0090__en-us_topic_0181281374_table5837184718449:

.. table:: **Table 3** JobParam parameters

   ========= ========= ================== ==============
   Parameter Mandatory Type               Description
   ========= ========= ================== ==============
   name      Yes       String             Job name.
   params    No        Map<String,String> Job parameter.
   ========= ========= ================== ==============

Response
--------

.. table:: **Table 4** Response parameter

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                 |
   +===========+===========+========+=============================================================================================+
   | taskId    | Yes       | String | ID of the task. Used to call the API for querying system tasks to obtain the import status. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0090__table943565132314:

.. table:: **Table 5** Approver attributes

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   approverName Yes       String Approver name
   ============ ========= ====== =============

Example Request
---------------

Import jobs from OBS to DLF. If there are jobs and scripts with the same name, overwrite them. The definition file of the imported job is in the **obs://aaaaa/job_batch.zip** OBS path, and the job name is **job_batch**.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/import
   {
       "path": "obs://aaaaa/job_batch.zip",
       "jobsParam": [
           {
               "name": "job_batch"
           }
       ]
   }

Import jobs from OBS to DLF when the review function is enabled. If there are jobs and scripts with the same name, overwrite them.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/import
   {
       "path": "obs://aaaaa/job_batch.zip",
       "jobsParam": [
           {
               "name": "job_batch"
           }
       ],
       "targetStatus": "SUBMITTED",
       "approvers": [
       {
         "approverName": "userName1"
       },
       {
         "approverName": "userName2"
       }
     ]
   }

Example Response
----------------

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "taskId":"008aae2e675933c7016759418e870000"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0815",
          "error_msg":"Fail to read OBS file."
      }
