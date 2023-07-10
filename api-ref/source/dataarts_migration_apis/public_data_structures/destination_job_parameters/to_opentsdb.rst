:original_name: dataartsstudio_02_0307.html

.. _dataartsstudio_02_0307:

To OpenTSDB
===========

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "toJobConfig.metric",
                   "value": "city.temp"
                 },
                 {
                   "name": "toJobConfig.timeStamp",
                   "value": "0"
                 },
                 {
                   "name": "toJobConfig.tags",
                   "value": "tagk1:tagv1"
                 },
                 {
                   "name": "toJobConfig.columnList",
                   "value": "metric:1&tag:2&timestamp&value"
                 }
               ],
               "name": "toJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+------------------------+-----------+--------+---------------------------------------------------------------------------------------------+
| Parameter              | Mandatory | Type   | Description                                                                                 |
+========================+===========+========+=============================================================================================+
| toJobConfig.metric     | No        | String | Data metric                                                                                 |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------+
| toJobConfig.timeStamp  | No        | String | Data point. The value is a character string or timestamp in the format of *yyyyMMddHHmmdd*. |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------+
| toJobConfig.tags       | No        | String | Data tag                                                                                    |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------+
| toJobConfig.columnList | No        | String | Field list                                                                                  |
+------------------------+-----------+--------+---------------------------------------------------------------------------------------------+
