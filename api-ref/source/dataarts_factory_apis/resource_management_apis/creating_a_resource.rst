:original_name: dataartsstudio_02_0102.html

.. _dataartsstudio_02_0102:

Creating a Resource
===================

Function
--------

This API is used to create a resource. Types of nodes, including DLI Spark, MRS Spark, and MRS MapReduce, can reference files such as JAR and properties through resources.

URI
---

-  URI format

   POST /v1/{project_id}/resources

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
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
   | location        | Yes             | String          | OBS path for storing the resource file. When **type** is set to **jar**, **location** is the path for storing the main JAR package. The path contains a maximum of 1,023 characters. For example, obs://myBucket/test.jar                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependFiles     | No              | List<String>    | JAR package and properties file that the main JAR package depends on. The description contains a maximum of 10,240 characters.                                                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc            | No              | String          | Description of the resource. The description contains a maximum of 255 characters.                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | No              | String          | Directory for storing the resource.                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Access the DataArts Studio console and choose **Data Development**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   ========== ========= ====== ============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ============
   resourceId Yes       String Resource ID.
   ========== ========= ====== ============

Example Request
---------------

Create a resource named **test**. The resource type is **jar**. The OBS path where the resource file is located is **obs://dlf-test/hadoop-mapreduce-examples-2.4.1.jar**. The JAR package and properties file on which the resource's main JAR package depends are **obs://dlf-test/depend1.jar","obs://dlf-test/depend2.jar**. The description is **test**. The directory where the resource is located is **/resource**.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/resources
   {
       "name": "test",
       "type": "jar",
       "location": "obs://dlf-test/hadoop-mapreduce-examples-2.4.1.jar",
       "dependFiles": ["obs://dlf-test/depend1.jar","obs://dlf-test/depend2.jar"],
       "desc": "test",
       "directory":"/resource"
   }

Example Response
----------------

-  Success response

   .. code-block::

      {
          "resourceId":"3624d1c3-5df5-4f20-9af9-98eadad6c5f9"
      }

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6259",
          "error_msg":"Files of the same name exist in the directory."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
