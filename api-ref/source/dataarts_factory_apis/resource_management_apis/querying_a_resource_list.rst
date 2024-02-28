:original_name: dataartsstudio_02_0105.html

.. _dataartsstudio_02_0105:

Querying a Resource List
========================

Function
--------

This API is used to query a resource list. During the query, you can specify the page number and the maximum number of records on each page.

URI
---

-  URI format

   GET /v1/{project_id}/resources?offset={offset}&limit={limit}&resourceName={resourceName}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                           |
      +=================+=================+=================+=======================================================================================================================+
      | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Start page of the paging list. Default value: **0** The value must be greater than or equal to **0**.                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | The maximum number of records on each page. The value ranges from 1 to 100.                                           |
      |                 |                 |                 |                                                                                                                       |
      |                 |                 |                 | Default value: **10**                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
      | resourceName    | No              | String          | Name of the resource.                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

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

========= ========= ============== ==============================
Parameter Mandatory Type           Description
========= ========= ============== ==============================
total     Yes       Integer        The total number of resources.
resources Yes       List<Resource> A list of resources.
========= ========= ============== ==============================

.. table:: **Table 3** Resource parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================================================================+
   | id              | Yes             | String          | ID of the resource. The resource ID is used to query the resource.                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Name of the resource. The name contains a maximum of 32 characters, including only letters, numbers, underscores (_), and hyphens (-).                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Resource type.                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  archive                                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  file                                                                                                                                                                                                                                                                   |
   |                 |                 |                 | -  jar                                                                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | location        | Yes             | String          | OBS path for storing the resource file. When **type** is set to **jar**, **location** is the path for storing the main JAR package. The path contains a maximum of 256 characters. For example, obs://myBucket/test.jar                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependFiles     | No              | List<String>    | JAR package and properties file that the main JAR package depends on. The description contains a maximum of 10,240 characters.                                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc            | No              | String          | The description contains a maximum of 255 characters.                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | No              | String          | Directory for storing the resource.                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Access the DataArts Studio console and choose **Data Development**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query a list of resources.

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/resources

Example Response
----------------

-  Success response

   HTTP status code 200

   .. code-block::

      {
          "total":1,
          "resources":[
              {
                  "id":"b384b9e9ab9b4ee8994c8633aabc9505",
                  "name":"test",
                  "type":"jar",
                  "location":"obs://00000000dlf-test/hadoop-mapreduce-examples-2.4.1.jar",
                  "dependFiles":[
                      "obs://00000000dlf-test/depend1.jar",
                      "obs://00000000dlf-test/depend2.jar"
                  ],
                  "desc":"test",
                  "directory":"/resource"
              }
          ]
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.3051",
          "error_msg":"The request parameter is invalid."
      }
