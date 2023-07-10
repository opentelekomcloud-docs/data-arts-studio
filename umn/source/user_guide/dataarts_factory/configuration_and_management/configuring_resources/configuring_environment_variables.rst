:original_name: dataartsstudio_01_0504.html

.. _dataartsstudio_01_0504:

Configuring Environment Variables
=================================

This topic describes how to configure and use environment variables.

Application Scenario
--------------------

Configure job parameters. If a parameter belongs to multiple jobs, you can extract this parameter as an environment variable. Environment variables can be imported and exported.

Importing Environment Variables
-------------------------------

This function is available only if the OBS service is available. If OBS is unavailable, variables can be imported from the local PC.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the navigation tree on the left, choose **Specifications**.

#. Click **Environment Variables**. On the **Environment Variables** page, click **Import**.

#. In the **Import Environment Variable** dialog box, select the environment variable file that has been uploaded to OBS or a local directory and the duplicate name policy.


   .. figure:: /_static/images/en-us_image_0000001373288353.jpg
      :alt: **Figure 2** Importing environment variables

      **Figure 2** Importing environment variables

.. _dataartsstudio_01_0504__en-us_topic_0175328117_section7729152119279:

Configuration Method
--------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 3** DataArts Factory

      **Figure 3** DataArts Factory

#. In the navigation tree on the left, choose **Specifications**.

#. On the **Environment Variable** page, set the variables or constants listed in :ref:`Table 1 <dataartsstudio_01_0504__table152451023155711>` and click **Save**.

   .. note::

      The difference between a variable and a constant lies in whether their values need to be reconfigured when they are imported to another workspace or project.

      -  The value of a variable (such as **workspace name**) varies depending on the workspace. When exporting a variable from a workspace and import it to another workspace, you must reconfigure its value.
      -  The value of a constant in different workspaces is the same. When importing a constant to another workspace, you do not need to reconfigure its value.

   .. _dataartsstudio_01_0504__table152451023155711:

   .. table:: **Table 1** Configuring environment variables

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================+
      | Parameter             | Yes                   | The parameter name must be unique, consist of 1 to 64 characters, and contain only letters, digits, underscores (**\_**), and hyphens (**-**). |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Value                 | Yes                   | Parameter values support constants and EL expressions but do not support system functions. For example, **123** and **abc** are supported.     |
      |                       |                       |                                                                                                                                                |
      |                       |                       | For details about how to use EL expressions, see :ref:`Expression Overview <dataartsstudio_01_0494>`.                                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   After configuring an environment variable, you can add, edit, or delete it.

   -  **Add**: Click **Add** to add an environment variable.
   -  **Edit**: If the parameter value is a constant, change the parameter value in the text box. If the parameter value is an EL expression, click |image1| next to the text box to edit the EL expression. Click **Save**.
   -  **Delete**: Click |image2| next to the parameter value text box to delete the environment variable.

How-Tos
-------

The configured environment variables can be used in either of the following ways:

#. ${Environment variable}
#. #{Evn.get("environment variable")}

Example
-------

Context:

-  A job named **test** has been created in the DataArts Factory module.
-  An environment variable has been added. The parameter name is **job** and the parameter value is **123**.

#. Open **test** and drag a **Create OBS** node from the node library.

#. On the **Node Properties** tab page, configure the node properties.


   .. figure:: /_static/images/en-us_image_0000001322088008.png
      :alt: **Figure 4** Create OBS

      **Figure 4** Create OBS

#. Click **Save** and then **Monitor** to monitor the running status of the job.

.. |image1| image:: /_static/images/en-us_image_0000001373087845.png
.. |image2| image:: /_static/images/en-us_image_0000001373168649.png
