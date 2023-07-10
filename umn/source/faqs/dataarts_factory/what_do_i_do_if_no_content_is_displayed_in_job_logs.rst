:original_name: dataartsstudio_03_0112.html

.. _dataartsstudio_03_0112:

What Do I Do If No Content Is Displayed in Job Logs?
====================================================

Symptom
-------

There is no content contained in the job log.

Cause Analysis
--------------

Check whether the user has the global permission of the object storage service (OBS) in IAM to ensure that the user can create and operate buckets.

Solutions
---------

Method 1: Create a bucket named dlf-log-{projectID} in OBS and grant the operation permission to the scheduling user.

Method 2: Add global OBS administrator permission in IAM user permissions.
