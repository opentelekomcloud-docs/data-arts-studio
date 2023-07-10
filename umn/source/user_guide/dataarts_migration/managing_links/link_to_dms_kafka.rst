:original_name: dataartsstudio_01_0038.html

.. _dataartsstudio_01_0038:

Link to DMS Kafka
=================

When connecting CDM to DMS Kafka, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0038__en-us_topic_0143085538_table22075105144748>`.

.. _dataartsstudio_01_0038__en-us_topic_0143085538_table22075105144748:

.. table:: **Table 1** Parameter description

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                | Example Value         |
   +=======================+============================================================================================================================+=======================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for         | dms_link              |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Service Type          | DMS Kafka edition. Currently, only the Platinum edition is available.                                                      | Platinum              |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Kafka Broker          | Address of a Kafka premium instance. The format is host:port.                                                              | ``-``                 |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Kafka SASL_SSL        | Whether to enable SSL authentication when a client connects to a Kafka premium instance.                                   | Yes                   |
   |                       |                                                                                                                            |                       |
   |                       | If Kafka SASL_SSL is enabled, data will be encrypted before transmission for higher security, but performance will suffer. |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Username              | Username for connecting to DMS Kafka. This parameter is displayed when **Kafka SASL_SSL** is enabled.                      | ``-``                 |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Password              | Password for connecting to DMS Kafka. This parameter is displayed when **Kafka SASL_SSL** is enabled.                      | ``-``                 |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
