:original_name: dataartsstudio_03_0124.html

.. _dataartsstudio_03_0124:

What Is the Number of Concurrent Jobs for Different CDM Cluster Versions?
=========================================================================

CDM migrates data through data migration jobs. It works in the following way:

#. When data migration jobs are submitted, CDM splits each job into multiple tasks based on the **Concurrent Extractors** parameter in the job configuration.

   .. note::

      Jobs for different data sources may be split based on different dimensions. Some jobs may not be split based on the **Concurrent Extractors** parameter.

#. CDM submits the tasks to the running pool in sequence. Tasks (defined by **Maximum Concurrent Extractors**) run concurrently. Excess tasks are queued.

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


   .. figure:: /_static/images/en-us_image_0000002305405497.png
      :alt: **Figure 1** Setting Maximum Concurrent Extractors for a CDM cluster

      **Figure 1** Setting Maximum Concurrent Extractors for a CDM cluster

#. Configure the number of concurrent extractors based on the following rules:

   a. When data is to be migrated to files, CDM does not support multiple concurrent tasks. In this case, set a single process to extract data.
   b. If each row of the table contains less than or equal to 1 MB data, data can be extracted concurrently. If each row contains more than 1 MB data, it is recommended that data be extracted in a single thread.
   c. Set **Concurrent Extractors** for a job based on **Maximum Concurrent Extractors** for the cluster. It is recommended that **Concurrent Extractors** is less than **Maximum Concurrent Extractors**.
   d. If the destination is DLI, you are advised to set the number of concurrent extractors to 1. Otherwise, data may fail to be written.


   .. figure:: /_static/images/en-us_image_0000002270788772.png
      :alt: **Figure 2** Setting Concurrent Extractors for a job

      **Figure 2** Setting Concurrent Extractors for a job
