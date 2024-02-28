:original_name: dataartsstudio_02_0057.html

.. _dataartsstudio_02_0057:

Deleting a Script
=================

Function
--------

This API is used to delete a specific script.

URI
---

-  URI format

   DELETE /v1/{project_id}/scripts/{script_name}

-  Parameter description

   .. table:: **Table 1** URI parameters

      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                           |
      +=============+===========+========+=======================================================================================================================+
      | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | script_name | Yes       | String | Script name.                                                                                                          |
      +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Parameters

   +-----------+-----------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type              | Description                                                                                                                                                 |
   +===========+===========+===================+=============================================================================================================================================================+
   | approvers | No        | List<JobApprover> | Script approver. This parameter is required if the review function is enabled. For details, see :ref:`Table 4 <dataartsstudio_02_0057__table943565132314>`. |
   +-----------+-----------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_02_0057__table943565132314:

.. table:: **Table 4** Approver attributes

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   approverName Yes       String Approver name
   ============ ========= ====== =============

Response Parameters
-------------------

None.

Example Request
---------------

.. code-block:: text

   DELETE /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts/echoTime

Delete a script when the review function is enabled.

.. code-block:: text

   DELETE /v1/b384b9e9ab9b4ee8994c8633aabc9505/scripts/echoTime
   {
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

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6201",
          "error_msg":"The script does not exist."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
