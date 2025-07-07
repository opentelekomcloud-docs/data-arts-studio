:original_name: dataartsstudio_01_1282.html

.. _dataartsstudio_01_1282:

Configuring a Template
======================

This section describes how to create and use a Flink SQL template. When writing Flink SQL code, you can use an SQL template for repeated service logic. In addition, you can use a job parameter template when configuring job parameters.

Constraints
-----------

This function applies to the following scenarios:

-  Use a script template for a Flink SQL script.
-  During pipeline job development, use a Fink SQL script which uses a script template for the MRS Flink Job node and use a parameter template for **Program Parameter** of the MRS Flink Job node.
-  Use a script template in a single-task Flink SQL job.
-  Use template parameters in a single-task Flink JAR job.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Templates**.

   -  Create a script template.

      a. On the **Script Templates** page, click **Add**.

      b. Set **Template Name**.

      c. Enter an SQL statement and reference script parameters.

      d. Configure the script template parameters. The parameter names cannot be changed, and the parameter values can be changed.


         .. figure:: /_static/images/en-us_image_0000002305406813.png
            :alt: **Figure 1** Creating a script template

            **Figure 1** Creating a script template

      e. Click **Save**.

         You can view, modify, or delete the created script template.

   -  Create a parameter template.

      a. On the **Parameter Templates** page, click **Add**.

      b. Set **Template Name**.

      c. Click **Add Parameter** and set parameter names and values. You can modify or delete parameters.


         .. figure:: /_static/images/en-us_image_0000002305406817.png
            :alt: **Figure 2** Creating a parameter template

            **Figure 2** Creating a parameter template

      d. Click **OK**.

         You can view, modify, or delete the created parameter template.

         For details about the application scenarios of script templates and parameter templates, see :ref:`Using Script Templates and Parameter Templates <dataartsstudio_01_1582>`.
