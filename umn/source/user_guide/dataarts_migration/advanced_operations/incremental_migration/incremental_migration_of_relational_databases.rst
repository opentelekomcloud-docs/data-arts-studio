:original_name: dataartsstudio_01_0113.html

.. _dataartsstudio_01_0113:

Incremental Migration of Relational Databases
=============================================

CDM supports incremental migration of relational databases. After a full migration is complete, data in a specified period can be incrementally migrated. For example, data added on the previous day can be exported at 00:00:00 every day.

-  **Migrating incremental data within a specified period of time**

   -  Application scenarios: The source end is a relational database. The destination end can be of any type.
   -  Key configurations: :ref:`WHERE Clause <dataartsstudio_01_0113__en-us_topic_0000001151779454_en-us_topic_0000001151619238_en-us_topic_0108275332_section7506134317385>` and Schedule Execution
   -  Prerequisites: The data table contains a date and time field or timestamp field.

In incremental migration, only the specified data is written to the data table. The existing records are not updated or deleted.

.. _dataartsstudio_01_0113__en-us_topic_0000001151779454_en-us_topic_0000001151619238_en-us_topic_0108275332_section7506134317385:

WHERE Clause
------------

-  Parameter position: When creating a table/file migration job, if the source end is a relational database, the **Where Clause** parameter is available in the advanced attributes of **Source Job Configuration**.

-  Parameter principle: Set **WHERE Clause** to an SQL statement, for example, **age > 18 and age <= 60**, CDM exports only the data that meets the SQL statement requirement. If **WHERE Clause** is not specified, the entire table is exported.

   **Where Clause** can be set to :ref:`macro variables of date and time <dataartsstudio_01_0114>`. When the data table contains the **date** or **timestamp** field, **Where Clause** and Schedule Execution can be used together to extract data of a specified date.

-  Example configurations:

   Suppose that the database table contains column **DS** indicating the time, the value type of the column is **varchar(30)**, and the inserted time format is similar to *2017-xx-xx*. See :ref:`Figure 1 <dataartsstudio_01_0113__en-us_topic_0000001151779454_en-us_topic_0000001151619238_en-us_topic_0108275332_fig14550053112127>`. Set the parameters as follows:

   .. _dataartsstudio_01_0113__en-us_topic_0000001151779454_en-us_topic_0000001151619238_en-us_topic_0108275332_fig14550053112127:

   .. figure:: /_static/images/en-us_image_0000001373408037.png
      :alt: **Figure 1** Table data

      **Figure 1** Table data

   #. **WHERE Clause**: Set this parameter to **DS='${dateformat(yyyy-MM-dd,-1,DAY)}'**.
   #. Scheduling job execution: Set **Cycle (days)** to **1** and **Start Time** to **00:00:00**.

   In this way, all data generated on the previous day can be exported at 00:00:00 every day. **WHERE Clause** can be configured to various :ref:`macro variables of date and time <dataartsstudio_01_0114>`. You can use the macro variables of date and time and scheduled jobs with specified cycle of minutes, hours, days, weeks, or months together to automatically export data at a specific time.
