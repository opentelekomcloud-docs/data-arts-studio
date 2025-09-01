:original_name: dataartsstudio_01_0114.html

.. _dataartsstudio_01_0114:

Using Macro Variables of Date and Time
======================================

During the creation of table/file migration jobs, CDM supports the macro variables of date and time in the following parameters of the source and destination links:

-  Source directory or file
-  Source table name
-  Directory filter and file filter of the **wildcard** type
-  Start time and end time of the **time filter** type
-  Partition filter criteria and where clause
-  Write directory
-  Destination table name

You can use the **${}** macro variable definition identifier to define the macros of the time type. currently, dateformat and timestamp are supported.

By using the macro variables of date and time and scheduled job, you can implement incremental synchronization of databases and files.

.. note::

   If you have configured a macro variable of date and time and schedule a CDM job through DataArts Studio DataArts Factory, the system replaces the macro variable of date and time with (*Planned start time of the data development job* - *Offset*) rather than (*Actual start time of the CDM job* - *Offset*).

dateformat
----------

**dateformat** supports two types of parameters:

-  **dateformat(format)**

   **format** indicates the date and time format. For details about the format definition, see the definition in **java.text.SimpleDateFormat.java**.

   For example, if the current date is **2017-10-16 09:00:00**, **yyyy-MM-dd HH:mm:ss** indicates **2017-10-16 09:00:00**.

-  dateformat(format, dateOffset, dateType)

   -  **format** indicates the format of the returned date.

   -  **dateOffset** indicates the date offset.

   -  **dateType** indicates the type of the date offset.

      Currently, **dateType** supports SECOND, MINUTE, HOUR, MONTH, YEAR, and DAY.

      .. note::

         Pay attention to the following special scenarios of **MONTH** and **YEAR**:

         -  If the date does not exist after the offset, the latest date of the month in the calendar is used.
         -  These two offset types cannot be used for the start time and end time in the **Time Filter** parameter of the source and destination jobs.

   For example, if the current date is **2023-03-01 09:00:00**, then:

   -  **dateformat(yyyy-MM-dd HH:mm:ss, -1, YEAR)** indicates the year before the current time, that is, **2022-03-01 09:00:00**.
   -  **dateformat(yyyy-MM-dd HH:mm:ss, -3, MONTH)** indicates three months before the current time, that is, **2022-12-01 09:00:00**.
   -  **dateformat(yyyy-MM-dd HH:mm:ss, -1, DAY)** indicates the day before the current time, that is, **2023-02-28 09:00:00**.
   -  **dateformat(yyyy-MM-dd HH:mm:ss, -1, HOUR)** indicates one hour before the current time, that is, **2023-03-01 08:00:00**.
   -  **dateformat(yyyy-MM-dd HH:mm:ss, -1, MINUTE)** indicates one minute before the current time, that is, **2023-03-01 08:59:00**.
   -  **dateformat(yyyy-MM-dd HH:mm:ss, -1, SECOND)** indicates one second before the current time, that is, **2023-03-01 08:59:59**.

timestamp
---------

**timestamp** supports two types of parameters:

-  **timestamp()**

   Indicates the returned timestamp of the current time, that is, the number of milliseconds that have elapsed since 00:00:00 on January 1, 1970 (1970-01-01 00:00:00 GMT). For example, 1508078516286.

-  **timestamp(dateOffset, dateType)**

   Indicates the timestamp returned after time offset. **dateOffset** and **dateType** indicate the date offset and the offset type, respectively.

   For example, if the current date is **2017-10-16 09:00:00**, **timestamp(-10, MINUTE)** indicates that the timestamp generated 10 minutes before the current time point is returned, that is, **1508115000000**.

Macro Variable Definition of Time and Date
------------------------------------------

Suppose that the current time is **2017-10-16 09:00:00**, then :ref:`Table 1 <dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_table45534079114353>` describes the macro variable definitions of time and date.

.. note::

   The examples in the table must be embedded in ''. For example, '${dateformat(yyyy-MM-dd)}' returns the current time in yyyy-MM-dd format.

.. _dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_table45534079114353:

.. table:: **Table 1** Macro variable definition of time and date

   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Macro Variable                              | Description                                                                                                                         | Display Effect        |
   +=============================================+=====================================================================================================================================+=======================+
   | ${dateformat(yyyy-MM-dd)}                   | Returns the current date in **yyyy-MM-dd** format.                                                                                  | 2017-10-16            |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy/MM/dd)}                   | Returns the current date in **yyyy/MM/dd** format.                                                                                  | 2017/10/16            |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy_MM_dd HH:mm:ss)}          | Returns the current time in **yyyy_MM_dd HH:mm:ss** format.                                                                         | 2017_10_16 09:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy-MM-dd HH:mm:ss, -1, DAY)} | Returns the current time in **yyyy-MM-dd HH:mm:ss** format. The date is one day before the current day.                             | 2017-10-15 09:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy-MM-dd, -1, DAY)} 00:00:00 | Returns 00:00:00 of the day before the current day in *yyyy-MM-dd HH:mm:ss* format.                                                 | 2017-10-15 00:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy-MM-dd, -1, DAY)} 12:00:00 | Returns 12:00:00 of the day before the current day in *yyyy-MM-dd HH:mm:ss* format.                                                 | 2017-10-15 12:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy-MM-dd, -N, DAY)} 00:00:00 | Returns 00:00:00 of the day N days before the current day in *yyyy-MM-dd HH:mm:ss* format.                                          | When N is 3:          |
   |                                             |                                                                                                                                     |                       |
   |                                             |                                                                                                                                     | 2017-10-13 00:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${dateformat(yyyy-MM-dd, -N, DAY)} 12:00:00 | Returns 12:00:00 of the day N days before the current day in *yyyy-MM-dd HH:mm:ss* format.                                          | When N is 3:          |
   |                                             |                                                                                                                                     |                       |
   |                                             |                                                                                                                                     | 2017-10-13 12:00:00   |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${timestamp()}                              | Returns the timestamp of the current time, that is, the number of milliseconds that have elapsed since 00:00:00 on January 1, 1970. | 1508115600000         |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${timestamp(-10, MINUTE)}                   | Returns the timestamp generated 10 minutes before the current time point.                                                           | 1508115000000         |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${timestamp(dateformat(yyyyMMdd))}          | Returns the timestamp of 00:00:00 of the current day.                                                                               | 1508083200000         |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${timestamp(dateformat(yyyyMMdd,-1,DAY))}   | Returns the timestamp of 00:00:00 of the previous day.                                                                              | 1507996800000         |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ${timestamp(dateformat(yyyyMMddHH))}        | Returns the timestamp of the current hour.                                                                                          | 1508115600000         |
   +---------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Time and Date Macro Variables of Paths and Table Names
------------------------------------------------------

:ref:`Figure 1 <dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_fig37004875105035>` shows an example. If:

-  **Table Name** under **Source Link Configuration** is set to **CDM_/${dateformat(yyyy-MM-dd)}**.
-  **Write Directory** under **Destination Link Configuration** is set to **/opt/ttxx/${timestamp()}**.

After the macro definition conversion, this job indicates that data in table **SQOOP.CDM_20171016** in the Oracle database is migrated to the **/opt/ttxx/1508115701746** directory of the HDFS server.

.. _dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_fig37004875105035:

.. figure:: /_static/images/en-us_image_0000002234238916.png
   :alt: **Figure 1** Setting **Table Name** and **Write Directory** to a time and date macro variable

   **Figure 1** Setting **Table Name** and **Write Directory** to a time and date macro variable

Currently, a table name or path name can contain multiple macro variables. For example, **/opt/ttxx/${dateformat(yyyy-MM-dd)}/${timestamp()}** is converted to **/opt/ttxx/2017-10-16/1508115701746**.

Time and Date Macro Variables in the Where Clause
-------------------------------------------------

:ref:`Figure 2 <dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_fig14550053112127>` uses table **SQOOP.CDM_20171016** as an example. The table contains column **DS**, which indicates the time.

.. _dataartsstudio_01_0114__en-us_topic_0000001197659211_en-us_topic_0000001197658799_en-us_topic_0108275294_fig14550053112127:

.. figure:: /_static/images/en-us_image_0000002269118281.png
   :alt: **Figure 2** Table data

   **Figure 2** Table data

Suppose that the current date is **2017-10-16** and you want to export data generated the day before the current day (DS = 2017-10-15), then you can set the value of **Where Clause** to **DS='${dateformat(yyyy-MM-dd,-1,DAY)}'** when creating a job. In this way, you can export all data that complies with the DS = 2017-10-15 condition.

Implementing Incremental Synchronization by Configuring the Macro Variables of Date and Time and Scheduled Jobs
---------------------------------------------------------------------------------------------------------------

Two simple application scenarios are as follows:

-  The database table contains column **DS** that indicates the time, the value type of the column is **varchar(30)**, and the inserted time format is similar to **2017-xx-xx**.

   In a scheduled job, the cycle is one day, and the scheduled job is executed at 00:00:00 every day. Set the value of **Where Clause** to **DS='${dateformat(yyyy-MM-dd,-1,DAY)}'**, and then data generated in the previous day will be exported at 00:00:00 every day.

-  The database table contains column **time** that indicates the time, the type is **Number**, and the inserted time format is timestamp.

   In a scheduled job, the cycle is one day, and the scheduled job is executed at 00:00:00 every day. Set the value of **Where Clause** to **time between ${timestamp(-1,DAY)} and ${timestamp()}**, and then data generated on the previous day will be exported at 00:00:00 every day.

Configuration principles of other application scenarios are the same.
