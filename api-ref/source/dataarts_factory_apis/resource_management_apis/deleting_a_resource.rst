:original_name: dataartsstudio_02_0061.html

.. _dataartsstudio_02_0061:

Deleting a Resource
===================

Function
--------

This API is used to delete a resource.

URI
---

-  URI format

   DELETE /v1/{project_id}/resources/{resource_id}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
      +=================+=================+=================+=============================================================================================================================+
      | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
      | resource_id     | Yes             | String          | Resource ID. For details about how to obtain the resource ID, see :ref:`Querying a Resource List <dataartsstudio_02_0105>`. |
      |                 |                 |                 |                                                                                                                             |
      |                 |                 |                 | The returned ID is **resource_id**.                                                                                         |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

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

None.

Example Request
---------------

.. code-block:: text

   DELETE /v1/b384b9e9ab9b4ee8994c8633aabc9505/resources/3624d1c3-5df5-4f20-9af9-98eadad6c5f9

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

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
