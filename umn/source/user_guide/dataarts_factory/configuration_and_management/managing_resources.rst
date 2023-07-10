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

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

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

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. Click **Create Resource**. In the displayed dialog box, configure resource parameters. :ref:`Table 2 <dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547>` describes the resource parameters. Click **OK**.

   .. _dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547:

   .. table:: **Table 2** Resource management parameters

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================+
      | Name                  | Yes                   | Name of the resource. The name must contain 1 to 32, including only letters, numbers, underscores (_), and hyphens (-).                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Yes                   | File type of the resource. Possible values:                                                                                                                             |
      |                       |                       |                                                                                                                                                                         |
      |                       |                       | -  jar: JAR file                                                                                                                                                        |
      |                       |                       | -  pyFile: User Python file                                                                                                                                             |
      |                       |                       | -  file: User file                                                                                                                                                      |
      |                       |                       | -  archive: User AI model file                                                                                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Location     | Yes                   | Location of the resource. OBS and HDFS are supported. HDFS supports only MRS Spark, MRS Flink Job and MRS MapReduce nodes.                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Main JAR package      | Yes                   | -  If **Resource Location** is **OBS**, select the main JAR package that has been uploaded to OBS.                                                                      |
      |                       |                       | -  If **Resource Location** is **HDFS**, select the main JAR package that has been uploaded to HDFS.                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Depended JAR Package  | No                    | Depended JAR package that has been uploaded to OBS. This parameter is required when **Type** is set to **jar** and **Resource Location** is set to **OBS** or **HDFS**. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Resource       | Yes                   | Specific resource file.                                                                                                                                                 |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Path          | Yes                   | Path to a directory where the resource is stored. This parameter is required only when **Resource Location** is set to **Local**.                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description           | No                    | Descriptive information about the resource.                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory      | Yes                   | Directory to which the resource belongs. The root directory is selected by default.                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Editing a Resource
------------------

After a resource is created, you can modify resource parameters.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 3** DataArts Factory

      **Figure 3** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. In the **Operation** column of the resource, click **Edit**. In the displayed dialog box, modify the resource parameters. For details, see :ref:`Table 2 <dataartsstudio_01_0519__en-us_topic_0165312432_table3484574617547>`.

#. Click **OK**.

Deleting a Resource
-------------------

You can delete resources that are no longer needed.

Before deleting a resource, ensure that it is not used by any jobs. When you delete a resource, the system checks the jobs that are referencing the resource. The **Version** column in the reference list indicates the job versions that are referencing the resource. After you click **Delete**, the job will be deleted as well as all version information about the job.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 4** DataArts Factory

      **Figure 4** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. In the **Operation** column of the resource, click **Delete**. The **Delete Resource** dialog box is displayed.

#. Click **Yes**.

Importing a Resource
--------------------

To import a resource, perform the following operations:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. In the resource directory, click |image2| and select **Import Resource**. The **Import Resource** dialog box is displayed.

#. Select the resource file that has been uploaded to OBS and click **Next**. After the import is complete, click **Close**.

Exporting a Resource
--------------------

To export a resource, perform the following operations:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 6** DataArts Factory

      **Figure 6** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. In the resource directory, select a resource, click |image3|, and select **Export Resource**. The system starts downloading the resource to the local PC.

Viewing Resource References
---------------------------

To view the references of a resource, perform the following operations:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 7** DataArts Factory

      **Figure 7** DataArts Factory

#. In the left navigation pane, choose **Configuration** > **Manage Resource**.

#. Right-click a resource in the list and select **View Reference**.

#. In the displayed **Reference List** dialog box, view the references of the resource.

.. |image1| image:: /_static/images/en-us_image_0000001373168665.png
.. |image2| image:: /_static/images/en-us_image_0000001373408053.png
.. |image3| image:: /_static/images/en-us_image_0000001322088028.png
