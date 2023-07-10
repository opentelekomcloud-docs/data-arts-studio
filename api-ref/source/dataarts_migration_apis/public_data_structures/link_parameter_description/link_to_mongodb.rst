:original_name: dataartsstudio_02_0271.html

.. _dataartsstudio_02_0271:

Link to MongoDB
===============

Description
-----------

By creating a MongoDB link, you can extract data from or load data to MongoDB.

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
                                   "name": "linkConfig.serverList",
                                   "value": "10.120.84.149:27017"
                               },
                               {
                                   "name": "linkConfig.database",
                                   "value": "DB_name"
                               },
                               {
                                   "name": "linkConfig.userName",
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
               "name": "mongo_link",
               "connector-name": "mongodb-connector"
           }
       ]
   }

Link Parameters
---------------

+-----------------------+-----------+--------+------------------------------------------------------------+
| Parameter             | Mandatory | Type   | Description                                                |
+=======================+===========+========+============================================================+
| linkConfig.serverList | Yes       | String | Server IP address list in *host1:port1;host2:port2* format |
+-----------------------+-----------+--------+------------------------------------------------------------+
| linkConfig.database   | Yes       | String | Name of the MongoDB database                               |
+-----------------------+-----------+--------+------------------------------------------------------------+
| linkConfig.userName   | Yes       | String | Username for logging in to the MongoDB server              |
+-----------------------+-----------+--------+------------------------------------------------------------+
| linkConfig.password   | Yes       | String | Password for logging in to the MongoDB server              |
+-----------------------+-----------+--------+------------------------------------------------------------+
