:original_name: dataartsstudio_03_0112.html

.. _dataartsstudio_03_0112:

What Do I Do If No Content Is Displayed in Job Logs?
====================================================

Symptom
-------

There is no content contained in the job log.

Cause Analysis
--------------

If the bucket directory for storing job logs has been configured in the workspace, check whether you have the global permission of OBS so that you can create and operate buckets.

Solutions
---------

Method 1: Create a bucket named dlf-log-{projectID} in OBS and grant the operation permission to the scheduling user.

.. note::

   The OBS path is only supported for OBS buckets and not for parallel file systems.

Method 2: Add global OBS administrator permission in IAM user permissions.
