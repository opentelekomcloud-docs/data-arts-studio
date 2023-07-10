:original_name: dataartsstudio_01_0032.html

.. _dataartsstudio_01_0032:

Link to Redis/DCS
=================

The Redis link is applicable to data migration of Redis created in the local data center or ECS. It is used to load data in the database or files to Redis.

The DCS link is used to load data from databases or files to Distributed Cache Service (DCS) on cloud. You are advised to use backup and restoration to migrate data from the third-party cloud Redis services to DCS.

When connecting CDM to an on-premises Redis database or DCS, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0032__en-us_topic_0108275391_table34037531171418>`.

.. _dataartsstudio_01_0032__en-us_topic_0108275391_table34037531171418:

.. table:: **Table 1** Parameter description

   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter               | Description                                                                                                                                                                                                                                                        | Example Value                     |
   +=========================+====================================================================================================================================================================================================================================================================+===================================+
   | Name                    | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                                                                                                 | redis_link                        |
   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Redis Deployment Method | Two deployment methods are available:                                                                                                                                                                                                                              | Single                            |
   |                         |                                                                                                                                                                                                                                                                    |                                   |
   |                         | -  **Single**: installation on a single-node system                                                                                                                                                                                                                |                                   |
   |                         | -  **Cluster**: installation on a cluster                                                                                                                                                                                                                          |                                   |
   |                         | -  **Proxy**: installation using a proxy                                                                                                                                                                                                                           |                                   |
   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Redis Server List       | List of MongoDB server addresses. Enter each address in the format of *IP address or domain name of the database server*:*port number*, and separate the entered addresses with semicolons (;).                                                                    | 192.168.0.1:7300;192.168.0.2:7301 |
   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Password                | Password used for logging in to Redis                                                                                                                                                                                                                              | ``-``                             |
   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Redis Database Index    | Index ID of a Redis database                                                                                                                                                                                                                                       | 0                                 |
   |                         |                                                                                                                                                                                                                                                                    |                                   |
   |                         | A Redis database is similar to a relational database. The total number of Redis databases can be set in the Redis configuration file. By default, there are 16 Redis databases. The database names are integers ranging from 0 to 15 instead of character strings. |                                   |
   +-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
