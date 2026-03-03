:original_name: dataartsstudio_01_0315.html

.. _dataartsstudio_01_0315:

Specifications
==============

Specifications of Exclusive DataArts DataService
------------------------------------------------

:ref:`Table 1 <dataartsstudio_01_0315__table139041229163716>` lists the specifications of DataArts DataService Exclusive.

.. _dataartsstudio_01_0315__table139041229163716:

.. table:: **Table 1** Specifications of Exclusive DataArts DataService

   =================== ===============================
   Instance            Max. APIs That Can Be Published
   =================== ===============================
   Small (x86 or ARM)  500
   Medium (x86 or ARM) 1,000
   Large (x86 or ARM)  2,000
   =================== ===============================

Specifications of API Return Data
---------------------------------

DataArts DataService is applicable to interactions involving a small amount of data, and is not applicable to returning a large amount of data through APIs. The following table lists the specifications of the data returned by DataArts DataService APIs.

.. table:: **Table 2** Restrictions on the number of data records returned by an API

   +-----------------+-----------------+-------------------+--------------------------------+
   | API Category    | Scenario        | Data Source       | Default Number of Data Records |
   +=================+=================+===================+================================+
   | Configuration   | Debugging       | DLI/MySQL/RDS/DWS | 10                             |
   +-----------------+-----------------+-------------------+--------------------------------+
   |                 | Call            | DLI/MySQL/RDS/DWS | 100                            |
   +-----------------+-----------------+-------------------+--------------------------------+
   | Script          | Test SQL        | N/A               | 10                             |
   +-----------------+-----------------+-------------------+--------------------------------+
   |                 | Debugging       | DLI               | -  Default pages: 100          |
   |                 |                 |                   | -  Custom pages: 1,000         |
   +-----------------+-----------------+-------------------+--------------------------------+
   |                 |                 | MySQL/RDS/DWS     | -  Default pages: 10           |
   |                 |                 |                   | -  Custom pages: 2,000         |
   +-----------------+-----------------+-------------------+--------------------------------+
   |                 | Call            | DLI               | -  Default pages: 100          |
   |                 |                 |                   | -  Custom pages: 1,000         |
   +-----------------+-----------------+-------------------+--------------------------------+
   |                 |                 | MySQL/RDS/DWS     | -  Default pages: 10           |
   |                 |                 |                   | -  Custom pages: 2,000         |
   +-----------------+-----------------+-------------------+--------------------------------+
