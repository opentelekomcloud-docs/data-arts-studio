:original_name: dataartsstudio_01_0076.html

.. _dataartsstudio_01_0076:

Performance Tuning
==================

Overview
--------

In addition to increasing the source read speed, improving the destination write performance, and increasing the bandwidth, you can accelerate migration using the following methods:

-  **Use a CDM cluster of higher specifications**

   The NIC bandwidth and maximum number of concurrent extractors vary depending on the CDM cluster specifications. If you want to migrate data faster, or the metrics of your CDM cluster (such as the CPU usage, disk usage, and memory usage) are often high, you may need a CDM cluster with higher specifications for data migration.

-  **Use multiple CDM clusters**

   In some scenarios, you are advised to use multiple CDM clusters to share workloads to improve migration efficiency and stability. The following are some examples:

   -  Multiple CDM clusters are required for different purposes or by multiple business departments. For example, you may need one CDM cluster for running data migration jobs and another one as an agent for DataArts Studio Management Center.
   -  You want to migrate a large number of tables. In this case, you can use multiple CDM clusters to run jobs simultaneously to improve migration efficiency.
   -  The CPU usage, disk usage, and memory usage of the in-use CDM cluster are often high. In this case, you are advised to use multiple CDM clusters to shared workloads.

-  **Avoid running too many CDM jobs simultaneously**

   If the number of CDM jobs that run concurrently exceeds the maximum concurrent extractors for the CDM cluster, some jobs will be queued, and the migration will be prolonged.

   Avoid running too many jobs simultaneously, which may cause slow migration due to insufficient resources.

-  **Change concurrent extractors**

   If the number of tasks is small, adjusting the number of concurrent extractors is the best way to improve performance. You can set the number of concurrent extractors for a job and the maximum number of concurrent extractors for a cluster.

   CDM migrates data through data migration jobs. It works in the following way:

   #. When data migration jobs are submitted, CDM splits each job into multiple tasks based on the **Concurrent Extractors** parameter in the job configuration.

      .. note::

         Jobs for different data sources may be split based on different dimensions. Some jobs may not be split based on the **Concurrent Extractors** parameter.

   #. CDM submits the tasks to the running pool in sequence. Tasks (defined by **Maximum Concurrent Extractors**) run concurrently. Excess tasks are queued.

   By setting appropriate values for parameters **Concurrent Extractors** and **Maximum Concurrent Extractors**, you can accelerate migration. For details about how to change **Concurrent Extractors**, see :ref:`Changing Concurrent Extractors <dataartsstudio_01_0076__en-us_topic_0000001287646722_section6623192417013>`.

.. _dataartsstudio_01_0076__en-us_topic_0000001287646722_section6623192417013:

Changing Concurrent Extractors
------------------------------

#. The maximum number of concurrent extractors for a cluster varies depending on the CDM cluster flavor. You are advised to set the maximum number of concurrent extractors to twice the number of vCPUs of the CDM cluster.

   .. table:: **Table 1** Maximum number of concurrent extractors for a CDM cluster

      =========== ================ =============================
      Flavor      vCPUs/Memory     Maximum Concurrent Extractors
      =========== ================ =============================
      cdm.large   8 vCPUs, 16 GB   16
      cdm.xlarge  16 vCPUs, 32 GB  32
      cdm.4xlarge 64 vCPUs, 128 GB 128
      =========== ================ =============================


   .. figure:: /_static/images/en-us_image_0000002269116797.png
      :alt: **Figure 1** Setting Maximum Concurrent Extractors for a CDM cluster

      **Figure 1** Setting Maximum Concurrent Extractors for a CDM cluster

#. Configure the number of concurrent extractors based on the following rules:

   a. When data is to be migrated to files, CDM does not support multiple concurrent tasks. In this case, set a single process to extract data.
   b. If each row of the table contains less than or equal to 1 MB data, data can be extracted concurrently. If each row contains more than 1 MB data, it is recommended that data be extracted in a single thread.
   c. Set **Concurrent Extractors** for a job based on **Maximum Concurrent Extractors** for the cluster. It is recommended that **Concurrent Extractors** is less than **Maximum Concurrent Extractors**.
   d. If the destination is DLI, you are advised to set the number of concurrent extractors to 1. Otherwise, data may fail to be written.


   .. figure:: /_static/images/en-us_image_0000002234077588.png
      :alt: **Figure 2** Setting Concurrent Extractors for a job

      **Figure 2** Setting Concurrent Extractors for a job
