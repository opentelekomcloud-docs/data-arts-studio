:original_name: dataartsstudio_01_0289.html

.. _dataartsstudio_01_0289:

From LogHub (SLS)
=================

If the source link of a job is a :ref:`LogHub (SLS) link <dataartsstudio_01_0288>`, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0289__en-us_topic_0000001447045200_table08521276117>`.

.. _dataartsstudio_01_0289__en-us_topic_0000001447045200_table08521276117:

.. table:: **Table 1** Parameter description

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                  | Example Value         |
   +=======================+==============================================================================================================================================+=======================+
   | Source Link Name      | LogHub (SLS) link                                                                                                                            | sls_link              |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | LogStore              | Name of the target logstore                                                                                                                  | ``-``                 |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | BatchSize             | Number of data records obtained from the log service at a time                                                                               | 128                   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | BeginDateTime         | Start time of data consumption, that is, the time when log data reaches LogHub (SLS). The value is a time string in *yyyyMMddHHmmss* format. | 20220113013000        |
   |                       |                                                                                                                                              |                       |
   |                       | .. note::                                                                                                                                    |                       |
   |                       |                                                                                                                                              |                       |
   |                       |    This parameter must be used together with **EndDateTime**. The value range includes **BeginDateTime** and excludes **EndDateTime**.       |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | EndDateTime           | End time of data consumption. The value is a string in *yyyyMMddHHmmss* format.                                                              | 20220213013000        |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
