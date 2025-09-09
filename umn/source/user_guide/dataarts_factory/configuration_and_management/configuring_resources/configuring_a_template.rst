:original_name: dataartsstudio_01_1282.html

.. _dataartsstudio_01_1282:

Configuring a Template
======================

This section describes how to create and use a template. When writing code, you can use an SQL template for repeated service logic. In addition, you can use a job parameter template when configuring job parameters.

Constraints
-----------

This function applies to the following scenarios:

-  Use a script template for a Flink SQL script.
-  During pipeline job development, use a Fink SQL script which uses a script template for the MRS Flink Job node and use a parameter template for **Program Parameter** of the MRS Flink Job node.
-  Use a script template in a single-task Flink SQL job.
-  Use template parameters in a single-task Flink JAR job.
-  You can use parameter templates for Spark SQL and Hive SQL scripts and single-task jobs. For details about how to use a template, see :ref:`Configuring a Default Item <dataartsstudio_01_04501>`.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Templates**.

   -  Create a script template.

      a. On the **Script Templates** page, click **Add**.

      b. Set **Template Name**.

      c. Enter an SQL statement and reference script parameters.

      d. Configure the script template parameters. The parameter names cannot be changed, and the parameter values can be changed.


         .. figure:: /_static/images/en-us_image_0000002269205393.png
            :alt: **Figure 1** Creating a script template

            **Figure 1** Creating a script template

      e. Click **Save**.

         You can view, modify, or delete the created script template.

   -  Create a parameter template.

      a. On the **Parameter Templates** page, click **Add**.

      b. Set **Template Name**.

      c. Click **Add Parameter** Set parameter names and values. You can modify or delete parameters.

      d. Click **OK**.

         You can view, modify, or delete the created parameter template.

         For details about the application scenarios of script templates and parameter templates, see :ref:`Using Script Templates and Parameter Templates <dataartsstudio_01_1582>`.
