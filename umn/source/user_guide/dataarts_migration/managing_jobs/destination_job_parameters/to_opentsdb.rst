:original_name: dataartsstudio_01_0074.html

.. _dataartsstudio_01_0074:

To OpenTSDB
===========

If the destination link of a job is the :ref:`Link to CloudTable OpenTSDB <dataartsstudio_01_0037>`, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0074__en-us_topic_0133467990_table5046103815165>`.

.. _dataartsstudio_01_0074__en-us_topic_0133467990_table5046103815165:

.. table:: **Table 1** Parameter description

   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | Parameter | Description                                                                                  | Example Value          |
   +===========+==============================================================================================+========================+
   | Metric    | (Optional) You can specify a metric or select an existing metric in OpenTSDB.                | city.temp              |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | Time      | (Optional) Data point. The value is a string or timestamp in the format of *yyyyMMddHHmmdd*. | 1598870800             |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | Tag       | (Optional) Data tag                                                                          | tagk:tagv, tagk2:tagv2 |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+
