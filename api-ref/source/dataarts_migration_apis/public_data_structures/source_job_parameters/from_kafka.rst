:original_name: dataartsstudio_02_0292.html

.. _dataartsstudio_02_0292:

From Kafka
==========

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
              "configs": [
                  {
                      "inputs": [
                          {
                          "name": "fromJobConfig.topicsList",
                          "value": "est1,est2"
                          },
                          {
                          "name": "fromJobConfig.kafkaConsumerStrategy",
                          "value": "EARLIEST"
                          },
                          {
                          "name": "fromJobConfig.isPermanency",
                          "value": "true"
                          }
                      ],
                      "name": "fromJobConfig"
                  }
              ]
          }

Parameter Description
---------------------

+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| Parameter                           | Mandatory       | Type            | Description                                                                                                          |
+=====================================+=================+=================+======================================================================================================================+
| fromJobConfig.topicsList            | Yes             | String          | List of Kafka topics. Separate multiple topics by commas (,).                                                        |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.kafkaConsumerStrategy | Yes             | Enumeration     | Used to set the initial offset when data is pulled from Kafka. The options are as follows:                           |
|                                     |                 |                 |                                                                                                                      |
|                                     |                 |                 | -  **LATEST**: maximum offset, that is, the latest data                                                              |
|                                     |                 |                 | -  **EARLIEST**: minimum offset, that is, the earliest data                                                          |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.isPermanency          | Yes             | Boolean         | Whether to run permanently                                                                                           |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.groupId               | No              | String          | Consumer group ID                                                                                                    |
|                                     |                 |                 |                                                                                                                      |
|                                     |                 |                 | If you export data from DMS Kafka, enter any value for Kafka Platinum but a valid consumer group ID for Kafka Basic. |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.dataFormat            | Yes             | Enumeration     | Format used for parsing data. The options are as follows:                                                            |
|                                     |                 |                 |                                                                                                                      |
|                                     |                 |                 | -  **BINARY**: Data is transferred without being parsed, which is applicable to file migration.                      |
|                                     |                 |                 | -  **CSV**: Source data will be migrated after being parsed in CSV format.                                           |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.maxPollRecords        | No              | String          | Maximum number of requests that can be sent to Kafka each time                                                       |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.maxPollInterval       | No              | String          | Maximum interval between each poll                                                                                   |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.separator             | No              | String          | Field delimiter                                                                                                      |
+-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
