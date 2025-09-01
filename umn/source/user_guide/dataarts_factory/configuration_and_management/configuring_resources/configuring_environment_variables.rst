:original_name: dataartsstudio_01_0504.html

.. _dataartsstudio_01_0504:

Configuring Environment Variables
=================================

This topic describes how to configure and use environment variables.

Application Scenario
--------------------

Configure job parameters. If a parameter belongs to multiple jobs, you can extract this parameter as an environment variable. Environment variables can be imported and exported.

.. note::

   The roles that can configure workspace environment variables in the simple and enterprise mode are as follows:

   Simple mode: Both developers and administrators can create and edit environment variables in a workspace. This mode does not distinguish the development environment from the production environment. Developers can modify environment variables.

   Enterprise mode: Only administrators can create or edit environment variables in a workspace.

Importing Environment Variables
-------------------------------

This function is available only if the OBS service is available. If OBS is unavailable, variables can be imported from the local PC.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation tree on the left, choose **Specifications**.

#. Click **Environment Variables**. On the **Environment Variables** page, click **Import**.

#. In the **Import Environment Variable** dialog box, select an environment variable file from OBS or a local path and the duplicate name policy.


   .. figure:: /_static/images/en-us_image_0000002234075804.png
      :alt: **Figure 1** Importing Environment Variables

      **Figure 1** Importing Environment Variables

Exporting Environment Variables
-------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation tree on the left, choose **Specifications**.
#. Click **Environment Variable**. On the **Environment Variable** page, click **Export** to export environment variables.

.. _dataartsstudio_01_0504__en-us_topic_0175328117_section7729152119279:

Configuration Method
--------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation tree on the left, choose **Specifications**.

#. On the **Environment Variable** page, set the variables or constants listed in :ref:`Table 1 <dataartsstudio_01_0504__table152451023155711>` and click **Save**.

   .. note::

      The difference between a variable and a constant lies in whether their values need to be reconfigured when they are imported to another workspace or project.

      -  The value of a variable (such as **workspace name**) varies depending on the workspace. When exporting a variable from a workspace and import it to another workspace, you must reconfigure its value.
      -  The value of a constant in different workspaces is the same. When importing a constant to another workspace, you do not need to reconfigure its value.


   .. figure:: /_static/images/en-us_image_0000002234235624.png
      :alt: **Figure 2** Configuring environment variables

      **Figure 2** Configuring environment variables

   .. _dataartsstudio_01_0504__table152451023155711:

   .. table:: **Table 1** Configuring environment variables

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================================================================+
      | Parameter             | Yes                   | The parameter name must be unique, consist of 1 to 64 characters, and contain only letters, digits, underscores (**\_**), and hyphens (**-**).                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                                                                         |
      |                       |                       | The parameter name must be in the format set in :ref:`Configuring Script Variables <dataartsstudio_01_04501__section310213518565>`. For example, if the format set in the script variable definition is **${dlf.}**, the parameter name must be set to **dlf.**\ *xxx*. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Value                 | Yes                   | Parameter values support constants and EL expressions but do not support system functions. For example, **123** and **abc** are supported. If the parameter value is a string, add double quotation marks (""), for example, **"05"**.                                  |
      |                       |                       |                                                                                                                                                                                                                                                                         |
      |                       |                       | For details about how to use EL expressions, see :ref:`Expression Overview <dataartsstudio_01_0494>`.                                                                                                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description           | No                    | Parameter description                                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   You can add, modify, delete, and reset environment variables.

   -  Add an environment variable: Click **Add**. After an environment variable is added, **Add** is displayed for it.
   -  Edit an environment variable: If the parameter value is a constant, change the parameter value in the text box. If the parameter value is an EL expression, click |image1| next to the text box to edit the EL expression. Click **Save**. After an environment variable is modified, **Modify** is displayed for it.
   -  Delete an environment variable: Click **Delete** next to the parameter value text box. After an environment variable is deleted, **Delete** is displayed for it.
   -  Reset an environment variable: When modifying or deleting an environment variable, you can click **Reset** in the **Operation** column to reset the variable value to the original value.

How-Tos
-------

The configured environment variables can be used in either of the following ways:

#. ${Environment variable}
#. #{Evn.get("Environment variable")}

Example
-------

Context:

-  A job named **test** has been created in the DataArts Factory module.
-  An environment variable has been added. The parameter name is **job** and the parameter value is **123**.

#. Open **test** and drag a **Create OBS** node from the node library.

#. On the **Node Properties** tab page, configure the node properties.


   .. figure:: /_static/images/en-us_image_0000002269114989.png
      :alt: **Figure 3** Configuring parameters for the Create OBS node

      **Figure 3** Configuring parameters for the Create OBS node

#. Click **Save** and then **Monitor** to monitor the running status of the job.

.. |image1| image:: /_static/images/en-us_image_0000002234075784.png
