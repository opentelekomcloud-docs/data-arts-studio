:original_name: dataartsstudio_02_0280.html

.. _dataartsstudio_02_0280:

Link to DMS Kafka
=================

Description
-----------

By creating a DMS Kafka link, you can connect to Kafka Basic or Kafka Platinum on DMS. Currently, you can only export data from DMS Kafka to Cloud Search Service.

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
                   "name": "linkConfig.kafkaType",
                   "value": "Platinum"
                 },
                 {
                   "name": "linkConfig.brokerList",
                   "value": "100.85.121.112:9094,100.85.220.134:9094,100.85.127.232:9094"
                 },
                 {
                   "name": "linkConfig.isPlatinumInstance",
                   "value": "false"
                 }
               ],
               "name": "linkConfig"
             }
           ],
           "extended-configs": {
             "name": "linkConfig.extendedFields",
             "value": "e30="
           }
         },
         "name": "dms_kafka",
         "connector-name": "dms-kafka-connector"
       }
     ]
   }

Link Parameters
---------------

+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
| Parameter                     | Mandatory       | Type            | Description                                                                                                                |
+===============================+=================+=================+============================================================================================================================+
| linkConfig.kafkaType          | Yes             | Enumeration     | DMS Kafka edition. Currently, only the Platinum edition is available.                                                      |
|                               |                 |                 |                                                                                                                            |
|                               |                 |                 | -  **Basic**: DMS Kafka Basic                                                                                              |
|                               |                 |                 | -  **Platinum**: DMS Kafka Platinum                                                                                        |
+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
| linkConfig.brokerList         | Yes             | String          | The DMS endpoint is in **host1:port1,host2:port2** format.                                                                 |
+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
| linkConfig.isPlatinumInstance | Yes             | Boolean         | Whether to enable SSL authentication when a client connects to a Kafka premium instance.                                   |
|                               |                 |                 |                                                                                                                            |
|                               |                 |                 | If Kafka SASL_SSL is enabled, data will be encrypted before transmission for higher security, but performance will suffer. |
+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
| linkConfig.user               | No              | String          | Username for connecting to DMS Kafka. This parameter is displayed when **Kafka SASL_SSL** is enabled.                      |
+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password           | No              | String          | Password for connecting to DMS Kafka. This parameter is displayed when **Kafka SASL_SSL** is enabled.                      |
+-------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
