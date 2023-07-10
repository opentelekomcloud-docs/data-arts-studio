:original_name: dataartsstudio_01_0028.html

.. _dataartsstudio_01_0028:

Link to an FTP or SFTP Server
=============================

The FTP/SFTP link is used to migrate files from the on-premises file server or ECS to database.

.. note::

   Only FTP servers running Linux are supported.

When connecting CDM to an FTP or SFTP server, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0028__en-us_topic_0108275400_table34037531171418>`.

.. _dataartsstudio_01_0028__en-us_topic_0108275400_table34037531171418:

.. table:: **Table 1** Parameter description

   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
   | Parameter            | Description                                                                                                        | Example Value  |
   +======================+====================================================================================================================+================+
   | Name                 | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for | ftp_link       |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
   | Host Name/IP Address | Host name or IP address of the FTP or SFTP server                                                                  | ftp.apache.org |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
   | Port                 | Port number of the FTP or SFTP server, which is 21 by default                                                      | 21             |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
   | Username             | Username used for logging in to the FTP or SFTP server                                                             | cdm            |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
   | Password             | Password used for logging in to the FTP or SFTP server                                                             | ``-``          |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+----------------+
