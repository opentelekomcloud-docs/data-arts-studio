:original_name: dataartsstudio_01_0118_0.html

.. _dataartsstudio_01_0118_0:

MD5 Verification
================

CDM extracts data from the migration source and writes the data to the migration destination. :ref:`Figure 1 <dataartsstudio_01_0118_0__en-us_topic_0000001197579313_en-us_topic_0000001151779052_en-us_topic_0108275377_fig4667102414522>` shows the migration mode when files are migrated to OBS.

.. _dataartsstudio_01_0118_0__en-us_topic_0000001197579313_en-us_topic_0000001151779052_en-us_topic_0108275377_fig4667102414522:

.. figure:: /_static/images/en-us_image_0000002270789488.png
   :alt: **Figure 1** Migrating files to OBS

   **Figure 1** Migrating files to OBS

During the process, CDM uses MD5 to verify file consistency.

-  **Extract**

   -  The migration source can be OBS, HDFS, FTP, SFTP, or HTTP. It can check whether the files extracted by CDM are consistent with source files.
   -  This function is controlled by the **MD5 File Extension** parameter (available when **File Format** is set to **Binary**) in **Source Job Configuration**. Set this parameter to the file name extension of the MD5 file in the source file system.
   -  If a source file **build.sh** and a file for saving MD5 value **build.sh.md5** are located in the same directory, and **MD5 File Extension** is configured, only the file **build.sh.md5** is migrated to the destination. Files without the MD5 value or whose MD5 values do not match fail to be migrated, and the MD5 file is not migrated.
   -  If **MD5 File Extension** is not configured, all files are migrated.

-  **Write**

   -  Currently, this function can be used only when OBS serves as the migration destination. It can check whether the files written to OBS are consistent with those extracted from CDM.
   -  This function is controlled by the **Validate MD5 Value** parameter in **Destination Job Configuration**. After the files are read and written to OBS, the MD5 value in the HTTP header is used to verify the files on OBS and the verification result is written to an OBS bucket (the bucket can be the one that does not store migration files). If the migration source does not have the MD5 file, the verification will not be performed.

.. note::

   -  When files are migrated to a file system, only the extracted files are verified.
   -  When files are migrated to OBS, both the extracted files and files written to OBS are verified.
   -  If MD5 verification is used, :ref:`KMS encryption <dataartsstudio_01_0117_0>` cannot be used.
