:original_name: ShowAvailabilityZones.html

.. _ShowAvailabilityZones:

Querying All AZs
================

Function
--------

This API is used to query all AZs of a CDM cluster.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

GET /v1.1/{project_id}/regions/{region_id}/availability_zones

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | region_id  | Yes       | String | Region ID. You can obtain it from the response message of the "Querying the Region List" API of the IAM service.        |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. This parameter is mandatory when :ref:`token authentication <dataartsstudio_02_0010>` is used. You can obtain it from the value of **X-Subject-Token** in the response message header returned by the "Obtaining a User Token" API of the IAM service. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------+-----------------------------------------------------------------------------------------------------------------+---------------------------+
   | Parameter      | Type                                                                                                            | Description               |
   +================+=================================================================================================================+===========================+
   | regionId       | String                                                                                                          | Region ID.                |
   +----------------+-----------------------------------------------------------------------------------------------------------------+---------------------------+
   | defaultAZ      | String                                                                                                          | Specifies the default AZ. |
   +----------------+-----------------------------------------------------------------------------------------------------------------+---------------------------+
   | availableZones | Array of :ref:`CdmClusterAvailabilityZone <showavailabilityzones__response_cdmclusteravailabilityzone>` objects | Indicates the AZ.         |
   +----------------+-----------------------------------------------------------------------------------------------------------------+---------------------------+

.. _showavailabilityzones__response_cdmclusteravailabilityzone:

.. table:: **Table 4** CdmClusterAvailabilityZone

   ================= ====== ======================
   Parameter         Type   Description
   ================= ====== ======================
   availableZoneId   String ID of the AZ
   availableZoneName String AZ name
   availableZoneCode String Indicates the AZ code.
   azStatus          String AZ status.
   type              String Indicates the AZ type.
   tags              Object AZ tag
   ================= ====== ======================

Example Requests
----------------

.. code-block:: text

   GET /v1.1/1551c7f6c808414d8e9f3c514a170f2e/regions/xxx-xxx-xxx/availability_zones

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "regionId" : "xxx-xxx-xxx",
     "defaultAZ" : "xxx-xxx-xxx",
     "availableZones" : [ {
       "availableZoneId" : "xxx-xxx-xxx",
       "availableZoneName" : "xxx-xxx-xxx",
       "availableZoneCode" : "xxx-xxx-xxx",
       "azStatus" : "Available",
       "type" : null,
       "tags" : null
     } ]
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------+
| Status Code | Description                                                                         |
+=============+=====================================================================================+
| 200         | The request is successful.                                                          |
+-------------+-------------------------------------------------------------------------------------+
| 400         | Request error.                                                                      |
+-------------+-------------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                              |
+-------------+-------------------------------------------------------------------------------------+
| 403         | No operation permission.                                                            |
+-------------+-------------------------------------------------------------------------------------+
| 404         | No resources found.                                                                 |
+-------------+-------------------------------------------------------------------------------------+
| 500         | Internal service error. For details about the returned error code, see Error Codes. |
+-------------+-------------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                                |
+-------------+-------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
