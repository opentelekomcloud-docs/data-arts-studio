:original_name: dataartsstudio_03_0122.html

.. _dataartsstudio_03_0122:

How Do I Use CDM to Export MySQL Data to an SQL File and Upload the File to an OBS Bucket?
==========================================================================================

Symptom
-------

How do I use CDM to export MySQL data to an SQL file and upload the file to an OBS bucket?

Solution
--------

CDM does not support this operation. You are advised to manually export a MySQL data file, enable the SFTP service on the server, and create a CDM job with SFTP as the source and OBS as the destination. Then you can execute the created job to transfer the file.
