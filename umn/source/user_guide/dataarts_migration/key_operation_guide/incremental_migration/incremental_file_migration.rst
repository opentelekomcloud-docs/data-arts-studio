:original_name: dataartsstudio_01_0112.html

.. _dataartsstudio_01_0112:

Incremental File Migration
==========================

CDM supports incremental migration of file systems. After full migration is complete, all new files or only specified directories or files can be exported.

Currently, CDM supports the following incremental migration modes:

#. **Exporting the files in a specified directory**

   -  Application scenarios: The migration source is a file system (OBS/HDFS/FTP/SFTP). In incremental migration, only the specified files are written to the migration destination. The existing records are not updated or deleted.
   -  Key configurations: :ref:`File/Path Filter <dataartsstudio_01_0112__en-us_topic_0000001151619650_en-us_topic_0000001197578895_en-us_topic_0108275366_section1070082019442>` and Schedule Execution
   -  Prerequisites: The source directory or file name contains the time field.

#. **Exporting the files modified after the specified time point**

   -  Application scenarios: The migration source is a file system (OBS/HDFS/FTP/SFTP). The specified time point refers to the time when the file is modified. CDM migrates the files modified at or after the specified time point.
   -  Key configurations: :ref:`Time Filter <dataartsstudio_01_0112__en-us_topic_0000001151619650_en-us_topic_0000001197578895_en-us_topic_0108275366_section2012420511142>` and Schedule Execution
   -  Prerequisites: None

.. note::

   If you have configured a macro variable of date and time and schedule a CDM job through DataArts Studio DataArts Factory, the system replaces the macro variable of date and time with (*Planned start time of the data development job* - *Offset*) rather than (*Actual start time of the CDM job* - *Offset*).

.. _dataartsstudio_01_0112__en-us_topic_0000001151619650_en-us_topic_0000001197578895_en-us_topic_0108275366_section1070082019442:

File/Path Filter
----------------

-  Parameter position: When creating a table/file migration job, if the migration source is a file system, set **Filter Type** in advanced attributes of **Source Job Configuration** to **Wildcard** or **Regular expression**.

-  Parameter principle: If you select **Wildcard** for **Filter Type**, CDM filters files or paths based on the configured wildcard character and migrates only files or paths that meet the specified condition.

-  Example configurations:

   Suppose that the source file name contains the date and time field, such as **2017-10-15 20:25:26**, the **/opt/data/file_20171015202526.data** file is generated. Set the parameters as follows:

   #. **Filter Type**: Select **Wildcard**.
   #. **File Filter**: Enter **"*${dateformat(yyyyMMdd,-1,DAY)}*"**, which is the format of the macro variables of date and time supported by CDM. For details, see :ref:`Using Macro Variables of Date and Time <dataartsstudio_01_0114>`.
   #. Schedule Execution: Set **Cycle (days)** to **1**.

In this way, you can import the files generated in the previous day to the destination directory every day to implement incremental synchronization.

In incremental file migration, **Path Filter** is used in the same way as **File Filter**. The path name must contain the time field. In this case, all files in the specified path can be synchronized periodically.

.. _dataartsstudio_01_0112__en-us_topic_0000001151619650_en-us_topic_0000001197578895_en-us_topic_0108275366_section2012420511142:

Time Filter
-----------

-  Parameter position: When creating a table/file migration job, if the migration source is a file system, set select **Yes** for **Time Filter**.

-  Parameter principle: After you specify the start time and end time, only files that are modified between the start time (included) and end time (excluded) will be migrated.

-  Example configurations:

   For example, if you want CDM to synchronize only the files generated from January 1, 2021 to January 1, 2022 to the destination, configure the following parameters:

   #. **Time Filter**: select **Yes**.
   #. **Minimum Timestamp**: Enter a value in the format of *yyyy-MM-dd HH:mm:ss*, such as **2021-01-01 00:00:00**.
   #. **Maximum Timestamp**: Enter a value in the format of *yyyy-MM-dd HH:mm:ss*, such as **2022-01-01 00:00:00**.

In this way, the CDM job migrates only the files generated from January 1, 2021 to January 1, 2022, and performs incremental synchronization next time it is started.
