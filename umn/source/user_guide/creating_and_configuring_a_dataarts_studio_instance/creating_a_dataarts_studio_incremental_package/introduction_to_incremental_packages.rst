:original_name: dataartsstudio_01_0139.html

.. _dataartsstudio_01_0139:

Introduction to Incremental Packages
====================================

DataArts Studio provides basic and incremental packages. If the basic package cannot meet your demands, you need to create an incremental package.

DataArts Studio Incremental Packages
------------------------------------

:ref:`Table 1 <dataartsstudio_01_0139__table53861148017>` lists the incremental packages provided by DataArts Studio.

.. _dataartsstudio_01_0139__table53861148017:

.. table:: **Table 1** Incremental packages

   +------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Package Type                                                           | Description                                                                                                                                                                                                                                                 | Scenario                                                                                                                       |
   +========================================================================+=============================================================================================================================================================================================================================================================+================================================================================================================================+
   | :ref:`DataArts Migration incremental package <dataartsstudio_01_0119>` | A DataArts Migration (that is, CDM) incremental package provides resources for a CDM cluster. When you create a CDM incremental package, the system automatically creates a CDM cluster based on the specifications you select for the incremental package. | A DataArts Studio instance does not contain CDM clusters. To use CDM clusters, create DataArts Migration incremental packages. |
   |                                                                        |                                                                                                                                                                                                                                                             |                                                                                                                                |
   |                                                                        | CDM clusters can be used in the following scenarios:                                                                                                                                                                                                        |                                                                                                                                |
   |                                                                        |                                                                                                                                                                                                                                                             |                                                                                                                                |
   |                                                                        | -  Data migration jobs can be created and run in CDM clusters to migrate data to the cloud or import data to the data lake.                                                                                                                                 |                                                                                                                                |
   |                                                                        | -  CDM clusters can be used as agents of data connections in Management Center, which enable communications between DataArts Studio instances and data sources.                                                                                             |                                                                                                                                |
   +------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
