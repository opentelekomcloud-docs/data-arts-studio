:original_name: dataartsstudio_03_0050.html

.. _dataartsstudio_03_0050:

What Do I Do If Node Error Logs Cannot Be Viewed When a Job Fails?
==================================================================

Error logs are stored in OBS. The current account must have the OBS read permissions to view logs. You can check the OBS permissions and OBS bucket policies in IAM.

.. note::

   When you create a job, a bucket named **dlf-log-{projectID}** will be created by default. If the bucket exists, you do not need to create a bucket again.
