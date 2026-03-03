:original_name: dataartsstudio_01_1021.html

.. _dataartsstudio_01_1021:

Embedding Data Watermarks
=========================

This section describes how to embed data watermarks. Data watermarking applies to the following scenarios:

-  Data forwarding process standardization

   Unauthorized users need to be approved when they forward data from enterprises for external usage. After the approval, the watermark technology is used to generate files that can be used outside enterprises.

-  Digital right protection

   To associate databases with their owners, embed watermarks representing ownerships in relational databases. In this way, enterprises' digital rights can be protected.

-  Quick source tracing of leaked data

   To locate security vulnerabilities, unseal the leaked data files, check whether watermarks exist based on the file integrity and watermark traces, and identify watermark information such as data source addresses, distribution units, owners, and distribution time.

Watermark Use Process
---------------------

:ref:`Figure 1 <dataartsstudio_01_1021__en-us_topic_0000001676159785_fig468313575540>` shows the process of using watermarks.

.. _dataartsstudio_01_1021__en-us_topic_0000001676159785_fig468313575540:

.. figure:: /_static/images/en-us_image_0000002269123189.png
   :alt: **Figure 1** Watermark use process

   **Figure 1** Watermark use process

Constraints
-----------

-  Only the MRS Doris and MRS Hive data sources support data watermark tasks.
-  Watermarks cannot be embedded into a primary key.
-  If a watermark is embedded in a numeric integer field, the data may be modified. Embed watermarks into a field whose value can be changed.
-  If **Dataset Scope** is set to **Incremental** for a data watermark embedding task, **Timestamp** or **Date** needs to be selected for **Time Field**.
-  For the MRS Doris data source, watermarks can be embedded only into fields of the string type, including Varchar, Text, and String. Ensure that the table into which watermarks are to be embedded contains fields of the string type.
-  To embed watermarks into the MRS Doris data source, you need to prepare an MRS cluster that contains the Hadoop, Spark, and Yarn components. The MRS cluster is used to run the watermark embedding task.

Prerequisites
-------------

An MRS Hive or MRS Doris connection has been created. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.

.. _dataartsstudio_01_1021__en-us_topic_0000001676159785_section191138181:

Creating a Data Watermark Embedding Task
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Data Watermark Embedding** from the left navigation bar, and click **Create** in the upper part of the displayed page.


   .. figure:: /_static/images/en-us_image_0000002234243736.png
      :alt: **Figure 2** Creating a data watermark embedding task

      **Figure 2** Creating a data watermark embedding task

#. In the displayed dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1021__en-us_topic_0000001676159785_table179731221105915>`.

   .. _dataartsstudio_01_1021__en-us_topic_0000001676159785_table179731221105915:

   .. table:: **Table 1** Basic settings

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================+
      | \*Task                            | Name of the watermark embedding task. The name can only contain letters, digits, underscores (_), and hyphens (-), and can contain a maximum of 64 characters.                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                           |
      |                                   | To facilitate the management of the watermark embedding task, you are advised to include the object into which you want to embed the watermark and the watermark ID in the name.                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the task                                                                                                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark ID                    | Watermark ID that will be embedded by the system into data tables. The watermark ID can contain a maximum of 16 characters.                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Error Correction Level          | The higher the level, the more bits of watermark information, and the lower bit error rate during source tracing. Note that a higher error correction level requires a larger amount of data to ensure the integrity of embedded information. The default value is **1**. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark Version               | **V1**: Watermarks depend on primary keys, and the embedding speed is fast. If primary keys are attacked, source tracing may fail.                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                           |
      |                                   | **V2**: Watermarks do not depend on primary keys. They are related only to embed columns. The embedding speed is slow and the robustness is enhanced.                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002234083872.png
      :alt: **Figure 3** Configuring basic information

      **Figure 3** Configuring basic information

#. Click **Next** to configure the source and target end parameters listed in :ref:`Table 2 <dataartsstudio_01_1021__en-us_topic_0000001676159785_table1093620161417>`.

   .. _dataartsstudio_01_1021__en-us_topic_0000001676159785_table1093620161417:

   .. table:: **Table 2** Source and target end parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | **Source Settings**               |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source Type                | Currently, the value can only be **MRS Hive**.                                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | Select a data connection. If no data connection is available, create one by referring to :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                                                                                                                                                                                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*HTTP/HTTPS Port                 | This parameter is required for the MRS Doris data source. To obtain the port, perform the following operations: Log in to MRS FusionInsight Manager of the Doris cluster, choose **Cluster** > **Services** > **Doris**, and click **Configurations**. If Kerberos authentication is enabled for the cluster, enter the value of **https_port** for this parameter. Otherwise, enter the value of **http_port** for this parameter. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Database                        | Select the databases and tables into which you want to embed the watermark.                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  Click **Configure** to select databases and tables.                                                                                                                                                                                                                                                                                                                                                                              |
      |                                   | -  Click **Clear** to delete the selected databases and data tables.                                                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Source Table                    |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark Embedding Bar         | Select a field type from the drop-down list as the embedding bar. For example, the value can be a number or a character.                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | Note that when **Watermark Version** is set to **V1**, the primary key column cannot be selected.                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Dataset Scope                   | If **Dataset Scope** is set to **Incremental**, you can set **Time Field** to **Timestamp** or **Date**.                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | Generally, the watermark embedding task is scheduled once if this parameter is set to **All** and is scheduled periodically if this parameter is set to **Incremental**.                                                                                                                                                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Time Field                      | If **Dataset Scope** is set to **Incremental**, you can set this parameter to **Timestamp** or **Date**.                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Target End Settings**           |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source Type                | Currently, the value can only be **MRS Hive**.                                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | Select a data connection. If no data connection is available, create one by referring to :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                                                                                                                                                                                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*HTTP/HTTPS Port                 | This parameter is required for the MRS Doris data source. To obtain the port, perform the following operations: Log in to MRS FusionInsight Manager of the Doris cluster, choose **Cluster** > **Services** > **Doris**, and click **Configurations**. If Kerberos authentication is enabled for the cluster, enter the value of **https_port** for this parameter. Otherwise, enter the value of **http_port** for this parameter. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Database                        | Select the database where the watermark table is stored from the drop-down list.                                                                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Target Table                    | Enter a unique table name. The table is automatically created when the table name entered does not exist.                                                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | Click **Test**. Otherwise, the next operation is not allowed.                                                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002269123245.png
      :alt: **Figure 4** Configuring source and target information

      **Figure 4** Configuring source and target information

#. Click **Next** and configure scheduling.

   -  If **Dataset Scope** is set to **All**, **Repeat** can be only set to **Once**.
   -  If **Dataset Scope** is set to **Incremental**, **Repeat** can be set to **Once** or **On Schedule**.

   If you set **Repeat** to **On Schedule**, set the parameters listed in :ref:`Table 3 <dataartsstudio_01_1021__en-us_topic_0000001676159785_en-us_topic_0000001676159741_en-us_topic_0141836089_table117064413127>`.

   .. _dataartsstudio_01_1021__en-us_topic_0000001676159785_en-us_topic_0000001676159741_en-us_topic_0141836089_table117064413127:

   .. table:: **Table 3** Parameters for periodic scheduling

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================+
      | \*Date                            | Period during which the task takes effect.                                                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Cycle                           | The frequency at which a task is executed. The options are:                                                                                                                                           |
      |                                   |                                                                                                                                                                                                       |
      |                                   | -  **minutes**: Select the scheduling start time and end time, and set the interval in minutes.                                                                                                       |
      |                                   | -  **hours**: Select the scheduling start time and end time, and set the interval in hours.                                                                                                           |
      |                                   | -  **Day**: Set the scheduling time everyday.                                                                                                                                                         |
      |                                   | -  **Week**: Select a day in a week and set the specific time to start scheduling.                                                                                                                    |
      |                                   | -  **Month**: Select a day in a month and set the specific time to start scheduling.                                                                                                                  |
      |                                   |                                                                                                                                                                                                       |
      |                                   | For example, you can set **Cycle** to **Week**, **Time** to **15:52**, and **Time Range** to **Tuesday**. In this case, the task is executed at 15:52 every Tuesday within the configured date range. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Start now                         | If you select **Start now**, the task is scheduled immediately.                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002234243852.png
      :alt: **Figure 5** Configuring scheduling

      **Figure 5** Configuring scheduling

#. Click **OK**.

Related Operations
------------------

-  Editing a task: On the **Data Watermark Embedding** page, locate a task and click **Edit** in the **Operation** column.

   A task in the **Scheduling** state cannot be edited.

-  Deleting tasks: On the **Data Watermark Embedding** page, locate a task, click **More** in the **Operation** column, and select **Delete**. To delete multiple tasks at a time, select the tasks and click **Delete** above the task list.

   A task in the **Scheduling** state cannot be deleted.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Running or scheduling a task: On the **Data Watermark Embedding** page, locate a task and click **Run** in the **Operation** column or click **More** in the **Operation** column and select **Start**.

   You can determine whether a task is scheduled once or repeatedly based on the scheduling period.

-  Viewing running instance logs: On the **Data Watermark Embedding** page, locate a task and click |image1| to expand instances. Then click **View Log**.

   If a task fails to be executed, you can locate the failure cause based on logs, rectify the fault, and try the task again. If the fault persists, contact technical support.

.. |image1| image:: /_static/images/en-us_image_0000002269123157.png
