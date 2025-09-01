:original_name: dataartsstudio_01_1628.html

.. _dataartsstudio_01_1628:

YASHAN Link Parameters
======================

:ref:`Table 1 <dataartsstudio_01_1628__en-us_topic_0000002024771290_table5321744015490>` describes the YASHAN link parameters.

.. note::

   Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

.. _dataartsstudio_01_1628__en-us_topic_0000002024771290_table5321744015490:

.. table:: **Table 1** YASHAN link parameters

   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter              | Description                                                                                                                                                                                   | Example Value         |
   +========================+===============================================================================================================================================================================================+=======================+
   | Name                   | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                            | yashan_link           |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Database Server        | IP address or domain name of the database to connect                                                                                                                                          | 192.168.0.1           |
   |                        |                                                                                                                                                                                               |                       |
   |                        | Click **Select** next to the text box to obtain the list of instances.                                                                                                                        |                       |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Port                   | Port of the database to connect                                                                                                                                                               | 1688                  |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Database Name          | Name of the database to connect                                                                                                                                                               | dbname                |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Username               | Username used for accessing the database This account must have the permissions required to read and write data tables and metadata.                                                          | cdm                   |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Password               | Password of the user                                                                                                                                                                          | ``-``                 |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Use Agent              | The agent function will be unavailable soon and does not need to be configured.                                                                                                               | ``-``                 |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Agent                  | The agent function will be unavailable soon and does not need to be configured.                                                                                                               | ``-``                 |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Reference Sign         | (Optional) Delimiter between the names of the referenced tables or columns. For details, see the product documentation of the corresponding database.                                         | "                     |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Driver Version         | Different types of relational databases adapt to different drivers. For details, see :ref:`How Do I Obtain a Driver? <dataartsstudio_01_0132__en-us_topic_0286032703_section631855342818>`    | ``-``                 |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Fetch Size             | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                                                             | 1000                  |
   |                        |                                                                                                                                                                                               |                       |
   |                        | Number of rows obtained by each request. Set this parameter based on the data source and the job's data size. If the value is too large or too small, the job execution time may be affected. |                       |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | SSL Encryption         | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                                                             | Yes                   |
   |                        |                                                                                                                                                                                               |                       |
   |                        | Select **Yes** if you want to enable SSL encrypted transmission.                                                                                                                              |                       |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Link Attributes        | (Optional) Click **Add** to add the JDBC connector attributes of multiple specified data sources. For details, see the JDBC connector document of the corresponding database.                 | socketTimeout=300     |
   |                        |                                                                                                                                                                                               |                       |
   |                        | The following are some examples:                                                                                                                                                              |                       |
   |                        |                                                                                                                                                                                               |                       |
   |                        | -  **socketTimeout**: JDBC connection timeout duration, in milliseconds                                                                                                                       |                       |
   |                        | -  **mysql.bool.type.transform**: whether to parse tinyint(1) to a Boolean value during data reading from a MySQL database. The default value is true.                                        |                       |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Link Secret Attributes | Custom secret attributes of the link                                                                                                                                                          | xxx=xxx               |
   +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
