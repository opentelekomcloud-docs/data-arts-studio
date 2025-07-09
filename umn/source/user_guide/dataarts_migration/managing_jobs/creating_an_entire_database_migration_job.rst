:original_name: dataartsstudio_01_0075.html

.. _dataartsstudio_01_0075:

Creating an Entire Database Migration Job
=========================================

Scenario
--------

CDM supports entire DB migration between homogeneous and heterogeneous data sources. The migration principles are the same as those in :ref:`Table/File Migration Jobs <dataartsstudio_01_0046>`. Each type of Elasticsearch, each key prefix of Redis, or each collection of MongoDB can be executed concurrently as a subtask.

.. note::

   Each time an entire DB migration job is executed, its subtasks are recreated based on the configuration of the migration job. You cannot modify the subtasks and then run the migration job again.

:ref:`Supported Data Sources <dataartsstudio_01_0215>` lists the data sources supporting entire database migration.

Constraints
-----------

Field names of the source and destination parameters cannot contain ampersands (&) or number signs (%).

Prerequisites
-------------

-  A link has been created. For details, see :ref:`Creating Links <dataartsstudio_01_0024>`.

-  The CDM cluster can communicate with the data source.

Procedure
---------

#. Log in to the management console and choose **Service List** > **Cloud Data Migration**. In the left navigation pane, choose **Cluster Management**. Locate the target cluster and click **Job Management**.

#. Choose **Entire DB Migration** > **Create Job**. The page for configuring the job is displayed.

#. Configure the related parameters of the source database according to :ref:`Table 1 <dataartsstudio_01_0075__en-us_topic_0108275370_table14973632102118>`.

   .. _dataartsstudio_01_0075__en-us_topic_0108275370_table14973632102118:

   .. table:: **Table 1** Parameter description

      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Source Database | Parameter                | Description                                                                                                                                                                                                                                                                                               | Example Value          |
      +=================+==========================+===========================================================================================================================================================================================================================================================================================================+========================+
      | -  DWS          | Schema/Tablespace        | Name of the schema or tablespace from which data will be extracted. This parameter is displayed when **Use SQL Statement** is set to **No**. Click the icon next to the text box to go to the page for selecting a schema or directly enter a schema or tablespace.                                       | schema                 |
      | -  MySQL        |                          |                                                                                                                                                                                                                                                                                                           |                        |
      | -  PostgreSQL   |                          | If the desired schema or tablespace is not displayed, check whether the login account has the permissions required to query metadata.                                                                                                                                                                     |                        |
      | -  SQL Server   |                          |                                                                                                                                                                                                                                                                                                           |                        |
      | -  Oracle       |                          |                                                                                                                                                                                                                                                                                                           |                        |
      | -  SAP HANA     |                          |                                                                                                                                                                                                                                                                                                           |                        |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      |                 | WHERE Clause             | WHERE clause used to specify the tables to be extracted. This parameter applies to all subtables in the entire DB migration. If this parameter is not set, the entire table is extracted. If the table to be migrated does not contain the fields specified by the WHERE clause, the migration will fail. | age > 18 and age <= 60 |
      |                 |                          |                                                                                                                                                                                                                                                                                                           |                        |
      |                 |                          | You can set a date macro variable to extract data generated on a specific date.                                                                                                                                                                                                                           |                        |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      |                 | Null in Partition Column | Whether a partition field can be null                                                                                                                                                                                                                                                                     | Yes                    |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Hive            | Database Name            | Name of the database to be migrated. The user configured in the source link must have the permission to read the database.                                                                                                                                                                                | hivedb                 |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | HBase           | Start Time               | Start time (included). The format is *yyyy-MM-dd hh:mm:ss*. The dateformat time macro variable function is supported. Examples: **2017-12-31 20:00:00**, **${dateformat(yyyy-MM-dd, -1, DAY)} 02:00:00**, and **${dateformat(yyyy-MM-dd HH:mm:ss, -1, DAY)}**                                             | ``-``                  |
      |                 |                          |                                                                                                                                                                                                                                                                                                           |                        |
      | CloudTable      |                          |                                                                                                                                                                                                                                                                                                           |                        |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      |                 | End Time                 | End time (excluded) The format is *yyyy-MM-dd hh:mm:ss*. The dateformat time macro variable function is supported. Examples: **2018-01-01 20:00:00**, **${dateformat(yyyy-MM-dd, -1, DAY)} 02:00:00**, and **${dateformat(yyyy-MM-dd HH:mm:ss, -1, DAY)}**                                                | ``-``                  |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Redis           | Key Filter Character     | Filter character used to determine the keys to be migrated For example, if the value of this parameter is **a\***, all asterisks (``*``) will be migrated.                                                                                                                                                | ``-``                  |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | DDS             | Database Name            | Name of the database from which data is to be migrated. The user configured in the source link must have the permission to read the database.                                                                                                                                                             | ddsdb                  |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      |                 | Query Filter             | Filter used to match documents. Example: **{HTTPStatusCode:{$gt:"400",$lt:"500"},HTTPMethod:"GET"}**                                                                                                                                                                                                      | ``-``                  |
      +-----------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

#. Configure the related parameters, from :ref:`Table 2 <dataartsstudio_01_0075__en-us_topic_0108275370_table17764626124115>`, for the destination cloud service.

   .. _dataartsstudio_01_0075__en-us_topic_0108275370_table17764626124115:

   .. table:: **Table 2** Destination job parameters

      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | Destination Database  | Parameter          | Description                                                                                                                                                               | Example Value   |
      +=======================+====================+===========================================================================================================================================================================+=================+
      | -  RDS for MySQL      | ``-``              | For details about the destination job parameters required for entire DB migration to an RDS database, see :ref:`To MySQL/SQL Server/PostgreSQL <dataartsstudio_01_0068>`. | schema          |
      | -  RDS for PostgreSQL |                    |                                                                                                                                                                           |                 |
      | -  RDS for SQL Server |                    |                                                                                                                                                                           |                 |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | DWS                   | ``-``              | For details about the destination job parameters required for entire DB migration to DWS, see :ref:`To DWS <dataartsstudio_01_1251>`.                                     | ``-``           |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | MRS Hive              | ``-``              | For details about the destination job parameters required for entire DB migration to MRS HIVE, see :ref:`To Hive <dataartsstudio_01_0066>`.                               | hivedb          |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | MRS HBase             | ``-``              | For details about the destination job parameters required for entire DB migration to MRS HBase or CloudTable, see :ref:`To HBase/CloudTable <dataartsstudio_01_0064>`.    | Yes             |
      |                       |                    |                                                                                                                                                                           |                 |
      | CloudTable            |                    |                                                                                                                                                                           |                 |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | Redis                 | Clear Database     | Clears the database data before data import.                                                                                                                              | Yes             |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | DDS                   | Database Name      | Name of the database from which data is to be migrated. The user configured in the source link must have the permission to read the database.                             | mongodb         |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      |                       | Migration Behavior | Select **Add** or **Replace**.                                                                                                                                            | ``-``           |
      +-----------------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

#. If a relational database is migrated, after job parameters are configured, click **Next** to access the page for selecting tables. You can select the tables to be migrated to the migration destination based on your requirements.

#. Click **Next** and set job parameters.


   .. figure:: /_static/images/en-us_image_0000002270846978.png
      :alt: **Figure 1** Task parameters

      **Figure 1** Task parameters

   :ref:`Table 3 <dataartsstudio_01_0075__en-us_topic_0108275370_en-us_topic_0108275458_table62790900104257>` describes related parameters.

   .. _dataartsstudio_01_0075__en-us_topic_0108275370_en-us_topic_0108275458_table62790900104257:

   .. table:: **Table 3** Task configuration parameters

      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                            | Description                                                                                                                                                                                                                                                                                                          | Example Value         |
      +======================================+======================================================================================================================================================================================================================================================================================================================+=======================+
      | Concurrent Tables                    | Number of tables to be concurrently executed                                                                                                                                                                                                                                                                         | 3                     |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Concurrent Extractors                | Number of extractors to be concurrently executed. Generally, retain the default value.                                                                                                                                                                                                                               | 1                     |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Write Dirty Data                     | Whether to record dirty data. By default, this parameter is set to **No**.                                                                                                                                                                                                                                           | Yes                   |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Write Dirty Data Link                | This parameter is only displayed when **Write Dirty Data** is set to **Yes**.                                                                                                                                                                                                                                        | obs_link              |
      |                                      |                                                                                                                                                                                                                                                                                                                      |                       |
      |                                      | Only links to OBS support dirty data writes.                                                                                                                                                                                                                                                                         |                       |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS Bucket                           | This parameter is only displayed when **Write Dirty Data Link** is a link to OBS.                                                                                                                                                                                                                                    | dirtydata             |
      |                                      |                                                                                                                                                                                                                                                                                                                      |                       |
      |                                      | Name of the OBS bucket to which the dirty data will be written.                                                                                                                                                                                                                                                      |                       |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Dirty Data Directory                 | This parameter is only displayed when **Write Dirty Data** is set to **Yes**.                                                                                                                                                                                                                                        | /user/dirtydir        |
      |                                      |                                                                                                                                                                                                                                                                                                                      |                       |
      |                                      | Directory for storing dirty data on OBS. Dirty data is saved only when this parameter is configured.                                                                                                                                                                                                                 |                       |
      |                                      |                                                                                                                                                                                                                                                                                                                      |                       |
      |                                      | You can go to this directory to query data that fails to be processed or is filtered out during job execution, and check the source data that does not meet conversion or cleaning rules.                                                                                                                            |                       |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Max. Error Records in a Single Shard | This parameter is only displayed when **Write Dirty Data** is set to **Yes**.                                                                                                                                                                                                                                        | 0                     |
      |                                      |                                                                                                                                                                                                                                                                                                                      |                       |
      |                                      | When the number of error records of a single map exceeds the upper limit, the job will automatically terminate and the imported data cannot be rolled back. You are advised to use a temporary table as the destination table. After the data is imported, rename the table or combine it into the final data table. |                       |
      +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Save** or **Save and Run**.

   When the job starts running, a sub-job will be generated for each table. You can click the job name to view the sub-job list.

.. note::

   During the migration of an entire Oracle database to Hudi, if you select a view or a table that has no primary key at the source, automatic table creation is not supported.
