:original_name: dataartsstudio_01_0134.html

.. _dataartsstudio_01_0134:

Preparations Before Using DataArts Studio
=========================================

Before using DataArts Studio, you must conduct data and business surveys and select an appropriate data governance model.

Then, make the following preparations by referring to this topic:

-  :ref:`DataArts Studio Preparations <dataartsstudio_01_0134__section485519219101>`
-  :ref:`Preparing a Data Source <dataartsstudio_01_0134__section104811741192013>`
-  :ref:`Preparing a Data Lake <dataartsstudio_01_0134__section19482194142011>`

.. _dataartsstudio_01_0134__section485519219101:

DataArts Studio Preparations
----------------------------

If you use DataArts Studio for the first time, create a DataArts Studio instance and create a workspace by following the instructions provided in section "Preparations" in the *DataArts Studio User Guide*. Then you can develop and operate data in the workspace.

.. _dataartsstudio_01_0134__section104811741192013:

Preparing a Data Source
-----------------------

Many on-premises data sources are of MySQL, PostgreSQL, HBase, and Hive type. Therefore, you need to make the following preparations:

-  The host where the data source is located can access the public network.
-  Obtain the public network IP address, database port, and the administrator username and password for accessing the databases.
-  Ensure that the database port is enabled in the outbound direction of the firewall rule to allow data to be migrated to the cloud.

After the data source is prepared, you can migrate the data source to the data lake by using data integration, and then perform data development, governance, and operations using DataArts Studio.

.. _dataartsstudio_01_0134__section19482194142011:

Preparing a Data Lake
---------------------

Before using DataArts Studio, select a cloud service as the data lake. The data lake stores raw data and data generated during data development and is used for subsequent data development, services, and operations. For details on the data lake products supported by DataArts Studio, see :ref:`Data Sources <dataartsstudio_01_0005>`.

After the data lake is prepared, you can :ref:`create a data connection <dataartsstudio_01_0009>` to connect DataArts Studio to the data lake and then perform :ref:`1 <dataartsstudio_01_0134__li6595416104116>` and :ref:`2 <dataartsstudio_01_0134__li835274064119>`. For details about the operations in :ref:`1 <dataartsstudio_01_0134__li6595416104116>` and :ref:`2 <dataartsstudio_01_0134__li835274064119>`, see "Step 2: Preparations" in *Getting Started*.

#. .. _dataartsstudio_01_0134__li6595416104116:

   **Creating a Database**

   Before using DataArts Migration to migrate your data to the cloud, create a destination database in the data lake. According to the implementation process of data lake governance, you are advised to create a database for each of the SDI layer, DWI layer, DWR layer, and DM layer in the data lake to implement hierarchical sharding. Data sharding is a concept involved in DataArts Architecture. You will know more about it during architecture design.

   You can create a database in the data lake using either of the following methods:

   -  You can create a database on the DataArts Factory console of DataArts Studio. For details, see **DataArts Factory** > **Data Management** > **Creating a Database**.
   -  You can also develop and execute a SQL script for creating a database in the SQL editor of DataArts Studio's DataArts Factory module or a data lake product, and then use the script to create a database. For details about how to develop a script, see **DataArts Factory** > **Script Development** > **Developing Scripts** > **Developing an SQL Script**.

#. .. _dataartsstudio_01_0134__li835274064119:

   **Creating a Data Table**

   Before using DataArts Migration to migrate your data to the cloud, create a destination table in the SDI layer database of the destination data lake to store raw data. During batch data migration, a destination table can be automatically created for the migration between relational databases and from a relational database to Hive. In this case, you do not need to create the destination table in the destination database in advance.

   You can create a table in the data lake using either of the following methods: If a table contains a large number of fields, you are advised to create the table by compiling SQL scripts.

   -  You can create a table on the DataArts Factory console of DataArts Studio. For details, see **DataArts Factory** > **Data Management** > **Creating a Table**.
   -  You can also develop and execute a SQL script for creating a table in the SQL editor of DataArts Studio's DataArts Factory module or a data lake product, and then use the script to create a table. For details about how to develop a script, see **DataArts Factory** > **Script Development** > **Developing Scripts** > **Developing an SQL Script**.
