:original_name: dataartsstudio_03_0124.html

.. _dataartsstudio_03_0124:

What Is the Number of Concurrent Jobs for Different CDM Cluster Versions?
=========================================================================

:ref:`Table 1 <dataartsstudio_03_0124__en-us_topic_0000001117256696_table164631842121720>` lists the number of concurrent jobs for different CDM cluster versions.

.. _dataartsstudio_03_0124__en-us_topic_0000001117256696_table164631842121720:

.. table:: **Table 1** Concurrent tasks

   +---------------------------+---------------------------------------+--------------------------------------+---------------------------------------+
   | Flavor                    | cdm.large                             | cdm.xlarge                           | cdm.4xlarge                           |
   +===========================+=======================================+======================================+=======================================+
   | Specifications            | Node quantity: 1                      | Node quantity: 1                     | Node quantity: 1                      |
   |                           |                                       |                                      |                                       |
   |                           | vCPUs \| memory: 8 vCPUs \| 16 GB     | vCPUs \| memory: 16 vCPUs \| 32 GB   | vCPUs \| memory: 64 vCPUs \| 128 GB   |
   |                           |                                       |                                      |                                       |
   |                           | Baseline/Max. bandwidth: 0.8/3 Gbit/s | Baseline/Max. bandwidth: 4/10 Gbit/s | Baseline/Max. bandwidth: 36/40 Gbit/s |
   +---------------------------+---------------------------------------+--------------------------------------+---------------------------------------+
   | Number of concurrent jobs | 30                                    | 100                                  | 300                                   |
   +---------------------------+---------------------------------------+--------------------------------------+---------------------------------------+

You are advised to use multiple CDM clusters in the following and other scenarios as needed:

-  Use different CDM clusters for different purposes, for example, for data migration jobs or as connection agents in the DataArts Studio Management Center.
-  Use different CDM clusters for different business departments, such as the finance department and online store.
