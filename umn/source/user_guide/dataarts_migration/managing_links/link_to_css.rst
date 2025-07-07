:original_name: dataartsstudio_01_0035.html

.. _dataartsstudio_01_0035:

Link to CSS
===========

Cloud Search Service (CSS) is a fully hosted distributed search service powered by open-source Elasticsearch. CSS links can be used to migrate log files and database records to CSS for search and analysis using Elasticsearch.

.. note::

   -  Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

:ref:`Table 1 <dataartsstudio_01_0035__en-us_topic_0108275341_table1714082724917>` lists the parameters for a CSS link.

.. _dataartsstudio_01_0035__en-us_topic_0108275341_table1714082724917:

.. table:: **Table 1** CSS link parameters

   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter                    | Description                                                                                                                                                                                 | Example Value                     |
   +==============================+=============================================================================================================================================================================================+===================================+
   | Name                         | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                          | css_link                          |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Elasticsearch Server List    | IP addresses or domain names (including the port numbers) of one or more Elasticsearch servers. The format is *ip:port*. Use semicolons (;) to separate multiple IP addresses.              | 192.168.0.1:9200;192.168.0.2:9200 |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Security Mode Authentication | Whether to enable security mode.                                                                                                                                                            | Yes                               |
   |                              |                                                                                                                                                                                             |                                   |
   |                              | If **Security Mode** has been enabled for the CSS cluster to be connected, set this parameter to **Yes**. Otherwise, set this to **No**.                                                    |                                   |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Username                     | This parameter is displayed when **Security Mode Authentication** is set to **Yes**. It indicates the username used for connecting to CSS.                                                  | admin                             |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Password                     | This parameter is displayed when **Security Mode Authentication** is set to **Yes**. It indicates the password used for connecting to CSS.                                                  | ``-``                             |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | HTTPS Access                 | This parameter is displayed when **Security Mode Authentication** is set to **Yes**. This parameter specifies whether to enable HTTPS access. HTTPS access is more secure than HTTP access. | Yes                               |
   +------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
