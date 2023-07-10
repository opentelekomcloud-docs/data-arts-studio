:original_name: dataartsstudio_02_0270.html

.. _dataartsstudio_02_0270:

Link to an FTP or SFTP Server
=============================

Description
-----------

By creating an FTP or SFTP link, you are able to extract files from or load files to the FTP or SFTP server. Files in CSV, JSON, and binary format are supported.

Sample Link
-----------

.. code-block::

   {
       "links": [
           {
               "link-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "linkConfig.server",
                                   "value": "10.120.85.167"
                               },
                               {
                                   "name": "linkConfig.port",
                                   "value": "22"
                               },
                               {
                                   "name": "linkConfig.username",
                                   "value": "username"
                               },
                               {
                                   "name": "linkConfig.password",
                                   "value": "Add password here"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "sftp_link",
               "connector-name": "sftp-connector"
           }
       ]
   }

Link Parameters
---------------

Parameters for creating the FTP or SFTP link are the same.

+---------------------+-----------+--------+---------------------------------------------------+
| Parameter           | Mandatory | Type   | Description                                       |
+=====================+===========+========+===================================================+
| linkConfig.server   | Yes       | String | IP address of the FTP or SFTP server              |
+---------------------+-----------+--------+---------------------------------------------------+
| linkConfig.port     | Yes       | String | Port number of the FTP or SFTP server             |
+---------------------+-----------+--------+---------------------------------------------------+
| linkConfig.username | Yes       | String | Username for logging in to the FTP or SFTP server |
+---------------------+-----------+--------+---------------------------------------------------+
| linkConfig.password | Yes       | String | Password for logging in to the FTP or SFTP server |
+---------------------+-----------+--------+---------------------------------------------------+
