:original_name: dataartsstudio_02_0278.html

.. _dataartsstudio_02_0278:

Link to CloudTable OpenTSDB
===========================

Description
-----------

By creating an OpenTSDB link, you can extract data from and load data to CloudTable OpenTSDB.

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
                   "name": "linkConfig.openTSDBQuorum",
                   "value": "opentsdb-sp8afz7bgbps5ur.cloudtable.com:4242"
                 },
                 {
                   "name": "linkConfig.securityMode",
                   "value": "UNSAFE"
                 }
               ],
               "name": "linkConfig"
             }
           ]
         },
         "name": "opentsdb",
         "connector-name": "opentsdb-connector"
       }
     ]
   }

Link Parameters
---------------

+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| Parameter                 | Mandatory       | Type            | Description                                                            |
+===========================+=================+=================+========================================================================+
| linkConfig.openTSDBQuorum | Yes             | String          | ZooKeeper Link of OpenTSDB                                             |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| linkConfig.securityMode   | Yes             | String          | Security or UNSAFE mode                                                |
|                           |                 |                 |                                                                        |
|                           |                 |                 | If you select **Security**, enter the project ID, username, and AK/SK. |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| linkConfig.user           | No              | String          | Username for accessing CloudTable                                      |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| linkConfig.ak             | No              | String          | AK for accessing CloudTable                                            |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| linkConfig.sk             | No              | String          | SK for accessing CloudTable                                            |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
| linkConfig.projectId      | No              | String          | Project ID of CloudTable                                               |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------+
