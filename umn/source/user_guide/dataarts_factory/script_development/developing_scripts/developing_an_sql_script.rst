:original_name: dataartsstudio_01_0424.html

.. _dataartsstudio_01_0424:

Developing an SQL Script
========================

DataArts Factory allows you to develop, debug, and run SQL scripts online. You can run developed scripts in jobs. For details, see :ref:`Developing a Pipeline Job <dataartsstudio_01_0435>`.

DataArts Factory supports the following types of SQL scripts. The SQL syntax varies depending on the data source. Before developing an SQL statement, learn about the syntax of the corresponding data source.

-  DLI SQL scripts: For details, see "Spark SQL Syntax" in *Spark SQL Syntax Reference* of the DLI service.
-  Hive SQL scripts: For details, see "Hive SQL" in *MapReduce Service (MRS) Usage Guide*.
-  DWS SQL scripts: For details, see the syntax descriptions in *Data Warehouse Service (DWS) Usage Guide*.
-  Spark SQL scripts: For details, see "Spark2x Basic Principles" in *MapReduce Service (MRS) Usage Guide*.
-  ClickHouse SQL scripts: For details, see "Common ClickHouse SQL Syntax" in *MapReduce Service (MRS) Usage Guide*.
-  Impala SQL scripts: For details, see "Impala" in *MapReduce Service (MRS) Usage Guide*.
-  Flink SQL scripts: For details, see "Stream SQL Join" in *MapReduce Service (MRS) Usage Guide*.
-  RDS SQL scripts: For details, see "Syntax" in *Relational Database Service User Guide*.
-  Presto SQL scripts: For details, see "Presto" in *MapReduce Service Overview*.
-  Spark Python scripts: For details, see "Configuring the Spark Python3 Sample Project" in *Developer Guide* in *MapReduce Service (MRS) Usage Guide*.
-  Doris SQL scripts: For details, see "Doris Basic Principles" in *MapReduce Service (MRS) Usage Guide*.

Prerequisites
-------------

-  A corresponding cloud service has been enabled and a database has been created in the cloud service.
-  A data connection that matches the data connection type of the created script. For details, see :ref:`Configuring DataArts Studio Data Connection Parameters <dataartsstudio_01_0009>`. The Flink SQL script does not involve this operation.
-  You have locked the script. Otherwise, you must click **Lock** so that you can develop the script. A script you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0912>`.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory, double-click a script to access the script development page.

#. In the upper part of the editor, select script properties. :ref:`Table 1 <dataartsstudio_01_0424__en-us_topic_0104967365_table18459183312499>` describes the script properties. Skip this step when creating a Flink SQL script.

   .. _dataartsstudio_01_0424__en-us_topic_0104967365_table18459183312499:

   .. table:: **Table 1** SQL script properties

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Property                          | Description                                                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================================================+
      | Data Connection                   | Select a data connection.                                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DLI Data Directory                | Select the DLI data directory.                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | -  Default DLI data directory **dli**                                                                                                                                                                                                                                                                                                                              |
      |                                   | -  Metadata catalog that has been created in LakeFormation associated with DLI.                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | Name of the database.                                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If you select the default DLI data directory **dli**, select a DLI database and tables.                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If you select a metadata catalog that has been created in LakeFormation associated with DLI, select a LakeFormation database and tables.                                                                                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Queue                    | Enter a resource queue for executing a job.                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | You can only enter rather than select a queue for Impala SQL and Hive SQL scripts.                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | Selects a resource queue for executing a DLI job. Set this parameter when a DLI or SQL script is created. After you select a queue, you can click |image1| to view the queue performance, including the number of running jobs and CU usage, in the last 24 hours.                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    -  If you select the default queue, a message is displayed, indicating that the performance of the default queue cannot be displayed.                                                                                                                                                                                                                           |
      |                                   |    -  If no queue is selected, is unavailable.                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | You can create a resource queue using either of the following methods:                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | -  Click |image2|. The **Queue Management** page of DLI is displayed.                                                                                                                                                                                                                                                                                              |
      |                                   | -  Go to the DLI console.                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    The default resource queue **default** provided by DLI is only used for trial. It may be occupied by multiple users at a time. Therefore, it is possible that you fail to obtain the resource for related operations. If the execution takes a long time or fails, you are advised to try again during off-peak hours or use a self-built queue to run the job. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    In addition, the **default** queue does not support the insert, load, or cat commands.                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | To set properties for submitting SQL jobs in the form of **key/value**, click |image3|. A maximum of 10 properties can be set. The properties are described as follows:                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    -  The environment variable must start with **hoodie.**, **dli.sql.**, **dli.ext.**, **dli.jobs.**, **spark.sql.**, or **spark.scheduler.pool**.                                                                                                                                                                                                                |
      |                                   |    -  If the environment variable is **dli.sql.autoBroadcastJoinThreshold**, the value must be an integer. If the environment variable is **dli.sql.shuffle.partitions**, the value must be a positive integer.                                                                                                                                                    |
      |                                   |    -  If the key of the environment variable is **dli.sql.shuffle.partitions** or **dli.sql.autoBroadcastJoinThreshold**, the environment variable cannot contain the greater than (>) or less than (<) sign.                                                                                                                                                      |
      |                                   |    -  If a parameter with the same name is configured in both a job and a script, the parameter value configured in the job will overwrite that configured in the script.                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | -  **dli.sql.autoBroadcastJoinThreshold**: specifies the data volume threshold to use BroadcastJoin. If the data volume exceeds the threshold, BroadcastJoin will be automatically enabled.                                                                                                                                                                        |
      |                                   | -  **dli.sql.shuffle.partitions**: specifies the number of partitions during shuffling.                                                                                                                                                                                                                                                                            |
      |                                   | -  **dli.sql.cbo.enabled**: specifies whether to enable the CBO optimization policy.                                                                                                                                                                                                                                                                               |
      |                                   | -  **dli.sql.cbo.joinReorder.enabled**: specifies whether join reordering is allowed when CBO optimization is enabled.                                                                                                                                                                                                                                             |
      |                                   | -  **dli.sql.multiLevelDir.enabled**: specifies whether to query the content in subdirectories if there are subdirectories in the specified directory of an OBS table or in the partition directory of an OBS partition table. By default, the content in subdirectories is not queried.                                                                           |
      |                                   | -  **dli.sql.dynamicPartitionOverwrite.enabled**: specifies that only partitions used during data query are overwritten and other partitions are not deleted.                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    When you run a DLI SQL script or test a DLI SQL single-task job in non-scheduling scenarios, the following parameters are enabled by default:                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    -  **spark.sql.adaptive.enabled**: Adaptive Query Execution (AQE) is enabled so that Spark can dynamically optimize the query execution plan based on the characteristics of the data being processed and improve the performance by reducing the amount of data to be processed.                                                                               |
      |                                   |    -  **spark.sql.adaptive.join.enabled**: AQE is enabled for join operations. The optimal join algorithm is selected based on the data being processed to improve performance.                                                                                                                                                                                    |
      |                                   |    -  **spark.sql.adaptive.skewedJoin.enabled**: AQE is enabled for skewed join operations. Skewed data can be automatically detected and the join algorithm is optimized accordingly to improve performance.                                                                                                                                                      |
      |                                   |    -  **spark.sql.mergeSmallFiles.enabled**: Merging of small files is enabled. Small files can be merged into large ones, improving performance and shortening the processing time. In addition, fewer files need to be read from remote storage, and more local files can be used.                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    If you do not want to use these functions, you can set the values of the preceding parameters to **false**.                                                                                                                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Enter an SQL statement in the editor. You can enter multiple SQL statements.

   The SQL syntax varies depending on the data source. Before developing an SQL statement, learn about the syntax of the corresponding data source.

   -  DLI SQL scripts: For details, see "Spark SQL Syntax" in *Spark SQL Syntax Reference* of the DLI service.
   -  Hive SQL scripts: For details, see "Hive SQL" in *MapReduce Service (MRS) Usage Guide*.
   -  DWS SQL scripts: For details, see the syntax descriptions in *Data Warehouse Service (DWS) Usage Guide*.
   -  Spark SQL scripts: For details, see "Spark2x Basic Principles" in *MapReduce Service (MRS) Usage Guide*.
   -  ClickHouse SQL scripts: For details, see "Common ClickHouse SQL Syntax" in *MapReduce Service (MRS) Usage Guide*.
   -  Impala SQL scripts: For details, see "Impala" in *MapReduce Service (MRS) Usage Guide*.
   -  Flink SQL scripts: For details, see "Stream SQL Join" in *MapReduce Service (MRS) Usage Guide*.
   -  RDS SQL scripts: For details, see "Syntax" in *Relational Database Service User Guide*.
   -  Presto SQL scripts: For details, see "Presto" in *MapReduce Service Overview*.
   -  Spark Python scripts: For details, see "Configuring the Spark Python3 Sample Project" in *Developer Guide* in *MapReduce Service (MRS) Usage Guide*.
   -  Doris SQL scripts: For details, see "Doris Basic Principles" in *MapReduce Service (MRS) Usage Guide*.

   .. note::

      -  SQL statements are separated by semicolons (**;**). If semicolons are used in other places but not used to separate SQL statements, escape them with backslashes (**\\**). For example:

         .. code-block::

            select 1;
            select * from a where b="dsfa\;";  --example 1\;example 2.

      -  RDS SQL does not support the begin ... commit transaction syntax. If necessary, use the start transaction ... commit transaction syntax.

      -  The script cannot be larger than 16 MB.

      -  The system date obtained by using an SQL statement is different from that obtained by using the database tool. The query result is stored in the database in the YYYY-MM-DD format, but the query result displayed on the page is in the converted format.

      -  When a user submits a Spark SQL script to MRS, the script is submitted to the tenant queue bound to the user by default. The bound queue is the queue corresponding to tenant role of the user. If there are multiple queues, the system preferentially selects a queue based on the queue priorities. To set a fixed queue for the user to submit scripts, log in to FusionInsight Manager, choose **Tenant Resources** > **Dynamic Resource Plan**, and click the **Global User Policy** tab. For details, see "Managing Global User Policies" in *MapReduce Service (MRS) Usage Guide*.

      -  Flink SQL, Hive SQL, and Spark SQL scripts support syntax check. After the check is complete, you can view the check result in the lower part of the page.

   To facilitate script development, DataArts Factory provides the following capabilities:

   -  The script editor supports the following shortcut keys, which improve the script development efficiency:

      -  **F8**: Run a script.
      -  **F9**: Stop running a script.
      -  **Ctrl** + **/**: Comment out or uncomment the line or code block where the cursor resides.
      -  **Ctrl** + **S**: Save a script.
      -  **Ctrl** + **Z**: Undo an action.
      -  **Ctrl** + **F**: Search for information.
      -  **Ctrl** + **Shift** + **R**: Replace
      -  **Ctrl** + **X**: Cut (Cut a line when the cursor selects nothing.)
      -  **Alt** + mouse dragging: Select columns to edit a block.
      -  **Ctrl** + mouse click: Select multiple lines to edit or indent them together.
      -  **Ctrl** + **→** (or **←**): Move the cursor rightwards (or leftwards) by word.
      -  **Ctrl** + **Home** or **Ctrl** + **End**: Navigate to the beginning or end of the current file.
      -  **Home** or **End**: Navigate to the beginning or end of the current line.
      -  **Ctrl** + **Shift** + **L**: Double-click all the same character strings and add cursors to them to implement batch modification.
      -  **Ctrl** + **D**: Delete a line.
      -  **Shift** + **Ctrl** + **U**: Unlock a script.
      -  **Ctrl** + **Alt** + **K**: Select the word where the cursor resides.
      -  **Ctrl** + **B**: Format
      -  **Ctrl** + **Shift** + **Z**: Redo
      -  **Ctrl** + **Enter**: Execute the selected line or content.
      -  **Ctrl** + **Alt** + **F**: Flag
      -  **Ctrl** + **Shift** + **K**: Search for the previous one.
      -  **Ctrl** + **K**: Search for the next one.
      -  **Ctrl** + **Backspace**: Delete the word to the left of the cursor.
      -  **Ctrl** + **Delete**: Delete the word to the right of the cursor.
      -  **Alt** + **Backspace**: Delete all content from the beginning of the line to the cursor.
      -  **Alt** + **Delete**: Delete all content from the cursor to the end of the line.
      -  **Alt** + **Shift**\ ``-``\ **Left**: Select all content from the beginning of the line to the cursor.
      -  **Alt** + **Shift**\ ``-``\ **Right**: Select all content from the cursor to the end of the line.

   -  System functions (Flink SQL, Spark SQL, ClickHouse SQL, and Presto SQL do not support system functions.)

      To view the functions supported by this type of data connection, click **System Functions** on the right of the editor. You can double-click a function to the editor to use it.

   -  Data tables can be read to generate SQL statements. This function is unavailable for Flink SQL, Spark Python, Presto SQL, and ClickHouse SQL.

      Click **Data Tables** on the right of the editor to display all the tables in the current database or schema. You can select tables and columns and click **Generate SQL Statement** in the lower right corner to generate an SQL statement, which you need to manually format.

   -  Script parameters (Currently, only Flink SQL does not support script parameters.)

      You can directly write script parameters in SQL statements. When debugging scripts, you can enter parameter values in the script editor. If the script is referenced by a job, you can set parameter values on the job development page. The parameter values can use EL expressions (see :ref:`Expression Overview <dataartsstudio_01_0494>`).

      .. note::

         If a parameter in an SQL script involves a variable, the format of the variable must be the same as that set in :ref:`Configuring Script Variables <dataartsstudio_01_04501__section310213518565>`. If they are different, the variable cannot be identified.

      In the following script example, *str1* indicates the parameter name. It can contain only letters, digits, hyphens (-), underscores (_), greater-than signs (>), and less-than signs (<), and can contain a maximum of 16 characters. The parameter name must be unique.

      .. code-block::

         select ${str1} from data;

      For MRS Spark SQL and MRS Hive SQL scripts, you set a program parameter by referring to **set hive.exec.parallel=true;** in the SQL statements or configure this parameter by setting **Program Parameter** on **Node Properties** of the job.


      .. figure:: /_static/images/en-us_image_0000002234238764.png
         :alt: **Figure 1** Program Parameter

         **Figure 1** Program Parameter

   -  Owner

      Click **Basic Info** to set the script owner and description.

   -  Allows you to go to the release page from the script development page in enterprise mode. Place the cursor over |image4| and click **Release**.

   -  For MRS API connections, parameters and values can be configured for Spark SQL and Hive SQL scripts. For proxy connections, this function is not supported.

      .. note::

         Click |image5| in the upper right corner to set environment variables for scripts. The following are some examples:

         Set environment variables for a Hive SQL script:

         --hiveconf hive.merge.mapfiles=true;

         --hiveconf mapred.job.queue.name=queue1

         Set environment variables for a Spark SQL script:

         --num-executors 1

         --executor-cores 4

         --queue queue2

         The former indicates the parameter name, and the latter indicates the parameter value.

         After the script is executed, view the execution details on the MRS management plane.

#. (Optional) In the upper part of the editor, click **Format** to format SQL statements. When developing a Flink SQL script, skip this step.

#. In the upper part of the editor, click **Execute**. If you need to execute some SQL statements separately, select the SQL statements first. After executing the SQL statements, view the execution history and result of the script in the lower part of the editor. When developing a Flink SQL script, skip this step.

   .. note::

      -  A maximum of 1,000 SQL statement execution results can be displayed. A maximum of 10,000 DLI SQL statement execution results can be displayed. To view more execution results, download or dump them by following the instructions in :ref:`Downloading or Dumping a Script Execution Result <dataartsstudio_01_0424__section2558253151213>`.
      -  You can perform the following operations on execution results:

         -  Double-click or right-click the name of an execution result tab to rename it. The name can contain a maximum of 16 characters.
         -  Right-click the name of an execution result tab to close the current tab, all the tabs to the left or right of the current tab, all the other tabs, or all the tabs.

      -  If the MRS cluster is a non-security cluster and the command whitelist is not restricted, you can easily find the corresponding task on the Yarn management page of MRS based on the script name and execution time after adding the application name information during Hive SQL execution. Note that if the default engine is **tez**, you need to set the engine to **mr** to disable the tez engine.
      -  When viewing the script execution result, you can double-click a field in any row to view the result details. You can copy the field name.
      -  You can control display of the script execution history by setting **Script Execution History** in **Default Configuration** to **Myself** or **All users**.

#. Above the editor, click **Save** to save the script.

   If the script is created but not saved, set the parameters listed in :ref:`Table 2 <dataartsstudio_01_0424__en-us_topic_0104967365_table35383235269>`.

   .. _dataartsstudio_01_0424__en-us_topic_0104967365_table35383235269:

   .. table:: **Table 2** Script parameters

      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Mandatory | Description                                                                                                                                        |
      +==================+===========+====================================================================================================================================================+
      | Script Name      | Yes       | Name of the script. The name contains a maximum of 128 characters, including only letters, numbers, hyphens (-), underscores (_), and periods (.). |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Owners           | No        | Owner of the script. By default, the creator of the script is the owner.                                                                           |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description      | No        | Descriptive information about the script.                                                                                                          |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Yes       | Directory to which the script belongs. The root directory is selected by default.                                                                  |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If you open an unsaved script, you can restore its content from the local cache.

      After the script is saved, a version is automatically generated and displayed in **Versions**. The version can be rolled back. If you save a script multiple times within a minute, only one version is recorded. If the intermediate data is important, you can click **Save new version** to save and add a version.

.. _dataartsstudio_01_0424__section2558253151213:

Downloading or Dumping a Script Execution Result
------------------------------------------------

After a script is executed successfully, you can download or dump the execution result. By default, all users can download and dump the execution results of SQL scripts. If you do not want all users to have this permission, configure the permission by referring to :ref:`Configuring a Data Export Policy <dataartsstudio_01_04501__section1970845152011>`.

-  After executing a script, you can click **Download** on the **Result** tab page to download a CSV result file to a local path. You can view the download record on the :ref:`Download Center <dataartsstudio_01_1821>` page.

-  After executing a script, you can click **Dump** on the **Result** tab page to dump a CSV and a JSON result file to OBS. For details, see :ref:`Table 3 <dataartsstudio_01_0424__table1192101552416>`.

   .. note::

      -  The dump function is supported only if the OBS service is available.
      -  Only the execution results of SQL script query statements can be dumped.
      -  If the execution result of a download or dump SQL statement contains commas (,), newline characters, or other special characters, data may be disordered, the number of rows may increase, or other issues may occur.

   .. _dataartsstudio_01_0424__table1192101552416:

   .. table:: **Table 3** Dump parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                |
      +=======================+=======================+============================================================================================================================================================================================================+
      | Data Format           | Yes                   | Format of the data to be exported. CSV and JSON formats are supported.                                                                                                                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Queue        | No                    | DLI queue where the export operation is to be performed. Set this parameter when a DLI or SQL script is created.                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compression Format    | No                    | Format of compression. Set this parameter when a DLI or SQL script is created.                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | -  none                                                                                                                                                                                                    |
      |                       |                       | -  bzip2                                                                                                                                                                                                   |
      |                       |                       | -  deflate                                                                                                                                                                                                 |
      |                       |                       | -  gzip                                                                                                                                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Path          | Yes                   | OBS path where the result file is stored. After selecting an OBS path, customize a folder. Then, the system will create it automatically for storing the result file.                                      |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | You can also go to the :ref:`Download Center <dataartsstudio_01_1821>` page to set the default OBS path, which will be automatically set for **Storage Path** in the **Dump Result** dialog box.           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cover Type            | No                    | If a folder that has the same name as your custom folder exists in the storage path, select a cover type. Set this parameter when a DLI or SQL script is created.                                          |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | -  **Overwrite**: The existing folder will be overwritten by the customized folder.                                                                                                                        |
      |                       |                       | -  **Report**: The system reports an error and suspends the export operation.                                                                                                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Export Column Name    | No                    | **Yes**: Column names will be exported.                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | **No**: Column names will not be exported.                                                                                                                                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Character Set         | No                    | -  **UTF-8**: default character set                                                                                                                                                                        |
      |                       |                       | -  **GB2312**: recommended when the data to be exported contains Chinese character sets                                                                                                                    |
      |                       |                       | -  **GBK**: expanded based on and compatible with GB2312                                                                                                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Quotation Character   | No                    | This parameter is available and can be set only when **Data Format** is **csv**.                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | Quotation characters are used to identify the beginning and end of text fields when exporting job results, and are used to separate fields.                                                                |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | Only one character can be set. The default value is double quotation marks (").                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | This is mainly used to handle data that contains spaces, special characters, or characters that are the same as the delimiter.                                                                             |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | For details about the examples of using quotation characters and escape characters, see :ref:`Example of Using Quotation Characters and Escape Characters <dataartsstudio_01_0424__section1729219531331>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Escape Character      | No                    | This parameter is available and can be set only when **Data Format** is **csv**.                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | If special characters, such as quotation marks, need to be included in the exported results, they can be represented using escape characters (backslash \\).                                               |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | Only one character can be set. The default value is a backslash (\\).                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | Common scenarios for using escape characters are:                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | -  If there is a third quotation mark between two quotation marks, add an escape character before the third quotation mark to prevent the field content from being split.                                  |
      |                       |                       | -  If there is already an escape character in the data content, add another escape character before the existing one to avoid the original character being used as an escape character.                    |
      |                       |                       |                                                                                                                                                                                                            |
      |                       |                       | For details about the examples of using quotation characters and escape characters, see :ref:`Example of Using Quotation Characters and Escape Characters <dataartsstudio_01_0424__section1729219531331>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Download or dump allows you to view more SQL script execution results. :ref:`Table 4 <dataartsstudio_01_0424__table19855813154916>` lists the maximum number of results that can be viewed, dumped, and downloaded for different types of SQL scripts.

.. _dataartsstudio_01_0424__table19855813154916:

.. table:: **Table 4** Maximum number of results that can be viewed, dumped, and downloaded

   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | SQL Type     | Maximum Number of Results That Can Be Viewed Online | Maximum Number/Size of Results That Can Be Downloaded                                  | Maximum Number/Size of Results That Can Be Dumped |
   +==============+=====================================================+========================================================================================+===================================================+
   | DLI          | 10,000                                              | 1,000 records, less than 3MB                                                           | Unlimited                                         |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | Hive         | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | GaussDB(DWS) | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | Spark        | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | RDS          | 1,000                                               | 1,000 records, less than 3MB                                                           | Not supported                                     |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | Presto       | 1,000                                               | The downloaded results are directly dumped to OBS. The number of results is unlimited. | Unlimited                                         |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | ClickHouse   | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | HetuEngine   | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | Impala       | 1,000                                               | 1,000 records, less than 3MB                                                           | 10,000 records or 3 MB                            |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+
   | Doris        | 1,000                                               | 1,000 records, less than 3MB                                                           | 1,000 records or 3 MB                             |
   +--------------+-----------------------------------------------------+----------------------------------------------------------------------------------------+---------------------------------------------------+

.. _dataartsstudio_01_0424__section1729219531331:

Example of Using Quotation Characters and Escape Characters
-----------------------------------------------------------

-  Usage of quotation characters and escape characters:

   -  Quotation character: used to identify and separate fields. The default value is double quotation marks (").
   -  Escape character: If special characters, such as quotation marks, need to be included in the exported results, they can be represented using escape characters (backslash \\). The default value is a backslash (\\).

      #. To prevent the content of a field from being split when there is a third quotation character between two quotation characters, add an escape character before the third quotation character.
      #. If there is already an escape character in the data content, add another escape character before the existing one to avoid the original character being used as an escape character.

-  Example:

   |image6|

   You can leave **Quotation Character** and **Escape Character** empty.

   |image7|

   If you leave them empty, the downloaded .csv file contains two rows in Excel.

   |image8|

   If you specify both of them, for example, enter double quotation marks ("), the downloaded file is as follows.

   |image9|

.. |image1| image:: /_static/images/en-us_image_0000002269118113.png
.. |image2| image:: /_static/images/en-us_image_0000002269198213.png
.. |image3| image:: /_static/images/en-us_image_0000002269118105.png
.. |image4| image:: /_static/images/en-us_image_0000002269116013.png
.. |image5| image:: /_static/images/en-us_image_0000002234238748.png
.. |image6| image:: /_static/images/en-us_image_0000002269198189.png
.. |image7| image:: /_static/images/en-us_image_0000002234078892.png
.. |image8| image:: /_static/images/en-us_image_0000002234078900.png
.. |image9| image:: /_static/images/en-us_image_0000002234238756.png
