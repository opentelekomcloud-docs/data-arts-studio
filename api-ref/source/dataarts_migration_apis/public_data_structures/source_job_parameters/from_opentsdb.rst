:original_name: dataartsstudio_02_0294.html

.. _dataartsstudio_02_0294:

From OpenTSDB
=============

Sample JSON File
----------------

.. code-block::

         "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.start",
                   "value": "0"
                 },
                 {
                   "name": "fromJobConfig.metric",
                   "value": "city.temp"
                 },
                 {
                   "name": "fromJobConfig.aggregator",
                   "value": "sum"
                 },
                 {
                   "name": "fromJobConfig.columnList",
                   "value": "ps.timestample&metric&aggregator&dps.value"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| Parameter                | Mandatory | Type   | Description                                                                                              |
+==========================+===========+========+==========================================================================================================+
| fromJobConfig.start      | Yes       | String | Start time of the query. The value is a character string or timestamp in the format of *yyyyMMddHHmmdd*. |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| fromJobConfig.end        | No        | String | End time of the query. The value is a character string or timestamp in the format of *yyyyMMddHHmmdd*.   |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| fromJobConfig.metric     | Yes       | String | Metric of the data to be migrated                                                                        |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| fromJobConfig.aggregator | Yes       | String | Aggregate function                                                                                       |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| fromJobConfig.tags       | No        | String | Data tag. If you specify this parameter, only the tagged data will be migrated.                          |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
| fromJobConfig.columnList | No        | String | Field list                                                                                               |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------+
