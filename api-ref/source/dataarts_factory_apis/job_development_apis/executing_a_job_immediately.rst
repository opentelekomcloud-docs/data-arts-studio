:original_name: dataartsstudio_02_0091.html

.. _dataartsstudio_02_0091:

Executing a Job Immediately
===========================

Function
--------

This API is used to execute a job immediately and check whether the job can be executed successfully.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/{job_name}/run-immediate

-  Parameter description

   .. table:: **Table 1** URI parameter

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

.. table:: **Table 3** Parameter

   +-----------+-----------+----------------+--------------------------------------------+
   | Parameter | Mandatory | Type           | Description                                |
   +===========+===========+================+============================================+
   | jobParams | No        | List<JobParam> | Parameters for executing a job immediately |
   +-----------+-----------+----------------+--------------------------------------------+

.. table:: **Table 4** JobParam data structure description

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | name            | Yes             | String          | Name of the parameter. It cannot exceed 64 characters.     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | value           | Yes             | String          | Value of the parameter. It cannot exceed 1,024 characters. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | paramType       | No              | String          | Parameter type                                             |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  variable                                                |
   |                 |                 |                 | -  constants                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 5** Response parameter

   ========== ========= ==== ================
   Parameter  Mandatory Type Description
   ========== ========= ==== ================
   instanceId Yes       Long Job instance ID.
   ========== ========= ==== ================

Example Request
---------------

Execute the **myJob** job once. The job contains parameter **aaa** with value **111** and parameter **bbb** with value **222**.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/myJob/run-immediate
   {
       "jobParams":[
           {
               "name":"aaa",
               "value":"111"
           },
           {
               "name":"bbb",
               "value":"222"
           }
       ]
   }

Example Response
----------------

-  Success response

   .. code-block::

      {
          "instanceId":132343
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0100",
          "error_msg":"The job does not exists."
      }
