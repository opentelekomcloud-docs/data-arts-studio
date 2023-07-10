:original_name: dataartsstudio_01_0072.html

.. _dataartsstudio_01_0072:

To DLI
======

If the destination link of a job is the :ref:`Link to DLI <dataartsstudio_01_0036>`, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165>`.

.. _dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165:

.. table:: **Table 1** Parameter description

   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter                | Description                                                                                                    | Example Value          |
   +==========================+================================================================================================================+========================+
   | Resource Queue           | Resource queue to which the destination table belongs                                                          | cdm                    |
   |                          |                                                                                                                |                        |
   |                          | The default queue of DLI cannot be used for migration jobs. You need to create a SQL queue in DLI.             |                        |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Database Name            | Name of the database to which data will be written                                                             | dli                    |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Table Name               | Name of the table to which data will be written                                                                | car_detail             |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Clear Data Before Import | Whether to clear data in the destination table before data import                                              | No                     |
   |                          |                                                                                                                |                        |
   |                          | If this parameter is set to **Yes**, data in the destination table will be cleared before the task is started. |                        |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Data Clearing Mode       | This parameter is available when **Clear Data Before Import** is set to **Yes**.                               | TRUNCATE               |
   |                          |                                                                                                                |                        |
   |                          | **TRUNCATE**: deletes standard data.                                                                           |                        |
   |                          |                                                                                                                |                        |
   |                          | **INSERT_OVERWRITE**: overwrites existing data with inserted data.                                             |                        |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
   | Partition                | This parameter is available when **Clear Data Before Import** is set to **Yes**.                               | year=2020,location=sun |
   |                          |                                                                                                                |                        |
   |                          | When you enter partitions, data in these partitions will be cleared.                                           |                        |
   +--------------------------+----------------------------------------------------------------------------------------------------------------+------------------------+
