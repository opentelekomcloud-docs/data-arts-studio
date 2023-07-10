:original_name: dataartsstudio_01_0120.html

.. _dataartsstudio_01_0120:

From DLI
========

If the source link of a job is the :ref:`Link to DLI <dataartsstudio_01_0036>`, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0120__en-us_topic_0000001145417420_table5046103815165>`.

.. _dataartsstudio_01_0120__en-us_topic_0000001145417420_table5046103815165:

.. table:: **Table 1** Parameter description

   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter             | Description                                                                                            | Example Value          |
   +=======================+========================================================================================================+========================+
   | Resource Queue        | Resource queue to which the destination table belongs                                                  | cdm                    |
   |                       |                                                                                                        |                        |
   |                       | The default queue of DLI cannot be used for migration jobs. You need to create a SQL queue in DLI.     |                        |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------+
   | Database Name         | Name of the database to which data will be written                                                     | dli                    |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------+
   | Table Name            | Name of the table to which data will be written                                                        | car_detail             |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------+
   | Partition             | Partition information. This parameter is available if **Clear Data Before Import** is set to **true**. | year=2020,location=sun |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------+
