:original_name: dataartsstudio_02_0291.html

.. _dataartsstudio_02_0291:

From DIS
========

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
             "configs": [
                 {
                     "inputs": [
                         {
                            "name": "fromJobConfig.streamName",
                            "value": "cdm"
                         },
                         {
                            "name": "fromJobConfig.disConsumerStrategy",
                            "value": "FROM_LAST_STOP"
                         },
                         {
                            "name": "fromJobConfig.isPermanency",
                            "value": "true"
                         },
                         {
                            "name": "fromJobConfig.maxPollRecords",
                            "value": "100"
                         },
                         {
                            "name": "fromJobConfig.shardId",
                            "value": "0"
                         },
                         {
                            "name": "fromJobConfig.dataFormat",
                            "value": "BINARY"
                         },
                         {
                            "name": "fromJobConfig.separator",
                            "value": ","
                         }
                     ],
                     "name": "fromJobConfig"
                 }
             ]
         }

Parameter Description
---------------------

+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| Parameter                         | Mandatory       | Type            | Description                                                                                       |
+===================================+=================+=================+===================================================================================================+
| fromJobConfig.streamName          | Yes             | String          | DIS stream name                                                                                   |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.disConsumerStrategy | Yes             | Enumeration     | Used to set the initial offset when data is pulled from DIS. The options are as follows:          |
|                                   |                 |                 |                                                                                                   |
|                                   |                 |                 | -  **LATEST**: maximum offset, that is, the latest data                                           |
|                                   |                 |                 | -  **FROM_LAST_STOP**: data after the last stop                                                   |
|                                   |                 |                 | -  **EARLIEST**: minimum offset, that is, the earliest data                                       |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.isPermanency        | Yes             | Boolean         | Whether to run permanently                                                                        |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.maxPollRecords      | No              | String          | Maximum number of requests that can be sent to DIS each time                                      |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.shardId             | Yes             | String          | ID of the DIS partition. You can enter multiple partition IDs, which are separated by commas (,). |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.dataFormat          | Yes             | Enumeration     | Format used for parsing data. The options are as follows:                                         |
|                                   |                 |                 |                                                                                                   |
|                                   |                 |                 | -  **BINARY**: Data is transferred without being parsed, which is applicable to file migration.   |
|                                   |                 |                 | -  **CSV**: Source data will be migrated after being parsed in CSV format.                        |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.separator           | No              | String          | Field delimiter                                                                                   |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
| fromJobConfig.appName             | No              | String          | Unique identifier of the consumer application                                                     |
+-----------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
