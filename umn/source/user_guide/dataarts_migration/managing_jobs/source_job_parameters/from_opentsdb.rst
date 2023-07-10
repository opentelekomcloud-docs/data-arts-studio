:original_name: dataartsstudio_01_0060.html

.. _dataartsstudio_01_0060:

From OpenTSDB
=============

If the source link of a job is the :ref:`Link to CloudTable OpenTSDB <dataartsstudio_01_0037>`, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0060__en-us_topic_0133467989_table5046103815165>`.

.. _dataartsstudio_01_0060__en-us_topic_0133467989_table5046103815165:

.. table:: **Table 1** Parameter description

   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
   | Parameter          | Description                                                                                              | Example Value           |
   +====================+==========================================================================================================+=========================+
   | Start Time         | Start time of the query. The value is a character string or timestamp in the format of *yyyyMMddHHmmdd*. | 20180920145505          |
   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
   | End Time           | (Optional) End time of the query. The value is a string or timestamp in the format of *yyyyMMddHHmmdd*.  | 20180921145505          |
   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
   | Metric             | Metric of the data to be migrated. You can specify a metric or select an existing metric in OpenTSDB.    | city.temp               |
   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
   | Aggregate Function | Aggregate function                                                                                       | sum                     |
   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
   | Tag                | (Optional) If you specify a tag, only the tagged data will be migrated.                                  | tagk1:tagv1,tagk2:tagv2 |
   +--------------------+----------------------------------------------------------------------------------------------------------+-------------------------+
