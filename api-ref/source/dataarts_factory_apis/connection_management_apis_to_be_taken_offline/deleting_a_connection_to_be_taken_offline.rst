:original_name: dataartsstudio_02_0054.html

.. _dataartsstudio_02_0054:

Deleting a Connection (to Be Taken Offline)
===========================================

.. note::

   The connection management capability is provided by Management Center. APIs of Management Center are recommended.

Function
--------

This API is used to delete a connection.

URI
---

-  URI format

   DELETE /v1/{project_id}/connections/{connection_name}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory | Type   | Description                                                                                                           |
      +=================+===========+========+=======================================================================================================================+
      | project_id      | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | connection_name | Yes       | String | Name of a connection.                                                                                                 |
      +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

Delete the connection.

.. code-block:: text

   DELETE /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections/connection1

Example Response
----------------

Success response

HTTP status code 204
