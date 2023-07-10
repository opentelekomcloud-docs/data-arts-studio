:original_name: dataartsstudio_01_0132.html

.. _dataartsstudio_01_0132:

Managing Drivers
================

The Java Database Connectivity (JDBC) provides programmatic access to relational databases. Applications can execute SQL statements and retrieve data using the JDBC API.

Before connecting CDM to a relational database, you need to upload the JDK 8 .jar driver of the relational database.

Prerequisites
-------------

-  A cluster has been created.
-  You have downloaded one of the drivers listed in :ref:`Table 1 <dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919>`.
-  (Optional) An SFTP link has been created by referring to :ref:`Link to an FTP or SFTP Server <dataartsstudio_01_0028>` and the corresponding driver has been uploaded to the offline file server.

.. _dataartsstudio_01_0132__en-us_topic_0286032703_section631855342818:

How Do I Obtain a Driver?
-------------------------

Different types of relational databases need to adapt to different drivers. You can obtain the JDK 8 .jar driver from the links provided in :ref:`Table 1 <dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919>`.

.. _dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919:

.. table:: **Table 1** Drivers

   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Relational Database Type | Driver Name     | How to Obtain                                                                                                               | Recommended Version                                                                                                                                            |
   +==========================+=================+=============================================================================================================================+================================================================================================================================================================+
   | -  RDS for MySQL         | MySQL           | https://downloads.mysql.com/archives/c-j/                                                                                   | mysql-connector-java-5.1.48.jar                                                                                                                                |
   | -  MySQL                 |                 |                                                                                                                             |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Oracle                   | ORACLE_6        | Driver packages: https://www.oracle.com/database/technologies/appdev/jdbc-downloads.html                                    | ojdbc8.jar for version 12.2.0.1                                                                                                                                |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          | ORACLE_7        | Driver packages of historical versions: https://repo1.maven.org/maven2/com/oracle/database/jdbc/ojdbc8/12.2.0.1/            | .. note::                                                                                                                                                      |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          | ORACLE_8        |                                                                                                                             |    New versions (for example, Oracle Database 21c (21.3) drivers) are not supported. If they are used, the schema name cannot be obtained during job creation. |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  RDS for PostgreSQL    | POSTGRESQL      | https://jdbc.postgresql.org/download                                                                                        | postgresql-42.1.4.jar for JDBC 4.2                                                                                                                             |
   | -  PostgreSQL            |                 |                                                                                                                             |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IBM Db2                  | DB2             | https://www.ibm.com/support/pages/db2-jdbc-driver-versions-and-downloads                                                    | 4.21.29                                                                                                                                                        |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  RDS for SQL Server    | SQLServer       | Driver packages:                                                                                                            | sqljdbc42.jar                                                                                                                                                  |
   | -  Microsoft SQL Server  |                 |                                                                                                                             |                                                                                                                                                                |
   |                          |                 | https://docs.microsoft.com/en-us/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15       |                                                                                                                                                                |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          |                 | Driver packages of historical versions:                                                                                     |                                                                                                                                                                |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          |                 | https://docs.microsoft.com/en-us/sql/connect/jdbc/release-notes-for-the-jdbc-driver?view=sql-server-ver15#previous-releases |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Access the CDM console, choose **Cluster Management** in the navigation pane, locate the target cluster, and choose **Job Management** > **Link Management** > **Driver Management**. The **Driver Management** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001321929292.jpg
      :alt: **Figure 1** Uploading a driver

      **Figure 1** Uploading a driver

#. Click **Upload** in the **Operation** column and select a local driver.

   Alternatively, click **Copy from SFTP** in the **Operation** column and configure the **SFTP Link** name and **Driver File Path**.

#. (Optional) If you have uploaded an updated version of a driver, you must restart the CDM cluster for the new driver to take effect.
