:original_name: dataartsstudio_01_1582.html

.. _dataartsstudio_01_1582:

Using Script Templates and Parameter Templates
==============================================

Scenario
--------

This function applies to the following scenarios:

-  Use a script template for a Flink SQL script.
-  During pipeline job development, use a Fink SQL script which uses a script template for the MRS Flink Job node and use a parameter template for **Program Parameter** of the MRS Flink Job node.
-  Use a script template in a single-task Flink SQL job.
-  Use template parameters in a single-task Flink JAR job.

   .. note::

      When you use a script template in a script, ensure that the SQL statement is in **@@{Script template}** format.

Prerequisites
-------------

A template has been created. If no template is available, create one by referring to :ref:`Configuring a Template <dataartsstudio_01_1282>`.

Using Templates
---------------

-  Use a script template for a Flink SQL script.

   #. In the navigation pane on the DataArts Studio console, choose **Data Development** > **Develop Script**.

   #. Right-click a script directory and select **Create Flink SQL Script**.

   #. Click **Template**. In the slide-out pane, select a template, for example, **412_mobna**. You can select multiple templates.


      .. figure:: /_static/images/en-us_image_0000002269199961.png
         :alt: **Figure 1** Using a script template

         **Figure 1** Using a script template

   #. Click **Save** to create the **412_test** script.

-  During the development of a pipeline job, use the Flink SQL script which uses a script template for the MRS Flink Job node.

   #. In the navigation pane on the DataArts Factory console, choose **Data Development** > **Develop Job**.

   #. Right-click a job directory and select **Create Job** to create a batch processing job in pipeline mode.

   #. On the displayed data development page, drag an MRS Flink Job node to the canvas.

   #. Select **Flink SQL job** for **Job Type** and select the Flink SQL script for **Script Path**.

      After the script is selected, the template parameters and values used by the script are automatically displayed.


      .. figure:: /_static/images/en-us_image_0000002234080688.png
         :alt: **Figure 2** Using the Flink SQL script

         **Figure 2** Using the Flink SQL script

-  During the development of a pipeline job, use a parameter template in **Program Parameter** of the MRS Flink Job node.

   #. Set **MRS Cluster**.

   #. Program parameters are automatically displayed. Click **Select Template** and select a parameter template. You can also select multiple templates.

      The parameter names and values are automatically displayed.


      .. figure:: /_static/images/en-us_image_0000002269199973.png
         :alt: **Figure 3** Using a parameter template for program parameters

         **Figure 3** Using a parameter template for program parameters

-  Use a script template in a single-task Flink SQL job.

   #. In the navigation pane on the DataArts Factory console, choose **Data Development** > **Develop Job**.

   #. Right-click a job directory and select **Create Job** to create a real-time processing job in single-task Flink SQL mode.

   #. Click **Template**. In the slide-out pane, select a template, for example, **412_mobna**. You can select multiple templates.


      .. figure:: /_static/images/en-us_image_0000002269199985.png
         :alt: **Figure 4** Using a script template in a single-task Flink SQL job

         **Figure 4** Using a script template in a single-task Flink SQL job

      |image1|

-  Use template parameters in a single-task Flink JAR job.

   #. In the navigation pane on the DataArts Factory console, choose **Data Development** > **Develop Job**.

   #. Right-click a job directory and select **Create Job** to create a real-time processing job in single-task Flink JAR mode.

   #. Set **MRS Cluster**.

   #. Program parameters are automatically displayed. Click **Select Template** and select a parameter template. You can also select multiple templates.

      The parameter names and values are automatically displayed.


      .. figure:: /_static/images/en-us_image_0000002234080700.png
         :alt: **Figure 5** Using a script template in a single-task Flink JAR job.

         **Figure 5** Using a script template in a single-task Flink JAR job.

.. |image1| image:: /_static/images/en-us_image_0000002234240552.png
