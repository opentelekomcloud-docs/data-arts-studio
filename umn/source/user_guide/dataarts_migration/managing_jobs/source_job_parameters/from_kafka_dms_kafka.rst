:original_name: dataartsstudio_01_0058.html

.. _dataartsstudio_01_0058:

From Kafka/DMS Kafka
====================

If the source link of a job is the :ref:`Link to Kafka <dataartsstudio_01_0033>` or :ref:`Link to DMS Kafka <dataartsstudio_01_0038>`, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0058__en-us_topic_0108275337_table45985388113529>`.

.. _dataartsstudio_01_0058__en-us_topic_0108275337_table45985388113529:

.. table:: **Table 1** Parameter description

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                      | Example Value         |
   +=======================+==================================================================================================================================+=======================+
   | Topics                | One or more topics can be entered.                                                                                               | est1,est2             |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Offset                | Initial offset parameter                                                                                                         | Latest                |
   |                       |                                                                                                                                  |                       |
   |                       | -  **Latest**: Maximum offset, indicating that the latest data will be extracted.                                                |                       |
   |                       | -  **Earliest**: Minimum offset, indicating that the earliest data will be extracted.                                            |                       |
   |                       | -  **Submitted**: data that has been submitted                                                                                   |                       |
   |                       | -  **Time Range**: data within a specified time range                                                                            |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Permanent Running     | Whether a job runs permanently.                                                                                                  | Yes                   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Consumer Group ID     | Consumer group ID                                                                                                                | sumer-group           |
   |                       |                                                                                                                                  |                       |
   |                       | If you export data from DMS Kafka, enter any value for Kafka Platinum but a valid consumer group ID for Kafka Basic.             |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Data Format           | Format used for parsing data. The options are as follows:                                                                        | Binary                |
   |                       |                                                                                                                                  |                       |
   |                       | -  **Binary**: Data is transferred directly. It is not converted to another format. This setting is suitable for file migration. |                       |
   |                       | -  **CSV**: Source data will be migrated after being converted in CSV format.                                                    |                       |
   |                       | -  **JSON**: Source data will be migrated after being converted in JSON format.                                                  |                       |
   |                       | -  **CDC (DRS_JSON)**: Source data will be migrated after being converted in DRS_JSON format.                                    |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Field Delimiter       | The default value is space. To set the **Tab** key as the delimiter, set this parameter to **\\t**.                              | ,                     |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Max. Poll Records     | (Optional) Maximum number of records per poll                                                                                    | 100                   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Max. Poll Interval    | (Optional) Maximum interval between polls (seconds)                                                                              | 100                   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------+-----------------------+
