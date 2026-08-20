:original_name: dataartsstudio_04_0006.html

.. _dataartsstudio_04_0006:

Step 4: Metadata Collection
===========================

To manage and monitor the raw data migrated to the cloud on DataArts Studio, you can use the DataArts Catalog module to collect and monitor the metadata at the Source Data Integration (SDI) layer.

.. _dataartsstudio_04_0006__en-us_topic_0233673152_section8634519275:

Collecting and Monitoring Metadata
----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

#. Choose **Metadata Collection** > **Collection Tasks** in the left navigation pane, right-click a directory in the directory tree, and choose **Create Directory** from the shortcut menu. In the dialog box displayed, enter the directory name, for example, **transport**, select a parent directory, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269111409.png
      :alt: **Figure 1** Collection Tasks

      **Figure 1** Collection Tasks

#. Select the **transport** directory in the directory tree and click **Add Task**.

#. Create a collection task named **transport_all**, configure parameters shown in the following figure, and click **Next**.


   .. figure:: /_static/images/en-us_image_0000002234072204.png
      :alt: **Figure 2** Creating a collection task (basic settings)

      **Figure 2** Creating a collection task (basic settings)


   .. figure:: /_static/images/en-us_image_0000002234072216.png
      :alt: **Figure 3** Creating a metadata collection task

      **Figure 3** Creating a metadata collection task

#. Configure the scheduling mode and click **Submit**.


   .. figure:: /_static/images/en-us_image_0000002269111457.png
      :alt: **Figure 4** Configuring the scheduling mode

      **Figure 4** Configuring the scheduling mode

#. In the collection task list, locate the new collection task and click **Start Scheduling** in the row that contains the task.


   .. figure:: /_static/images/en-us_image_0000002234232068.png
      :alt: **Figure 5** Starting scheduling

      **Figure 5** Starting scheduling

#. Choose **Metadata Collection** > **Task Monitoring** in the left navigation pane, and check whether the collection task is successful.


   .. figure:: /_static/images/en-us_image_0000002234072192.png
      :alt: **Figure 6** Viewing a monitoring task

      **Figure 6** Viewing a monitoring task

#. After the collection task is successful, choose **Data Map** > **Data Catalog** in the left navigation pane, click the **Technical Assets** tab, and set filter criteria. For example, select **mrs_hive_link** for **Data Connections** and **Table** for **Types**. All tables that meet the filter criteria are displayed.


   .. figure:: /_static/images/en-us_image_0000002269191517.png
      :alt: **Figure 7** Technical assets

      **Figure 7** Technical assets

#. Click the target metadata name to view its details.


   .. figure:: /_static/images/en-us_image_0000002234072248.png
      :alt: **Figure 8** Metadata details

      **Figure 8** Metadata details
