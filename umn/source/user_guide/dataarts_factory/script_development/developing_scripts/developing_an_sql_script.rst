:original_name: dataartsstudio_01_0424.html

.. _dataartsstudio_01_0424:

Developing an SQL Script
========================

You can develop, debug, and run SQL scripts online. The developed scripts can be run in jobs. For details, see :ref:`Developing a Job <dataartsstudio_01_0435>`.

Prerequisites
-------------

-  A corresponding cloud service has been enabled and a database has been created in the cloud service. The Flink SQL script does not involve this operation.
-  A data connection that matches the data connection type of the created script. For details, see :ref:`Creating Data Connections <dataartsstudio_01_0009>`. The Flink SQL script does not involve this operation.
-  You have locked the script. Otherwise, you must click **Lock** so that you can develop the script. A script you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0901__li156131452182514>`.

Procedure
---------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory, double-click a script to access the script development page.

#. In the upper part of the editor, select script properties. :ref:`Table 1 <dataartsstudio_01_0424__en-us_topic_0104967365_table18459183312499>` describes the script properties. Skip this step when creating a Flink SQL script.

   .. _dataartsstudio_01_0424__en-us_topic_0104967365_table18459183312499:

   .. table:: **Table 1** SQL script properties

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Property                          | Description                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================+
      | Data Connection                   | Selects a data connection.                                                                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | Name of the database.                                                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Queue                    | Selects a resource queue for executing a DLI job. Set this parameter when a DLI or SQL script is created.                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   | You can create a resource queue using either of the following methods:                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   | -  Click |image1|. The **Queue Management** page of DLI is displayed.                                                                                                                                                                                                                    |
      |                                   | -  Go to the DLI console.                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   |    DLI provides the default resource queue **default**, which does not support insert, load, or cat commands.                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   | To set properties for submitting SQL jobs in the form of **key/value**, click |image2|. A maximum of 10 properties can be set. The properties are described as follows:                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                          |
      |                                   | -  **dli.sql.autoBroadcastJoinThreshold**: specifies the data volume threshold to use BroadcastJoin. If the data volume exceeds the threshold, BroadcastJoin will be automatically enabled.                                                                                              |
      |                                   | -  **dli.sql.shuffle.partitions**: specifies the number of partitions during shuffling.                                                                                                                                                                                                  |
      |                                   | -  **dli.sql.cbo.enabled**: specifies whether to enable the CBO optimization policy.                                                                                                                                                                                                     |
      |                                   | -  **dli.sql.cbo.joinReorder.enabled**: specifies whether join reordering is allowed when CBO optimization is enabled.                                                                                                                                                                   |
      |                                   | -  **dli.sql.multiLevelDir.enabled**: specifies whether to query the content in subdirectories if there are subdirectories in the specified directory of an OBS table or in the partition directory of an OBS partition table. By default, the content in subdirectories is not queried. |
      |                                   | -  **dli.sql.dynamicPartitionOverwrite.enabled**: specifies that only partitions used during data query are overwritten and other partitions are not deleted.                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Enter an SQL statement in the editor. You can enter multiple SQL statements.

   .. note::

      -  Note that the system date obtained by using an SQL statement is different from that obtained by using the database tool. The query result is stored in the database in the YYYY-MM-DD format, but the query result displayed on the page is in the converted format.

      -  SQL statements are separated by semicolons (**;**). If semicolons are used in other places but not used to separate SQL statements, escape them with backslashes (**\\**). For example:

         .. code-block::

            select 1;
            select * from a where b="dsfa\;";  --example 1\;example 2.

   To facilitate script development, DataArts Factory provides the following capabilities:

   -  The script editor supports the following shortcut keys, which improve the script development efficiency:

      -  **Ctrl** + **/**: Comment out or uncomment the line or code block at the cursor.
      -  **Ctrl** + **S**: Save
      -  **Ctrl** +\ **Z**: Cancel
      -  **Ctrl** + **Y**: Redo
      -  **Ctrl** + **F**: Search
      -  **Ctrl** + **Shift** + **R**: Replace
      -  **Ctrl** + **X**: Cut (cut a line when the cursor selects nothing).
      -  **Alt** + mouse dragging: Select columns to edit a block.
      -  **Ctrl** + mouse click: Select multiple lines to edit or indent them together.
      -  **Shift** + **Ctrl** + **K**: Delete the current line.
      -  **Ctrl** + **→** (or **←**): Move the cursor rightwards (or leftwards) by word.
      -  **Ctrl** + **Home** or **Ctrl** + **End**: Navigate to the beginning or end of the current file.
      -  **Home** or **End**: Navigate to the beginning or end of the current line.
      -  **Ctrl** + **Shift** + **L**: Double-click all the same character strings and add cursors to them to implement batch modification.

   -  System functions (Flink SQL, Spark SQL, ClickHouse SQL, and Presto SQL do not support system functions.)

      To view the functions supported by this type of data connection, click **System Function** on the right of the editor. You can double-click a function to the editor to use it.

   -  Data tables can be read to generate SQL statements. (Flink SQL, Spark SQL, ClickHouse SQL, and Presto SQL do not support this function.)

      Click **Data Tables** on the right of the editor to display all the tables in the current database or schema. You can select tables and columns and click **Generate SQL Statement** in the lower right corner to generate an SQL statement, which you need to manually format.

   -  Script parameters (Currently, only Flink SQL does not support script parameters.)

      You can directly write script parameters in SQL statements. When debugging scripts, you can enter parameter values in the script editor. If the script is referenced by a job, you can set parameter values on the job development page. The parameter values can use EL expressions (see :ref:`Expression Overview <dataartsstudio_01_0494>`).

      In the following script example, *str1* indicates the parameter name. It can contain only letters, numbers, hyphens (-), underscores (_), greater-than signs (>), and less-than signs (<), and can contain a maximum of 16 characters. The parameter name must be unique.

      .. code-block::

         select ${str1} from data;

      For MRS Spark SQL and MRS Hive SQL scripts, you set a program parameter by referring to **set hive.exec.parallel=true;** in the SQL statements or configure this parameter by setting **Program Parameter** on **Node Properties** of the job.


      .. figure:: /_static/images/en-us_image_0000001322408304.png
         :alt: **Figure 2** Program Parameter

         **Figure 2** Program Parameter

   -  Owner

      Click **Basic Info** to set the script owner and description.

#. (Optional) In the upper part of the editor, click **Format** to format the SQL statement. When developing a Flink SQL script, skip this step.

#. In the upper part of the editor, click **Execute**. If you need to execute some SQL statements separately, select the SQL statements first. After executing the SQL statement, view the execution history and result of the script in the lower part of the editor. When developing a Flink SQL script, skip this step.

   .. note::

      -  You can perform the following operations on execution results:

         -  Double-click or right-click the name of an execution result tab to rename it. The name can contain a maximum of 16 characters.
         -  Right-click the name of an execution result tab to close the current tab, all the tabs to the left or right of the current tab, all the other tabs, or all the tabs.

      -  If the MRS cluster is a non-security cluster and the command whitelist is not restricted, you can easily find the corresponding task on the Yarn management page of MRS based on the script name and execution time after adding the application name information during Hive SQL execution. Note that if the default engine is **tez**, you need to set the engine to **mr** to disable the tez engine.

#. Above the editor, click |image3| to save the script.

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

Downloading or Dumping a Script Execution Result
------------------------------------------------

**Constraints**: This function is available only when the OBS service is available.

After the script is executed successfully, you can download or dump the execution result. Only users with the **DAYU Administrator** or **Tenant Administrator** policy can download or dump execution results..

-  Download result: Download the CSV result files to the local host.

-  Dump result: Dump the CSV result files to OBS. For details, see :ref:`Table 3 <dataartsstudio_01_0424__table1192101552416>`.

   .. note::

      The execution results of Flink SQL scripts, RDS SQL scripts, and shell scripts cannot be dumped.

   .. _dataartsstudio_01_0424__table1192101552416:

   .. table:: **Table 3** Parameters for dumping results

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================================+
      | Data Format           | Yes                   | Format of the data to be exported. Only CSV result files can be exported.                                                                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Queue        | No                    | DLI queue where the export operation is to be performed. Set this parameter when a DLI or SQL script is created.                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compression Format    | No                    | Format of compression. Set this parameter when a DLI or SQL script is created.                                                                                        |
      |                       |                       |                                                                                                                                                                       |
      |                       |                       | -  none                                                                                                                                                               |
      |                       |                       | -  bzip2                                                                                                                                                              |
      |                       |                       | -  deflate                                                                                                                                                            |
      |                       |                       | -  gzip                                                                                                                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Path          | Yes                   | OBS path where the result file is stored. After selecting an OBS path, customize a folder. Then, the system will create it automatically for storing the result file. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cover Type            | No                    | If a folder that has the same name as your custom folder exists in the storage path, select a cover type. Set this parameter when a DLI or SQL script is created.     |
      |                       |                       |                                                                                                                                                                       |
      |                       |                       | -  **Overwrite**: The existing folder will be overwritten by the customized folder.                                                                                   |
      |                       |                       | -  **Report**: The system reports an error and suspends the export operation.                                                                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001322088404.png
.. |image2| image:: /_static/images/en-us_image_0000001373288761.png
.. |image3| image:: /_static/images/en-us_image_0000001373288605.png
