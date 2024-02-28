:original_name: dataartsstudio_02_0103.html

.. _dataartsstudio_02_0103:

Modifying a Resource
====================

Function
--------

This API is used to modify a specific resource. When modifying the resource, specify the resource ID.

-  The resource type and directory cannot be modified.

URI
---

-  URI format

   PUT /v1/{project_id}/resources/{resource_id}

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

.. table:: **Table 3** Resource parameters

   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                | Description                                                                                                                                                                                                                                                               |
   +=================+=================+=====================+===========================================================================================================================================================================================================================================================================+
   | name            | Yes             | String              | Name of the resource. The name contains a maximum of 32 characters, including only letters, numbers, underscores (_), and hyphens (-).                                                                                                                                    |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String              | Resource type.                                                                                                                                                                                                                                                            |
   |                 |                 |                     |                                                                                                                                                                                                                                                                           |
   |                 |                 |                     | -  archive                                                                                                                                                                                                                                                                |
   |                 |                 |                     | -  file                                                                                                                                                                                                                                                                   |
   |                 |                 |                     | -  jar                                                                                                                                                                                                                                                                    |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | location        | No              | String              | OBS path for storing the resource file. When **type** is set to **jar**, **location** is the path for storing the main JAR package. The path contains a maximum of 1,023 characters. For example, obs://myBucket/test.jar                                                 |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependFiles     | No              | List<String>        | JAR package and properties file that the main JAR package depends on. The description contains a maximum of 10,240 characters.                                                                                                                                            |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependPackages  | No              | List<DependPackage> | JAR package and properties file that the main JAR package depends on. The description contains a maximum of 10,240 characters. If this parameter and the **dependFiles** parameter are both available, this parameter is preferentially parsed.                           |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc            | No              | String              | Description of the resource. The description contains a maximum of 255 characters.                                                                                                                                                                                        |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | directory       | Yes             | String              | Directory for storing the resource.                                                                                                                                                                                                                                       |
   |                 |                 |                     |                                                                                                                                                                                                                                                                           |
   |                 |                 |                     | Access the DataArts Studio console and choose **Data Development**. In the left navigation pane, choose **Development** > **Develop Script**. In the directory tree of the script, you can view the created directories. The default directory is the **root** directory. |
   +-----------------+-----------------+---------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** DependPackage parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   type      No        String File type
   location  No        String File path
   ========= ========= ====== ===========

Response Parameters
-------------------

None.

Example Request
---------------

Modify a resource named **test**. The resource type is **jar**. The OBS path where the resource file is located is **obs://dlf-test/hadoop-mapreduce-examples-2.4.1.jar**. The JAR package and properties file on which the resource's main JAR package depends are **obs://dlf-test/depend1.jar","obs://dlf-test/depend2.jar**. The description is **test**. The directory where the resource is located is **/resource**.

.. code-block:: text

   PUT /v1/b384b9e9ab9b4ee8994c8633aabc9505/resources/3624d1c3-5df5-4f20-9af9-98eadad6c5f9
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

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6241",
          "error_msg":"The resource information does not exist."
      }
