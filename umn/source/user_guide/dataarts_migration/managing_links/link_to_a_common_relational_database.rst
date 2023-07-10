:original_name: dataartsstudio_01_0044.html

.. _dataartsstudio_01_0044:

Link to a Common Relational Database
====================================

Common relational databases include: Data Warehouse Service (DWS), RDS for MySQL, RDS for PostgreSQL, RDS for SQL Server, PostgreSQL, Microsoft SQL Server, IBM Db2, and SAP HANA.

Prerequisites
-------------

You have uploaded required drivers by following the instructions in :ref:`Managing Drivers <dataartsstudio_01_0132>`.

Parameters for a link to a common relational database
-----------------------------------------------------

:ref:`Table 1 <dataartsstudio_01_0044__en-us_topic_0108275292_table5321744015490>` lists the link parameters.

.. _dataartsstudio_01_0044__en-us_topic_0108275292_table5321744015490:

.. table:: **Table 1** Parameters for a link to a common relational database

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter             | Description                                                                                                                                                                                   | Example Value                                               |
   +=======================+===============================================================================================================================================================================================+=============================================================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                            | mysql_link                                                  |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Database Server       | IP address or domain name of the database to connect                                                                                                                                          | 192.168.0.1                                                 |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       | Click **Select** next to the text box and select a DWS or RDS DB instance in the displayed dialog box.                                                                                        |                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Port                  | Port of the database to connect                                                                                                                                                               | The port number varies depending on the database. Examples: |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       |                                                                                                                                                                                               | Default port of SQL Server: **1433**                        |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       |                                                                                                                                                                                               | Default port of PostgreSQL: **5432**                        |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Database Name         | Name of the database to connect                                                                                                                                                               | dbname                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Username              | Username used for accessing the database This account must have the permissions required to read and write data tables and metadata.                                                          | cdm                                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Password              | Password of the user                                                                                                                                                                          | ``-``                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Use Agent             | Whether to extract data from the data source through an agent                                                                                                                                 | Yes                                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Agent                 | Click **Select** and select the agent created in :ref:`Managing Agents <dataartsstudio_01_0128>`.                                                                                             | ``-``                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Driver Version        | Select a driver version that adapts to the database type.                                                                                                                                     | ``-``                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Fetch Size            | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                                                             | 1000                                                        |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       | Number of rows obtained by each request. Set this parameter based on the data source and the job's data size. If the value is either too large or too small, the job may run for a long time. |                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | SSL Encryption        | (Optional) If you set this parameter to **Yes**, CDM can connect to the database (on-premises databases excluded) in SSL encryption mode.                                                     | Yes                                                         |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       | Security hardening has been performed on RDS for PostgreSQL. For this reason, when creating a link to RDS for PostgreSQL, set this parameter to **Yes**.                                      |                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Link Attributes       | (Optional) Click **Add** to add the JDBC connector attributes of multiple specified data sources. For details, see the JDBC connector document of the corresponding database.                 | sslmode=require                                             |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       | .. note::                                                                                                                                                                                     |                                                             |
   |                       |                                                                                                                                                                                               |                                                             |
   |                       |    By default, **useCursorFetch** is enabled, indicating that the JDBC connector communicates with relational databases using the binary protocol.                                            |                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Reference Sign        | (Optional) Delimiter between the names of the referenced tables or columns. For details, see the product documentation of the corresponding database.                                         | '                                                           |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
