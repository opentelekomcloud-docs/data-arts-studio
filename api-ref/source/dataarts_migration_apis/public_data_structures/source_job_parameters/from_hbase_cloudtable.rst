:original_name: dataartsstudio_02_0286.html

.. _dataartsstudio_02_0286:

From HBase/CloudTable
=====================

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.table",
                   "value": "rf_from"
                 },
                 {
                   "name": "fromJobConfig.columnFamilies",
                   "value": "rowkey&f"
                 },
                 {
                   "name": "fromJobConfig.columns",
                   "value": "rowkey:rowkey&f:_small"
                 },
                 {
                   "name": "fromJobConfig.formats",
                   "value": {
                     "f:_date": "yyyy-MM-dd",
                     "f:_timestamp": "yyyy-MM-dd HH:mm:ss"
                   }
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

-  HBase/CloudTable job parameter description

   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory       | Type            | Description                                                                                                                                                |
   +==============================+=================+=================+============================================================================================================================================================+
   | fromJobConfig.table          | Yes             | String          | Name of the table from which data is extracted. For example, **cdm**.                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.columnFamilies | No              | String          | Column family to which the data to be extracted belongs                                                                                                    |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.columns        | No              | String          | Columns to be extracted. Use **&** to separate column numbers and **:** to separate column families and columns. For example, **cf1:c1&cf2:c2**.           |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.isSplit        | No              | Boolean         | Whether to split the rowkey. For example, **true**.                                                                                                        |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.delimiter      | No              | String          | Delimiter used for splitting rowkeys. If this parameter is not set, row keys will not be split. For example, vertical bars (|).                            |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.startTime      | No              | String          | Minimum timestamp of the time range (the time point is included). The format is *yyyy-MM-dd hh:mm:ss*.                                                     |
   |                              |                 |                 |                                                                                                                                                            |
   |                              |                 |                 | Only the data created at this point in time and later is extracted.                                                                                        |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.endTime        | No              | String          | Maximum timestamp of the time range (the time point is not included). The format is *yyyy-MM-dd hh:mm:ss*.                                                 |
   |                              |                 |                 |                                                                                                                                                            |
   |                              |                 |                 | Only the data created before this point in time is extracted.                                                                                              |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.formats        | No              | Data structure  | Time format. For details, see :ref:`Description of the fromJobConfig.formats parameter <dataartsstudio_02_0286__en-us_topic_0108272812_li45055411174737>`. |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _dataartsstudio_02_0286__en-us_topic_0108272812_li45055411174737:

   Description of the **fromJobConfig.formats** parameter

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   name      Yes       String Column number. For example, **1**.
   value     Yes       String Time format. For example, *yyyy-MM-dd*.
   ========= ========= ====== =======================================
