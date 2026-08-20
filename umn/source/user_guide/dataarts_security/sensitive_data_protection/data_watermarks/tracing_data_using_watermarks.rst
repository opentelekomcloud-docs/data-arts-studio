:original_name: dataartsstudio_01_1022.html

.. _dataartsstudio_01_1022:

Tracing Data Using Watermarks
=============================

This section describes how to use watermarks to trace leaked data in files.

DataArts Security provides users with the source tracing function to accurately trace the leaked data. Users can check whether watermarks exist based on the leaked data file integrity and watermark traces, identify watermark traces, and accurately locate the security issues and find the personnel or departments accountable for the leakage problem.

Prerequisites
-------------

-  After obtaining the leaked data file, a CSV (Comma-Separated Values) file whose size does not exceed 20 MB has been generated and saved to the local host.
-  A data watermark embedding task has been created. For details, see :ref:`Embedding Data Watermarks <dataartsstudio_01_1021>`.

Notes and Constraints
---------------------

-  Watermarks can only be used to trace data in files no larger than 20 MB.
-  To trace data accurately, ensure the integrity and correctness of the data. The first column of the target table data file cannot be empty, and the file should contain more than 5,000 data records.

Creating a Data Watermark Source Tracing Task
---------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Data Watermark Source Tracing** from the left navigation bar, and click **Create** in the upper part of the displayed page.


   .. figure:: /_static/images/en-us_image_0000002269196145.png
      :alt: **Figure 1** Creating a source tracing task

      **Figure 1** Creating a source tracing task

#. In the displayed dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1022__en-us_topic_0000001627240326_table39921691916>`.


   .. figure:: /_static/images/en-us_image_0000002269196137.png
      :alt: **Figure 2** Creating a source tracing task

      **Figure 2** Creating a source tracing task

   .. _dataartsstudio_01_1022__en-us_topic_0000001627240326_table39921691916:

   .. table:: **Table 1** Parameters

      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                                                                                                                            |
      +=============+========================================================================================================================================================================================================+
      | Task        | The name of the watermark task to be created. Task names can include only letters, numbers, underscores (_), and hyphens (-), and cannot exceed 64 characters.                                         |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description | A description of the task. The description can contain a maximum of 1,024 characters.                                                                                                                  |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Source File | CSV file generated from the leaked data file. The file cannot be larger than 20 MB.                                                                                                                    |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Separator   | Select a separator from the drop-down list based on the uploaded CSV file. The options are **Comma (,)**, **Tab**, **Vertical bar (|)**, and **Semicolon (;)**. By default, **Comma (,)** is selected. |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After all settings are complete, click **Run**.

Related Operations
------------------

-  Viewing the source tracing result: On the **Data Watermark Source Tracing** page, locate a task and click **View Result** in the **Operation** column. Source tracing results are displayed only for the tasks that have been successfully executed.


   .. figure:: /_static/images/en-us_image_0000002234076868.png
      :alt: **Figure 3** Source tracing result

      **Figure 3** Source tracing result

-  Deleting tasks: On the **Data Watermark Source Tracing** page, locate a task and click **Delete** in the **Operation** column. To delete multiple tasks at a time, select the tasks and click **Delete** above the task list.

   A task in the **Scheduling** state cannot be deleted.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.
