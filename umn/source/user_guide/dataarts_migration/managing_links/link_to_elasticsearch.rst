:original_name: dataartsstudio_01_1380.html

.. _dataartsstudio_01_1380:

Link to Elasticsearch
=====================

Elasticsearch links can be used to connect to Elasticsearch services in third-party clouds and local data centers and on Elastic Cloud Servers (ECSs).

.. note::

   -  The Elasticsearch connector only supports Elasticsearch clusters in non-security mode.
   -  Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

:ref:`Table 1 <dataartsstudio_01_1380__en-us_topic_0000001768005284_table22075105144748>` lists the parameters for an Elasticsearch link.

.. _dataartsstudio_01_1380__en-us_topic_0000001768005284_table22075105144748:

.. table:: **Table 1** Elasticsearch link parameters

   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter                 | Description                                                                                                                                                                                    | Example Value                     |
   +===========================+================================================================================================================================================================================================+===================================+
   | Name                      | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                             | css_link                          |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Elasticsearch Server List | IP addresses or domain names (including the port numbers) of one or more Elasticsearch servers. The format is *ip:port*. Use semicolons (;) to separate multiple IP addresses or domain names. | 192.168.0.1:9200;192.168.0.2:9200 |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
