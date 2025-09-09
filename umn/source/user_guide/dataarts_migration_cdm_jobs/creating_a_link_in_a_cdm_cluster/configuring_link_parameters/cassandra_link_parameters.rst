:original_name: dataartsstudio_01_004501.html

.. _dataartsstudio_01_004501:

Cassandra Link Parameters
=========================

.. note::

   -  Cassandra is not supported in version 2.9.3.300 or later.
   -  Do not change the password or user when a job is running. If you do so, the password will not take effect immediately and the job will fail.

.. table:: **Table 1** Parameter description

   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Parameter                   | Description                                                                                                                                           | Example Value           |
   +=============================+=======================================================================================================================================================+=========================+
   | Name                        | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                    | mongodb_link            |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Service node                | An address of one node or addresses of multiple nodes. Separate addresses with semicolons (;). You are advised to configure multiple nodes at a time. | 192.168.0.1;192.168.0.2 |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Port                        | Port number of the Cassandra node to be connected.                                                                                                    | 9042                    |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Username                    | User name for connecting to Cassandra.                                                                                                                | cdm                     |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Password                    | Password for connecting to Cassandra.                                                                                                                 | ``-``                   |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Connection timeout duration | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                     | 5                       |
   |                             |                                                                                                                                                       |                         |
   |                             | Connection timeout interval, in seconds.                                                                                                              |                         |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
   | Read timeout duration       | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                     | 12                      |
   |                             |                                                                                                                                                       |                         |
   |                             | Read timeout interval, in seconds. If the value is less than or equal to 0, no timeout occurs.                                                        |                         |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
