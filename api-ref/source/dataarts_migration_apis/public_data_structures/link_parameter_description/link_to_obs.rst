:original_name: dataartsstudio_02_0263.html

.. _dataartsstudio_02_0263:

Link to OBS
===========

Description
-----------

By creating an OBS link, you can extract files from or load files to OBS. Files in CSV, JSON, and binary format are supported.

Sample Link
-----------

The following is the message body of a sample link. You are advised to store the AK and SK in ciphertext in the configuration file or environment variables and decrypt them when needed to ensure security.

.. code-block::

   {
       "links": [
           {
               "link-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "linkConfig.storageType",
                                   "value": "OBS"
                               },
                               {
                                   "name": "linkConfig.server",
                                   "value": "10.121.16.183"
                               },
                               {
                                   "name": "linkConfig.port",
                                   "value": "443"
                               },
                               {
                                   "name":"linkConfig.accessKey",
                                   "value": "<YOUR AK>"
                               },
                               {
                                   "name":"linkConfig.securityKey",
                                   "value":"<YOUR SK>"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "obs_link",
               "connector-name": "obs-connector"
           }
       ]
   }

Link Parameters
---------------

+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter              | Mandatory | Type   | Description                                                                                                                                       |
+========================+===========+========+===================================================================================================================================================+
| linkConfig.storageType | Yes       | String | Storage class of an object                                                                                                                        |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.server      | Yes       | String | Endpoint of the OBS server.                                                                                                                       |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.port        | Yes       | String | Data transmission port. The HTTPS port number is 443 and the HTTP port number is 80.                                                              |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.accessKey   | Yes       | String | AK. You are advised to store it in ciphertext in the configuration file or an environment variable and decrypt it when needed to ensure security. |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.securityKey | Yes       | String | SK. You are advised to store it in ciphertext in the configuration file or an environment variable and decrypt it when needed to ensure security. |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
