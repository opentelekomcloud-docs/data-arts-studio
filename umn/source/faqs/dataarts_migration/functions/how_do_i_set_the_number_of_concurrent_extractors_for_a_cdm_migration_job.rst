:original_name: dataartsstudio_03_0336.html

.. _dataartsstudio_03_0336:

How Do I Set the Number of Concurrent Extractors for a CDM Migration Job?
=========================================================================

The number of concurrent extractors in a CDM migration job is related to the cluster specifications and table size. The value range is 1 to 300. If the value is too large, the extractors are queued.

You are advised to set 4 concurrent extractors for each 1 CU (1 CU = 1 vCPU and 4 GB), as listed in :ref:`Table 1 <dataartsstudio_03_0336__en-us_topic_0000001225868959_table17343144375319>`. You can also adjust the value as needed. If each row of the table contains less than or equal to 1 MB data, you can extract data concurrently. If each row contains more than 1 MB data, you are advised to extract data in a single thread.

.. note::

   -  When data is to be migrated to files, CDM does not support multiple concurrent tasks. In this case, set a single process to extract data.
   -  The number of concurrent extractors of a job is affected by **Maximum Concurrent Extractors** configured on the **Settings** page. The **Maximum Concurrent Extractors** parameter specifies the total number of concurrent extractions.

.. _dataartsstudio_03_0336__en-us_topic_0000001225868959_table17343144375319:

.. table:: **Table 1** Reference configurations of concurrent extractors

   ================== ================ =====================
   CDM Cluster Flavor vCPUs/Memory     Concurrent Extractors
   ================== ================ =====================
   cdm.large          8 vCPUs, 16 GB   16
   cdm.xlarge         16 vCPUs, 32 GB  32
   cdm.4xlarge        64 vCPUs, 128 GB 128
   ================== ================ =====================
