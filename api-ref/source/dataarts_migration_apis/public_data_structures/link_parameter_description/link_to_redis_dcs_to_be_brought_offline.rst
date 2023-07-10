:original_name: dataartsstudio_02_0272.html

.. _dataartsstudio_02_0272:

Link to Redis/DCS (to Be Brought Offline)
=========================================

Description
-----------

By creating a Redis link, you can extract data from or load data to the Redis server. By creating a DCS link, you can load data to Data Cache Service (DCS), but not extract data for DCS. The data can be stored in string or hash format.

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
                                   "name": "linkConfig.deploymentMode",
                                   "value": "Cluster"
                               },
                               {
                                   "name": "linkConfig.serverlist",
                                   "value": "10.120.84.149:7300"
                               },
                               {
                                   "name": "linkConfig.password",
                                   "value": "Add password here"
                               },
                               {
                                   "name": "linkConfig.dbIndex",
                                   "value": "0"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "redis_link",
               "connector-name": "redis-connector"
           }
       ]
   }

Link Parameters
---------------

+---------------------------+-----------------+-----------------+------------------------------------------------------------+
| Parameter                 | Mandatory       | Type            | Description                                                |
+===========================+=================+=================+============================================================+
| linkConfig.deploymentMode | Yes             | Enumeration     | Redis deployment mode. The options are as follows:         |
|                           |                 |                 |                                                            |
|                           |                 |                 | -  **Single**: single-node deployment                      |
|                           |                 |                 | -  **Cluster**: cluster deployment                         |
+---------------------------+-----------------+-----------------+------------------------------------------------------------+
| linkConfig.serverlist     | Yes             | String          | Server IP address list in *host1:port1;host2:port2* format |
+---------------------------+-----------------+-----------------+------------------------------------------------------------+
| linkConfig.password       | Yes             | String          | Password for logging in to the Redis server                |
+---------------------------+-----------------+-----------------+------------------------------------------------------------+
| linkConfig.dbIndex        | Yes             | String          | Redis database index                                       |
+---------------------------+-----------------+-----------------+------------------------------------------------------------+
