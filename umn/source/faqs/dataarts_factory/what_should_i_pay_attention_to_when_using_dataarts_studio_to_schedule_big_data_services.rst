:original_name: dataartsstudio_03_0149.html

.. _dataartsstudio_03_0149:

What Should I Pay Attention to When Using DataArts Studio to Schedule Big Data Services?
========================================================================================

Symptom
-------

Notes for scheduling big data services using DataArts Studio

Solution
--------

Lock management is unavailable for DLI and MRS. Therefore, if you perform read and write operations on the tables simultaneously, data conflict will occur and the operations will fail.

If you want to perform read and write operations on the data tables of big data services, use either of the following methods to perform serial operations:

-  Create a job with two nodes, one for the read operation and the other for the write operation, and execute the nodes in sequence to avoid conflicts.
-  Create a job for the read operation and another job for the write operation, and configure a dependency relationship between the two jobs to avoid conflicts.
