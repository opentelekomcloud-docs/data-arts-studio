:original_name: dataartsstudio_01_0030.html

.. _dataartsstudio_01_0030:

Link to MongoDB
===============

This link is used to transfer data from a third-party cloud MongoDB service or MongoDB created in the on-premises data center or ECS to a big data platform.

When connecting CDM to an on-premises MongoDB database, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0030__en-us_topic_0108275382_table34037531171418>`.

.. note::

   Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

.. _dataartsstudio_01_0030__en-us_topic_0108275382_table34037531171418:

.. table:: **Table 1** MongoDB link parameters

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Description                                                                                                                                                                                     | Example Value                     |
   +=======================+=================================================================================================================================================================================================+===================================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                              | mongodb_link                      |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Server List           | List of MongoDB server addresses. Enter each address in the format of *IP address or domain name of the database server*:*port number*, and separate the entered addresses with semicolons (;). | 192.168.0.1:7300;192.168.0.2:7301 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Database Name         | Name of the MongoDB database to be connected                                                                                                                                                    | DB_mongodb                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Username              | Username for logging in to MongoDB                                                                                                                                                              | cdm                               |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Password              | Password for logging in to MongoDB                                                                                                                                                              | ``-``                             |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Direct Connection     | This mode applies to the scenario where the network of the primary node is normal but the network of the replica node is abnormal.                                                              | No                                |
   |                       |                                                                                                                                                                                                 |                                   |
   |                       | .. note::                                                                                                                                                                                       |                                   |
   |                       |                                                                                                                                                                                                 |                                   |
   |                       |    -  Only one IP address can be configured for the server list in direct connection mode.                                                                                                      |                                   |
   |                       |    -  This mode applies to the scenario where the network of the primary node is normal but the network of the replica node is abnormal.                                                        |                                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Link Attributes       | Custom link attributes. The MongoDB attributes are supported. The unit is ms. The link attributes are as follows:                                                                               | socketTimeout=60000               |
   |                       |                                                                                                                                                                                                 |                                   |
   |                       | -  **socketTimeout**: The default value is **60000**.                                                                                                                                           |                                   |
   |                       | -  **maxWaitTime**: The default value is **10000**.                                                                                                                                             |                                   |
   |                       | -  **connectTimeout**. The default value is **10000**.                                                                                                                                          |                                   |
   |                       | -  **serverSelectionTimeout**: The default value is **5000**.                                                                                                                                   |                                   |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
