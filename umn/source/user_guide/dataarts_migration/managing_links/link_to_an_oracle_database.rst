:original_name: dataartsstudio_01_1212.html

.. _dataartsstudio_01_1212:

Link to an Oracle Database
==========================

:ref:`Table 1 <dataartsstudio_01_1212__en-us_topic_0000001265548638_table114522287389>` lists the parameters for a link to an Oracle database.

.. _dataartsstudio_01_1212__en-us_topic_0000001265548638_table114522287389:

.. table:: **Table 1** Parameters for a link to an Oracle database

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                   | Example Value         |
   +=======================+===============================================================================================================================================================================================+=======================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                            | oracle_link           |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Database Server       | IP address or domain name of the database to connect                                                                                                                                          | 192.168.0.1           |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Port                  | Port of the database to connect                                                                                                                                                               | Default port: 1521    |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Connection Type       | Oracle database connection type. The following options are available:                                                                                                                         | SID                   |
   |                       |                                                                                                                                                                                               |                       |
   |                       | -  **Service Name**: Use **SERVICE_NAME** to connect to the Oracle database.                                                                                                                  |                       |
   |                       | -  **SID**: Use **SID** to connect to the Oracle database.                                                                                                                                    |                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Instance Name         | Oracle instance ID, which is used to differentiate databases by instances. This parameter is available only when **Connection Type** is set to **SID**.                                       | dbname                |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Database Name         | Name of the database to connect This parameter is available only when **Connection Type** is set to **Service Name**.                                                                         | dbname                |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Username              | Username used for accessing the database This account must have the permissions required to read and write data tables and metadata.                                                          | cdm                   |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Password              | Password of the username                                                                                                                                                                      | ``-``                 |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Use Agent             | Whether to extract data from the data source through an agent                                                                                                                                 | Yes                   |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Agent                 | Click **Select** and select the agent created in :ref:`Managing Agents <dataartsstudio_01_0128>`.                                                                                             | ``-``                 |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Oracle Version        | Oracle database version. This parameter is available only for Oracle links. If **java.sql.SQLException: Protocol violation** is displayed, select another version.                            | Later than 12.1       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Fetch Size            | (Optional) Displayed when you click **Show Advanced Attributes**.                                                                                                                             | 1000                  |
   |                       |                                                                                                                                                                                               |                       |
   |                       | Number of rows obtained by each request. Set this parameter based on the data source and the job's data size. If the value is either too large or too small, the job may run for a long time. |                       |
   |                       |                                                                                                                                                                                               |                       |
   |                       | A migration from the Oracle to DWS database may time out due to a long data write duration in the DWS database. In this case, reduce the value of **Fetch Size** for the Oracle database.     |                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Link Attributes       | (Optional) Click **Add** to add the JDBC connector attributes of multiple specified data sources. For details, see the JDBC connector document of the corresponding database.                 | sslmode=require       |
   |                       |                                                                                                                                                                                               |                       |
   |                       | .. note::                                                                                                                                                                                     |                       |
   |                       |                                                                                                                                                                                               |                       |
   |                       |    By default, **useCursorFetch** is enabled, indicating that the JDBC connector communicates with relational databases using the binary protocol.                                            |                       |
   |                       |                                                                                                                                                                                               |                       |
   |                       |    -  The open-source MySQL database supports the **useCursorFetch** parameter. You do not need to set this parameter.                                                                        |                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Reference Sign        | (Optional) Delimiter between the names of the referenced tables or columns. For details, see the product documentation of the corresponding database.                                         | '                     |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
