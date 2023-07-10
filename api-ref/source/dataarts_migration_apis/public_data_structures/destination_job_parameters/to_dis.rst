:original_name: dataartsstudio_02_0306.html

.. _dataartsstudio_02_0306:

To DIS
======

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "toJobConfig.streamName",
                   "value": "cdm"
                 },
                 {
                   "name": "toJobConfig.separator",
                   "value": ","
                 },
                 {
                   "name": "toJobConfig.identifierEnclose",
                   "value": "'"
                 }
               ],
               "name": "toJobConfig"
             }
           ]
         }

Parameter description
---------------------

+-------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
| Parameter                     | Mandatory | Type   | Description                                                                                                  |
+===============================+===========+========+==============================================================================================================+
| toJobConfig.streamName        | Yes       | String | DIS stream name                                                                                              |
+-------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
| toJobConfig.separator         | No        | String | Field separator. The default value is a space.                                                               |
+-------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
| toJobConfig.identifierEnclose | No        | String | Delimiter used to separate referenced table names or column names. By default, this parameter is left blank. |
+-------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
