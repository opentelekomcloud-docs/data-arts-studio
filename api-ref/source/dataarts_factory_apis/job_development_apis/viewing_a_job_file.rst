:original_name: dataartsstudio_02_0063.html

.. _dataartsstudio_02_0063:

Viewing a Job File
==================

Function
--------

This API is used to check whether there are jobs and scripts in the job file to be imported from OBS to DLF.

URI
---

-  URI format

   POST /v1/{project_id}/jobs/check-file

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

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                         |
   +===========+===========+========+=====================================================================================================+
   | path      | No        | String | If OBS is deployed, the job definition file is stored on OBS, for example, obs://myBucket/jobs.zip. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 3** Response parameters

   +-----------+-----------+--------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type         | Description                                                                                                              |
   +===========+===========+==============+==========================================================================================================================+
   | jobs      | No        | List<Job>    | Job information. For details, see :ref:`Table 4 <dataartsstudio_02_0063__en-us_topic_0181281317_table165346413179>`.     |
   +-----------+-----------+--------------+--------------------------------------------------------------------------------------------------------------------------+
   | scripts   | No        | List<Script> | Script information. For details, see :ref:`Table 5 <dataartsstudio_02_0063__en-us_topic_0181281317_table1996985891715>`. |
   +-----------+-----------+--------------+--------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0063__en-us_topic_0181281317_table165346413179:

.. table:: **Table 4** job data structure description

   ========= ========= ================== ===============
   Parameter Mandatory Type               Description
   ========= ========= ================== ===============
   params    No        Map<String,String> Job parameter.
   name      Yes       String             Job name.
   path      Yes       String             Path of the job
   ========= ========= ================== ===============

.. _dataartsstudio_02_0063__en-us_topic_0181281317_table1996985891715:

.. table:: **Table 5** Data structure description of **Script**

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   name      Yes       String Script name.
   path      Yes       String Path of the script.
   ========= ========= ====== ===================

Example Request
---------------

Query the parameter definitions in the job file on OBS. The OBS path of the job definition file is **obs://aaaaa/DLF_myJob.zip**.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/jobs/check-file
   {
   "path": "obs://aaaaa/DLF_myJob.zip"
   }

Example Response
----------------

-  Success response

   .. code-block::

      {
          "jobs":[
              {
                  "name":"test",
                  "path":"/test",
                  "params":{
                      "ddd":"dddd"
                  }
              },
              {
                  "name":"test1",
                  "path":"/test",
                  "params":{
                      "ddd":"dddd"
                  }
              }
          ],
          "scripts":[
              {
                  "name":"script1",
                  "path":"/path1"
              },
              {
                  "name":"script2",
                  "path":"/path1"
              }
          ]
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.0815",
          "error_msg":"Fail to read OBS file."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
