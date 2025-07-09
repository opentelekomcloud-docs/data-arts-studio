:original_name: dataartsstudio_01_0432.html

.. _dataartsstudio_01_0432:

Job Development Process
=======================

The job development function provides the following capabilities:

-  Provides a graphical designer that allows you to quickly build a data processing workflow by drag-and-drop.
-  Presets multiple job types, such as data integration, computing and analysis, data monitoring, and resource management, and completes complex data analysis and processing based on dependencies between jobs.
-  Supports various scheduling modes.
-  Supports job import and export.
-  Monitors job status and sends job result notifications.
-  Provides editing locks for collaborative development.
-  Supports job version management and generation of saved and submitted versions.

   .. note::

      If you save a script multiple times within a minute, only one version is recorded. If the intermediate data is important, you can click **Save new version** to save and add a version.

-  Allows you to copy long job names. Click |image1|, perform fuzzy search to query matched scripts, and click the copy button next to a long job name to copy it.
-  Allows you to right-click a job to quickly copy the job name and to quickly close an opened job tab page.
-  Provides a link in the execution results of single-task MRS Spark SQL and MRS Hive SQL jobs that use a connection of the MRS API type. Through this link, you can switch to MRS Yarn to view execution logs.
-  Allows you to switch to the task release page by clicking **Release** when developing a job in enterprise mode.
-  Allows you to filter submitted, unsubmitted, scheduled, and unscheduled jobs. Unsubmitted jobs are marked in red, and unscheduled jobs are marked in yellow.
-  Allows you to configure the SQL editor style for single-task jobs. Click **Style Configuration** to configure the editor, icon display, annotation templates, and shortcut keys that can be used in the SQL script editor.
-  Allows you to view single-task SQL query results in a table or list. You can click **Style Configuration** and set **SQL Query Result Display Mode** on the **Configure Editor** tab page.

Before developing a job, you can learn about the basic job development process.


.. figure:: /_static/images/en-us_image_0000002305406665.png
   :alt: **Figure 1** Job development process

   **Figure 1** Job development process

#. Create a job: Currently, two job types are available: batch and real-time, which are used for batch data processing and real-time connection data processing, respectively. Batch jobs support pipeline and single-node modes. For details, see :ref:`Creating a Job <dataartsstudio_01_0434>`.
#. Develop the job: Develop the created job. You can orchestrate and configure nodes. For details, see :ref:`Developing a Pipeline Job <dataartsstudio_01_0435>`.
#. Schedule the job: Configure job scheduling tasks. For details, see :ref:`Setting Up Scheduling for a Job <dataartsstudio_01_0470>`.

   -  If the processing mode of a job is batch processing, configure scheduling types for jobs. Three scheduling types are supported: run once, run periodically, and event-based. For details, see :ref:`Setting Up Scheduling for a Job Using the Batch Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section1590152794714>`.
   -  If the processing mode of a job is real-time processing, configure scheduling types for nodes. Three scheduling types are supported: run once, run periodically, and event-based. For details, see :ref:`Setting Up Scheduling for Nodes of a Job Using the Real-Time Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section644754422910>`.

#. Submit a version and unlock the script: After performing this step, the job can be scheduled and modified by other developers. For details, see :ref:`Submitting a Version <dataartsstudio_01_0902>`.
#. (Optional) Manage the job: After the job development is complete, you can manage the job as required. For details, see :ref:`(Optional) Managing Jobs <dataartsstudio_01_0408>`.
#. Release the job. This step is required in enterprise mode. For details, see :ref:`Releasing a Job Task <dataartsstudio_01_1903>`.

.. |image1| image:: /_static/images/en-us_image_0000002270846790.png
