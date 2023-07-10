:original_name: dataartsstudio_01_0434.html

.. _dataartsstudio_01_0434:

Creating a Job
==============

A job is composed of one or more nodes that are performed collaboratively to complete data operations. Before developing a job, create a new one.

Prerequisites
-------------

Each workspace can hold a maximum of 10,000 jobs. Ensure that the number of your jobs does not reach this upper limit.

(Optional) Creating a Directory
-------------------------------

If a directory exists, you do not need to create one.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory list, right-click a directory and choose **Create Directory** from the shortcut menu.

#. In the **Create Directory** dialog box, configure directory parameters based on :ref:`Table 1 <dataartsstudio_01_0434__en-us_topic_0099797006_table15634204645014>`.

   .. _dataartsstudio_01_0434__en-us_topic_0099797006_table15634204645014:

   .. table:: **Table 1** Job directory parameters

      +------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                           |
      +==================+=======================================================================================================================================+
      | Directory Name   | Name of a job directory. The name must contain 1 to 64 characters, including only letters, numbers, underscores (_), and hyphens (-). |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Parent directory of the job directory. The parent directory is the root directory by default.                                         |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.


Creating a Job
--------------

The quantity of jobs is less than the maximum quota (10,000).

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Create a job using either of the following methods:

   Method 1: On the **Develop Job** page, click **Create Job**.


   .. figure:: /_static/images/en-us_image_0000001373288653.png
      :alt: **Figure 3** Creating a job (method 1)

      **Figure 3** Creating a job (method 1)

   Method 2: In the directory list, right-click a directory and choose **Create Job** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0000001373408333.png
      :alt: **Figure 4** Creating a job (method 2)

      **Figure 4** Creating a job (method 2)

#. In the displayed dialog box, configure job parameters. :ref:`Table 2 <dataartsstudio_01_0434__en-us_topic_0099797006_table65314728174945>` describes the job parameters.

   .. _dataartsstudio_01_0434__en-us_topic_0099797006_table65314728174945:

   .. table:: **Table 2** Job parameters

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Job Name                          | Name of the job. The name must contain 1 to 128 characters, including only letters, numbers, hyphens (-), underscores (_), and periods (.).                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Processing Mode                   | Type of the job.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  **Batch processing**: Data is processed periodically in batches based on the scheduling plan, which is used in scenarios with low real-time requirements. This type of job is a pipeline that consists of one or more nodes and is scheduled as a whole. It cannot run for an unlimited period of time, that is, it must end after running for a certain period of time.                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |    You can configure job-level scheduling tasks for this type of job. That is, the job is scheduled as a whole. For details, see :ref:`Setting Up Scheduling for a Job Using the Batch Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section1590152794714>`.                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  **Real-time processing**: Data is processed in real time, which is used in scenarios with high real-time performance. This type of job is a business relationship that consists of one or more nodes. You can configure scheduling policies for each nodes, and the tasks started by nodes can keep running for an unlimited period of time. In this type of job, lines with arrows represent only service relationships, rather than task execution processes or data flows.        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |    You can configure node-level scheduling tasks for this type of job, that is, each node can be independently scheduled. For details, see :ref:`Setting Up Scheduling for Nodes of a Job Using the Real-Time Processing Mode <dataartsstudio_01_0470__en-us_topic_0099797007_section644754422910>`.                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Creation Method                   | Selects a job creation mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  Create Empty Job: Create an empty job.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   | -  Create Based on Template: Create a job using a template.                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory                  | Directory to which the job belongs. The root directory is selected by default.                                                                                                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Owner                             | Owner of the job.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Priority                          | Priority of the job. The value can be **High**, **Medium**, or **Low**.                                                                                                                                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                            | After an agency is configured, the job interacts with other services as an agency during job execution. If an agency has been configured for the workspace by referring to :ref:`Configuring a Workspace-Level Agency <dataartsstudio_01_0555__section3485198599>`, the new job uses the workspace-level agency by default. You can also change the agency to a job-level agency by referring to :ref:`Configuring a Job-level Agency <dataartsstudio_01_0555__section20224154881414>`. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |    Job-level agency takes precedence over workspace-level agency.                                                                                                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Path                          | Selects the OBS path to save job logs. By default, logs are stored in a bucket named **dlf-log-**\ {*Projectid*}.                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |    -  If you want to customize a storage path, select the bucket that you have created on OBS.                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    -  Ensure that you have the read and write permissions on the OBS path specified by this parameter. Otherwise, the system cannot write logs or display logs.                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
