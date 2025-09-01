:original_name: dataartsstudio_01_0519.html

.. _dataartsstudio_01_0519:

Managing Resources
==================

You can upload custom code or text files as resources on Manage Resource and schedule them when running nodes. Nodes that can invoke resources include DLI Spark, MRS Spark, DLI Flink Job, and MRS MapReduce.

After creating a resource, configure the file associated with the resource. Resources can be directly referenced in jobs. When the resource file is changed, you only need to change the resource reference location. You do not need to modify the job configuration. For details about resource usage examples, see :ref:`Developing a DLI Spark Job <dataartsstudio_01_0521>`.

Constraints
-----------

This function depends on OBS or MRS HDFS.

(Optional) Creating a Directory
-------------------------------

If a directory exists, you do not need to create one.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. In the directory list, click |image1|. In the displayed dialog box, configure directory parameters. :ref:`Table 1 <dataartsstudio_01_0519__en-us_topic_0165312432_table07684185145>` describes the directory parameters.

   .. _dataartsstudio_01_0519__en-us_topic_0165312432_table07684185145:

   .. table:: **Table 1** Resource directory parameters

      +------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                           |
      +==================+=======================================================================================================================================================+
      | Directory Name   | Name of the resource directory. The name must contain 1 to 32 characters, including only letters, numbers, underscores (**\_**), and hyphens (**-**). |
      +------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Parent directory of the resource directory. The parent directory is the root directory by default.                                                    |
      +------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. _dataartsstudio_01_0519__en-us_topic_0165312432_section6325757145320:

Creating a Resource
-------------------

You have enabled OBS before creating a resource.

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. Click **Create Resource**. In the displayed dialog box, configure resource parameters. :ref:`Table 2 <dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547>` describes the resource parameters. Click **OK**.

   .. _dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547:

   .. table:: **Table 2** Resource management parameters

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                   |
      +=======================+=======================+===============================================================================================================================+
      | Name                  | Yes                   | Name of the resource. The name must contain 1 to 32, including only letters, numbers, underscores (_), and hyphens (-).       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Yes                   | File type of the resource. Possible values:                                                                                   |
      |                       |                       |                                                                                                                               |
      |                       |                       | -  jar: JAR file                                                                                                              |
      |                       |                       | -  pyFile: User Python file                                                                                                   |
      |                       |                       | -  file: User file                                                                                                            |
      |                       |                       | -  archive: User AI model file The supported file name extensions are **zip**, **tgz**, **tar.gz**, **tar**, and **jar**.     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Resource Location     | Yes                   | Location of the resource. OBS and HDFS are supported. HDFS supports only MRS Spark, MRS Flink Job and MRS MapReduce nodes.    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | File Path             | Yes                   | Select an OBS file path when **Resource Location** is set to **OBS**.                                                         |
      |                       |                       |                                                                                                                               |
      |                       |                       | Select an MRS cluster name when **Resource Location** is set to **HDFS**.                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Depended Package      | No                    | This parameter is available only for DLI Spark nodes.                                                                         |
      |                       |                       |                                                                                                                               |
      |                       |                       | Depended JAR package that has been uploaded to OBS. This parameter is required when **Type** is set to **jar** or **pyFile**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory      | Yes                   | Directory to which the resource belongs. The root directory is selected by default.                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Description           | No                    | Descriptive information about the resource.                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

Editing a Resource
------------------

After a resource is created, you can modify resource parameters.

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.
#. In the **Operation** column of the resource, click **Edit**. In the displayed dialog box, modify the resource parameters. For details, see :ref:`Table 2 <dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547>`.
#. Click **OK**.

Deleting a Resource
-------------------

You can delete resources that are no longer needed.

Before deleting a resource, ensure that it is not used by any jobs.

.. important::

   If you are trying to delete a resource that is being used by jobs, the **Delete Resource** dialog box is displayed. When you click **OK**, the **Reference List** dialog box is displayed, in which you can view the jobs that are using the resource and click **View** in the **Operation** column to go to the job details page.

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.
#. In the **Operation** column of the resource, click **Delete**. The **Delete Resource** dialog box is displayed.
#. Click **Yes**.

Importing a Resource
--------------------

To import a resource, perform the following operations:

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.
#. In the resource directory, click |image2| and select **Import Resource**. The **Import Resource** dialog box is displayed.
#. Select the resource file that has been uploaded to OBS and click **Next**. After the import is complete, click **Close**.

Exporting a Resource
--------------------

To export a resource, perform the following operations:

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.
#. In the resource directory, select a resource, click |image3|, and select **Export Resource**. The system starts downloading the resource to the local PC.

Viewing Resource References
---------------------------

To view the references of a resource, perform the following operations:

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.
#. Right-click a resource in the list and select **View Reference**.
#. In the displayed **Reference List** dialog box, view the references of the resource.

.. |image1| image:: /_static/images/en-us_image_0000002234235724.png
.. |image2| image:: /_static/images/en-us_image_0000002234235716.png
.. |image3| image:: /_static/images/en-us_image_0000002234075884.png
