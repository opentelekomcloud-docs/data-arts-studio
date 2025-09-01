:original_name: dataartsstudio_01_0028.html

.. _dataartsstudio_01_0028:

FTP/SFTP Link Parameters
========================

The FTP/SFTP link is used to migrate files from the on-premises file server or ECS to a database.

.. note::

   -  Only FTP servers running Linux are supported.
   -  Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

When connecting CDM to an FTP or SFTP server, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0028__en-us_topic_0108275400_table34037531171418>`.

.. _dataartsstudio_01_0028__en-us_topic_0108275400_table34037531171418:

.. table:: **Table 1** FTP/SFTP link parameters

   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter                     | Description                                                                                                                                                        | Example Value         |
   +===============================+====================================================================================================================================================================+=======================+
   | Name                          | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                 | ftp_link              |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Host Name/IP Address          | Host name or IP address of the FTP or SFTP server                                                                                                                  | ftp.apache.org        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Port                          | Port number of the FTP or SFTP server. The default value is **21** for FTP and **22** for SFTP.                                                                    | 21                    |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Username                      | Username used for logging in to the FTP or SFTP server                                                                                                             | cdm                   |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Password                      | Password used for logging in to the FTP or SFTP server                                                                                                             | ``-``                 |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | FTP File Name controlEncoding | This parameter is available for a FTP link.                                                                                                                        | ISO-8859-1            |
   |                               |                                                                                                                                                                    |                       |
   |                               | It indicates the controlEncoding file name encoding configuration of ftp-client. The value can be **ISO-8859-1** or **UFT8**. The default value is **ISO-8859-1**. |                       |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
