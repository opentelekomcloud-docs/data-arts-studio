:original_name: dataartsstudio_01_0122.html

.. _dataartsstudio_01_0122:

CDM Metrics
===========

Function
--------

Cloud Eye monitors the running status of cloud services and usage of each metric, and creates alarm rules for monitoring metrics.

After you create a CDM cluster, Cloud Eye automatically associates with CDM monitoring metrics to help you understand the running status of the CDM cluster.

-  This section describes the CDM metrics that can be monitored by Cloud Eye as well as their namespaces and dimensions.
-  For details about CDM monitoring metrics, see :ref:`Querying CDM Metrics <dataartsstudio_01_0124>`.
-  For details about how to set alarm rules, see :ref:`Configuring CDM Alarm Rules <dataartsstudio_01_0123>`.

Prerequisites
-------------

You have obtained required Cloud Eye permissions.

Namespace
---------

SYS.CDM

Metrics
-------

:ref:`Table 1 <dataartsstudio_01_0122__en-us_topic_0108275290_table77137321225>` lists the CDM metrics.

.. _dataartsstudio_01_0122__en-us_topic_0108275290_table77137321225:

.. table:: **Table 1** CDM metrics

   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | ID                  | Name                          | Description                                                                                                                                                                         | Value Range        | Monitored Object     | Monitoring Period (Raw Data) |
   +=====================+===============================+=====================================================================================================================================================================================+====================+======================+==============================+
   | bytes_in            | Bytes In                      | Measures the network inbound rate of the monitored object.                                                                                                                          | >= 0 bytes/s       | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: byte/s                                                                                                                                                                        |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | bytes_out           | Bytes Out                     | Measures the network outbound rate of the monitored object.                                                                                                                         | >= 0 bytes/s       | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: byte/s                                                                                                                                                                        |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | cpu_usage           | CPU Usage                     | Measures the CPU usage of the monitored object.                                                                                                                                     | 0% to 100%         | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | mem_usage           | Memory Usage                  | Measures the memory usage of the monitored object.                                                                                                                                  | 0% to 100%         | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | pg_pending_job      | Number of Queued Jobs         | Number of jobs in the PENDING state in the CDM instance.                                                                                                                            | >=0                | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: count                                                                                                                                                                         |                    |                      |                              |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | .. note::                                                                                                                                                                           |                    |                      |                              |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               |    This metric is available in version 2.10.0.300 and later versions.                                                                                                               |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | pending_threads     | Maximum Concurrent Extractors | Number of concurrent extraction threads in the Waiting state in the CDM instance.                                                                                                   | >=0                | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: count                                                                                                                                                                         |                    |                      |                              |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | .. note::                                                                                                                                                                           |                    |                      |                              |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               |    This metric is available in version 2.10.0.300 and later versions.                                                                                                               |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | disk_usage          | Disk Usage                    | Measures the disk usage of the physical server accommodating the monitored ECS, which is not accurate as that obtained on the monitored ECS.                                        | 0.001% to 90%      | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | disk_io             | Disk I/O                      | Measures the bytes read from and written to a disk per second on the physical server accommodating the monitored ECS, which is not accurate as those obtained on the monitored ECS. | 0 GB to 10 GB      | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: Byte/s                                                                                                                                                                        |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | tomcat_heap_usage   | Heap Memory Usage             | Measures the heap memory usage of the physical server accommodating the monitored ECS, which is not accurate as that obtained on the monitored ECS.                                 | 0.001% to 90%      | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | tomcat_connect      | Tomcat Concurrent Connections | Measures the number of Tomcat concurrent connections on the physical server.                                                                                                        | 0 to 2,147,483,647 | Cloud Data Migration | 1 minute                     |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | tomcat_thread_count | Tomat Threads                 | Measures the number of Tomcat threads on the physical server.                                                                                                                       | 0 to 2,147,483,647 | Cloud Data Migration | 1 minute                     |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | pg_connect          | Database Connections          | Measures the number of Postgres database connections on the physical server.                                                                                                        | 0 to 2,147,483,647 | Cloud Data Migration | 1 minute                     |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | pg_submission_row   | Rows                          | Measures the number of rows in the submission table of the Postgres database on the physical server.                                                                                | 0 to 2,147,483,647 | Cloud Data Migration | 1 minute                     |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | pg_failed_job_rate  | Job Failure Rate              | Measures the job failure rate of the sqoop process on the physical server.                                                                                                          | 0.001% to 100%     | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+
   | inodes_usage        | Inodes Usage                  | Measures the disk inodes usage of the physical server accommodating the monitored ECS, which is not accurate as that obtained on the monitored ECS.                                 | 0.001% to 100%     | Cloud Data Migration | 1 minute                     |
   |                     |                               |                                                                                                                                                                                     |                    |                      |                              |
   |                     |                               | Unit: %                                                                                                                                                                             |                    |                      |                              |
   +---------------------+-------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+----------------------+------------------------------+

Dimension
---------

=========== ============
Key         Value
=========== ============
instance_id CDM instance
=========== ============
