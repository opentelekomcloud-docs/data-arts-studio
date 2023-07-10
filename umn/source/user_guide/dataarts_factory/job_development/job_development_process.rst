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
-  Supports job version management.

Before developing a job, you can learn about the basic job development process from :ref:`Figure 1 <dataartsstudio_01_0432__fig751515296455>`.

.. _dataartsstudio_01_0432__fig751515296455:

.. figure:: /_static/images/en-us_image_0000001373288629.png
   :alt: **Figure 1** Job development process

   **Figure 1** Job development process

#. Create a job: Currently, two job types are available: batch and real-time, which are used for batch data processing and real-time connection data processing, respectively. For details, see :ref:`Creating a Job <dataartsstudio_01_0434>`.
#. Develop the job: Develop the created job. You can orchestrate and configure nodes. For details, see :ref:`Developing a Job <dataartsstudio_01_0435>`.
#. Schedule the job: Configure job scheduling tasks. For details, see :ref:`Setting Up Scheduling for a Job <dataartsstudio_01_0470>`.

   -  If the processing mode of a job is batch processing, configure scheduling types for jobs. Three scheduling types are supported: run once, run periodically, and event-based. For details, see :ref:`Setting Up Scheduling for a Job Using the Batch Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section1590152794714>`.
   -  If the processing mode of a job is real-time processing, configure scheduling types for nodes. Three scheduling types are supported: run once, run periodically, and event-based. For details, see :ref:`Setting Up Scheduling for Nodes of a Job Using the Real-Time Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section644754422910>`.

#. Submit a version and unlock the script: After performing this step, the job can be scheduled and modified by other developers. For details, see :ref:`Submitting a Version and Unlocking the Script <dataartsstudio_01_0902>`.
#. (Optional) Manage the job: After the job development is complete, you can manage the job as required. For details, see :ref:`(Optional) Managing Jobs <dataartsstudio_01_0408>`.
