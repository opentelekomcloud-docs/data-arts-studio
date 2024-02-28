:original_name: dataartsstudio_02_0104.html

.. _dataartsstudio_02_0104:

Querying a Resource
===================

Function
--------

This API is used to query resource details. A resource contains various files such as JAR, ZIP, and properties files. A created resource can be used in job nodes such as DLI Spark and MRS Spark.

URI
---

-  URI format

   GET /v1/{project_id}/resources/{resource_id}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                                                                     |
      +=============+===========+========+=================================================================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.                                           |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_id | Yes       | String | Resource ID. For details about how to obtain the resource ID, see :ref:`Querying a Resource List <dataartsstudio_02_0105>`. The returned ID is **resource_id**. |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Resource parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================================================================+
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
   | desc            | No              | String          | Description of the resource. The description contains a maximum of 255 characters.                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | No              | String          | Directory for storing the resource.                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Access the DataArts Studio console and choose **Data Development**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

View resource details.

.. code-block:: text

   GET /v1/b384b9e9ab9b4ee8994c8633aabc9505/resources/3624d1c3-5df5-4f20-9af9-98eadad6c5f9

Example Response
----------------

-  Success response

   .. code-block::

      {
          "name": "test",
          "type": "jar",
          "location": "obs://dlf-test/hadoop-mapreduce-examples-2.4.1.jar",
          "dependFiles": ["obs://dlf-test/depend1.jar","obs://dlf-test/depend2.jar"],
          "desc": "test",
          "directory":"/resource"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6241",
          "error_msg":"The resource information does not exist."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
