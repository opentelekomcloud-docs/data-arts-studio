:original_name: dataartsstudio_01_0804.html

.. _dataartsstudio_01_0804:

Configuring a Metadata Collection Task
======================================

You can create collection tasks by configuring metadata collection policies. Different types of data sources require different collection policies. Metadata management allows you to collect technical metadata using the configured collection policies.

Constraints
-----------

-  If the collection scope is not specified for a metadata collection task, all data tables and files of a data connection are collected by default. After the collection task is complete, if data tables or files are added to the data connection, you must run the metadata collection task again to collect the new data tables or files.

-  Due to MRS cluster restrictions, metadata collection tasks cannot directly collect metadata of Hive partitioned tables by default.

   To collect metadata of Hive partitioned tables, add parameter **hive-ext.display.desc.statistic.stats** and value **true** to **hive.server.customized.configs** in **HiveServer(Role) > Customization** of the MRS cluster. For details, see :ref:`Enabling Metadata Collection from Hive Partitioned Tables of an MRS Cluster <dataartsstudio_01_0804__section1615142113579>`.

Prerequisites
-------------

-  Metadata of the following types of data sources can be collected: DWS, DLI, MRS HBase, MRS Hive, RDS, and Oracle. To obtain metadata, you must first create data connections in Management Center. To collect metadata from other data sources (such as OBS, CSS, and GES), you do not need to create data connections in Management Center.

-  Before you can collect the metadata of Hudi tables by collecting the MRS Hive metadata, you must enable synchronization of the Hive table configuration for Hudi tables.

-  To collect metadata of Hive partitioned tables, add parameter **hive-ext.display.desc.statistic.stats** and value **true** to **hive.server.customized.configs** in **HiveServer(Role) > Customization** of the MRS cluster. For details, see :ref:`Enabling Metadata Collection from Hive Partitioned Tables of an MRS Cluster <dataartsstudio_01_0804__section1615142113579>`.

Creating a Collection Task
--------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Metadata Collection** > **Task Management** from the left navigation bar.

3. Select the directory for the collection task. If no directory is available, create one as :ref:`Figure 1 <dataartsstudio_01_0804__fig28981041106>` shows.

   .. _dataartsstudio_01_0804__fig28981041106:

   .. figure:: /_static/images/en-us_image_0000002234239632.png
      :alt: **Figure 1** Directory that stores the collection task to create

      **Figure 1** Directory that stores the collection task to create

4. Click **Create** in the upper part of the displayed page or right-click **Task name** and choose **Add Task** from the shortcut menu. On the page displayed, set the parameters.

   :ref:`Figure 2 <dataartsstudio_01_0804__fig19474451115>` shows the entries for creating a task.

   .. _dataartsstudio_01_0804__fig19474451115:

   .. figure:: /_static/images/en-us_image_0000002234239644.png
      :alt: **Figure 2** Entries for creating a collection task

      **Figure 2** Entries for creating a collection task

   a. Set the basic configuration based on :ref:`Table 1 <dataartsstudio_01_0804__table994734213271>`.

      .. _dataartsstudio_01_0804__table994734213271:

      .. table:: **Table 1** Basic configuration parameters

         +------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter        | Description                                                                                                                                                  |
         +==================+==============================================================================================================================================================+
         | Task Name        | Name of a collection task. The value can contain only letters, numbers, and underscores (_), and cannot exceed 62 characters.                                |
         +------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description      | Information to better identify the collection task. Length of the description cannot exceed 255 characters.                                                  |
         +------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Select Directory | The directory that stores the collection task. You can select an existing one. :ref:`Figure 1 <dataartsstudio_01_0804__fig28981041106>` shows the directory. |
         +------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Configure data source information based on :ref:`Table 2 <dataartsstudio_01_0804__table673214448313>`.

      .. _dataartsstudio_01_0804__table673214448313:

      .. table:: **Table 2** Data source parameters

         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter             |                                                | Description                                                                                                                                                                                                                                                                                                                                     |
         +=======================+================================================+=================================================================================================================================================================================================================================================================================================================================================+
         | Data Connection Type  |                                                | Select a data connection type from the drop-down list box.                                                                                                                                                                                                                                                                                      |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | .. note::                                                                                                                                                                                                                                                                                                                                       |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                |    Metadata of the following types of data sources can be collected: DWS, DLI, MRS HBase, MRS Hive, RDS, and Oracle. To obtain metadata, you must first create data connections in Management Center. To collect metadata from other data sources (such as OBS, CSS, and GES), you do not need to create data connections in Management Center. |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | -  **DWS**            | Data Connection Name                           | -  To use an existing data connection, select a value from the drop-down list.                                                                                                                                                                                                                                                                  |
         | -  **DLI**            |                                                | -  To use a data connection that does not exist, click **Create** to add one.                                                                                                                                                                                                                                                                   |
         | -  **MRS HBase**      |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         | -  **MRS Hive**       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         | -  **ORACLE**         |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         | -  **RDS**            |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | Database                                       | Database, schema, or namespace and data table from which data will be collected                                                                                                                                                                                                                                                                 |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       | (or **Database and Schema** and **Namespace**) | -  Click **Set** next to **Database** (or **Database and Schema** or **Namespace**) to set the range of databases (or databases and schemas or namespaces) to be scanned by the collection task. If this parameter is not set, all databases (or databases and schemas or namespaces) under the data connection are scanned by default.         |
         |                       |                                                | -  Click **Set** next to **Table** to set the range of tables to be scanned by the collection task. If this parameter is not set, all tables in the database (or database and schema or namespace) are scanned by default.                                                                                                                      |
         |                       |                                                | -  If neither the database (or database and schema or namespace) nor the data table is set, the task scans all data tables of the selected data connection.                                                                                                                                                                                     |
         |                       |                                                | -  Click **Clear** to delete the selected database (or database and schema or namespace) and data table.                                                                                                                                                                                                                                        |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | Table                                          |                                                                                                                                                                                                                                                                                                                                                 |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | **CSS**               | Cluster                                        | Select the CSS cluster for storing the data to be collected.                                                                                                                                                                                                                                                                                    |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | You can also click **Create** to create a CSS cluster. After the CSS cluster is created, click **Refresh** and select the new CSS cluster.                                                                                                                                                                                                      |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | CDM Cluster                                    | Select the agent provided by the CDM cluster.                                                                                                                                                                                                                                                                                                   |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | You can also click **Create** to create an agent. After the agent is created, click **Refresh** and select the new agent.                                                                                                                                                                                                                       |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | Index                                          | Index, similar to "database" in the relational database (RDB), stores Elasticsearch data. It is a logical space that consists of one or more shards.                                                                                                                                                                                            |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | **GES**               | Graph                                          | Select graphs that store structured data based on "relationships".                                                                                                                                                                                                                                                                              |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | CDM Cluster                                    | Select the agent provided by the CDM cluster.                                                                                                                                                                                                                                                                                                   |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | You can also click **Create** to create an agent. After the agent is created, click **Refresh** and select the new agent.                                                                                                                                                                                                                       |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | **OBS**               | OBS Bucket                                     | Select the OBS bucket from which data will be collected.                                                                                                                                                                                                                                                                                        |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | OBS Path                                       | Select the path of the OBS bucket from which data will be collected.                                                                                                                                                                                                                                                                            |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | Collection Scope                               | Select the range of data to be collected.                                                                                                                                                                                                                                                                                                       |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | -  If you select **This folder**, the collection task collects only the objects in the folder set in the OBS path.                                                                                                                                                                                                                              |
         |                       |                                                | -  If you select **This folder and subfolders**, the collection task collects all objects in the folder set in the OBS path, including the objects in the sub-folders.                                                                                                                                                                          |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                       | Collected Content                              | Select the content of data to be collected.                                                                                                                                                                                                                                                                                                     |
         |                       |                                                |                                                                                                                                                                                                                                                                                                                                                 |
         |                       |                                                | -  If you select **Folders and objects**, the collection task collects folders and objects.                                                                                                                                                                                                                                                     |
         |                       |                                                | -  If you select **Folders**, the collection task collects only folders.                                                                                                                                                                                                                                                                        |
         +-----------------------+------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Set parameters under **Metadata Collection**. See :ref:`Table 3 <dataartsstudio_01_0804__table199065010379>`.

      .. note::

         Metadata collection parameters are available only for DWS, DLI, MRS HBase, MRS Hive, RDS, or Oracle connections.

      .. _dataartsstudio_01_0804__table199065010379:

      .. table:: **Table 3** Parameters for metadata collection

         +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                                  | Description                                                                                                                                                                         |
         +============================================+=====================================================================================================================================================================================+
         | The data source metadata has been updated. | When metadata in a data connection changes, you can configure an update policy to set the metadata update mode in the data catalog.                                                 |
         |                                            |                                                                                                                                                                                     |
         |                                            | Note that the configured update and deletion policies apply only to the databases and data tables configured by yourself.                                                           |
         |                                            |                                                                                                                                                                                     |
         |                                            | -  If you select **Update metadata in the data directory only**, the collection task updates only the metadata that has been collected in the data catalog.                         |
         |                                            | -  If you select **Add new metadata to the data directory only**, the collection task collects only metadata that exists in the data source but does not exist in the data catalog. |
         |                                            | -  If you select **Update metadata in the data directory and add metadata**, the collection task fully synchronizes metadata from the data source.                                  |
         |                                            | -  If you select **Ignore the update and addition operations**, the metadata in the data source is not collected.                                                                   |
         +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | The data source metadata has been deleted. | When metadata in a data connection changes, you can configure a deletion policy to set the metadata update mode in the data catalog.                                                |
         |                                            |                                                                                                                                                                                     |
         |                                            | -  If you select **Delete metadata from data directory**, when some metadata in the data source is deleted, the corresponding metadata is also deleted from the data catalog.       |
         |                                            | -  If you select **Ignore the deletion**, when some metadata in the data source is deleted, the corresponding metadata is not deleted from the data catalog.                        |
         +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Set parameters when **Data Summary** is selected. See :ref:`Table 4 <dataartsstudio_01_0804__table373593012409>` for details.

      .. note::

         -  **Data Summary** parameters are available only for DWS, DLI connections.
         -  You are advised not to select **Data Summary** unless necessary. Selecting this option will increase the SQL execution workload. As a result, the metadata collection task may take a longer time than expected.

      .. _dataartsstudio_01_0804__table373593012409:

      .. table:: **Table 4** Parameters

         +-------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                                             | Description                                                                                                                                                             |
         +=======================================================+=========================================================================================================================================================================+
         | Full data                                             | If this option is selected, a data profile is generated in the data catalog based on all data collected.                                                                |
         |                                                       |                                                                                                                                                                         |
         |                                                       | This mode applies to scenarios where the data volume is less than 1 million.                                                                                            |
         +-------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Sampled data, first *x* rows                          | If this option is selected, a data profile is generated in the data catalog based on all data collected.                                                                |
         |                                                       |                                                                                                                                                                         |
         |                                                       | This mode is applicable to scenarios with a large amount of data.                                                                                                       |
         +-------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Randomly collect *x*\ % records of data from all data | If this option is selected, a data profile is generated in the data catalog based on all data collected.                                                                |
         |                                                       |                                                                                                                                                                         |
         |                                                       | This mode is applicable to scenarios with a large amount of data.                                                                                                       |
         +-------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Data Lake Insight Queue                               | The queue used to obtain profile data and execute DLI SQL statements.                                                                                                   |
         |                                                       |                                                                                                                                                                         |
         |                                                       | If you select **Collect unique value**, the number of unique values in the collected table is calculated and displayed on the **Profile** tab page in the data catalog. |
         +-------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   e. Set parameters when **Data Classification** is selected. (This option is available only when DataArts Catalog provides data security functions. The data classification cannot be associated with a sensitive data identification rule created in the independent DataArts Security module.)

      -  If you select **Data Classification** and create a classification rule group or select an existing classification rule group by referring to :ref:`Creating a Data Classification (To Be Removed) <dataartsstudio_01_0822>`, data will be automatically identified and a classification will be added.
      -  If you select **Update the data table security level based on the data classification result**, the table security level must be the same as the highest security level of the matched classification rules.

      -  If you select **Manually** for **Synchronize Data**, classification rules and security levels are not automatically added to **Column Attributes** of **Data Catalog** under **Data Map**. Go to the **Task Monitoring** page. Locate the target instance and choose **More** > **View Scanning Result** to view the execution result of the collection task and check whether the classification result matches. Select the check box of the classification matching field and click **Synchronize** to manually synchronize the classification rule and security level.

      .. note::

         Only when you choose the DWS or DLI data source, you can add data classifications for automatic data identification. In addition, you can add classification rules only for columns in the data tables and OBS objects.

5. Click **Next** and select a scheduling mode.

   **Once**: If the execution duration of a task exceeds the configured timeout duration, the task is considered failed.

   **Repeating**: See :ref:`Table 5 <dataartsstudio_01_0804__table7217145245713>` for details.

   .. note::

      a. If **Once** is selected, a manual task instance is generated. A manual task has no dependency on scheduling and must be manually triggered.
      b. If **Repeating** is selected, a periodic instance is generated. A periodic instance is an instance snapshot that is automatically scheduled when the scheduled execution time is arrived.
      c. When a periodic task is scheduled once, an instance workflow is generated. You can perform routine O&M on scheduled instance tasks, such as viewing the running status, stopping and rerunning the scheduled tasks.

   .. _dataartsstudio_01_0804__table7217145245713:

   .. table:: **Table 5** Parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================+
      | Scheduling Date                   | The period during which a scheduling task takes effect.                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scheduling Cycle                  | The frequency at which the scheduling task is executed, which can be:                                                                                               |
      |                                   |                                                                                                                                                                     |
      |                                   | -  Minutes                                                                                                                                                          |
      |                                   | -  Hours                                                                                                                                                            |
      |                                   | -  Days                                                                                                                                                             |
      |                                   | -  Weeks                                                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start Time                        | Start time of periodic scheduling, which is used together with the start time in **Scheduling Date**.                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Time Interval                     | Interval between two periodic scheduling operations                                                                                                                 |
      |                                   |                                                                                                                                                                     |
      |                                   | A scheduling task instance starts even if the previous scheduling task instance has not ended. A collection task supports concurrent running of multiple instances. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | End Time                          | End time of periodic scheduling, which is used together with the end time in **Scheduling Date**.                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Timeout                           | Timeout duration for a task instance. If a task runs longer than the value of this parameter, the task fails to be executed.                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start                             | If this check box is selected, the task is scheduled immediately.                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. Click **Submit**. The collection task is created.

Managing a Collection Task
--------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Metadata Collection** > **Task Management** from the left navigation bar.

Then, you can view all created collection tasks.

.. table:: **Table 6** Parameters for managing collection tasks

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                           |
   +===================================+=======================================================================================================================================================================================================+
   | Task Name                         | The name of a collection task.                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                       |
   |                                   | Click a collection task name to view the collection policies and scheduling properties.                                                                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                              | The name of a data connection.                                                                                                                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduling Status                 | The scheduling status of a collection task. You can click |image1| to view only tasks of the specified statuses.                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduling Cycle                  | The scheduling frequency of a collection task. You can click |image2| to view only tasks of the specified frequencies.                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description                       | The description of a collection task.                                                                                                                                                                 |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creator                           | The creator of a collection task.                                                                                                                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Last Executed On                  | The last time when the collection task ran.                                                                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | You can perform the following operations on a created collection task:                                                                                                                                |
   |                                   |                                                                                                                                                                                                       |
   |                                   | -  **Edit**: Modify the parameters that are closely related to the policies of collection tasks whose status is **Started**, **Not started**, or **Failed**. The data source type cannot be modified. |
   |                                   | -  **Run**: Click **Run** to run a collection task once and view its status and related logs on the **Task Monitoring** page.                                                                         |
   |                                   | -  **Start Scheduling**: If the status of a task is **Stopped**, you can start scheduling the task based on the configured scheduling mode.                                                           |
   |                                   | -  **Stop Scheduling**: When the scheduling status is **Scheduling**, you can stop the scheduling.                                                                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0804__section1615142113579:

Enabling Metadata Collection from Hive Partitioned Tables of an MRS Cluster
---------------------------------------------------------------------------

#. Log in to MRS Manager as user **admin**.

#. On FusionInsight Manager, choose **Cluster** > **Services** > **Hive** and click the **Configurations** tab and then **All Configurations**. Choose **HiveServer(Role)** > **Customization**. Add **hive-ext.display.desc.statistic.stats** to the value of **hive.server.customized.configs** and set the value of **hive-ext.display.desc.statistic.stats** to **true**.


   .. figure:: /_static/images/en-us_image_0000002269119017.png
      :alt: **Figure 3** Adding a custom parameter

      **Figure 3** Adding a custom parameter

#. After setting the parameter, click **Save** in the upper left corner and then **OK** in the dialog box to save the configuration.


   .. figure:: /_static/images/en-us_image_0000002234079840.png
      :alt: **Figure 4** Saving the configuration

      **Figure 4** Saving the configuration

#. After saving the configuration, switch to the **Instances** tab page, select the instance that has expired, click **More**, and select **Instance Rolling Restart** to make the configuration take effect.


   .. figure:: /_static/images/en-us_image_0000002269199113.png
      :alt: **Figure 5** Performing a rolling instance restart

      **Figure 5** Performing a rolling instance restart

.. |image1| image:: /_static/images/en-us_image_0000002269199097.jpg
.. |image2| image:: /_static/images/en-us_image_0000002234254362.jpg
