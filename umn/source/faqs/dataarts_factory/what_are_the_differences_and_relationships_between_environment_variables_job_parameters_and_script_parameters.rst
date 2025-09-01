:original_name: dataartsstudio_03_0136.html

.. _dataartsstudio_03_0136:

What Are the Differences and Relationships Between Environment Variables, Job Parameters, and Script Parameters?
================================================================================================================

Symptom
-------

Differences and relationships between environment variables, job parameters, and script parameters

Solution
--------

The application scopes of workspace environment variables, job parameters, and script parameters are different. If a workspace environment variable, a job parameter, and a script parameter have the same name, their priorities are as follows: **job parameter > workspace environment variable > script parameter**.

Introduction and usage of environment variables, job parameters, and script parameters are as follows:

-  Variables and constants can be defined in environment variables. Environment variables take effect in current workspace.

   -  The value of a variable (such as **workspace name**) varies depending on the workspace. When exporting a variable from a workspace and import it to another workspace, you must reconfigure its value.
   -  The value of a constant in different workspaces is the same. When importing a constant to another workspace, you do not need to reconfigure its value.


   .. figure:: /_static/images/en-us_image_0000002234076288.png
      :alt: **Figure 1** Environment variable

      **Figure 1** Environment variable

-  Parameters and constants can be defined in job parameters. Job parameters take effect in current job.

   -  The value of a parameter varies depending on jobs. When exporting a parameter from a workspace and import it to another workspace, you must reconfigure its value.
   -  The value of a constant in different jobs is the same. When importing a constant to another job, you do not need to reconfigure its value.


   .. figure:: /_static/images/en-us_image_0000002269195581.png
      :alt: **Figure 2** Job parameter.

      **Figure 2** Job parameter.

-  Script parameters take effect in current script and it can be used in the following ways.

   -  Enter SQL script parameters in the script editor (Flink SQL is not supported). If the script is executed independently, you can configure the parameters in the lower part of the editor, as shown in :ref:`Figure 3 <dataartsstudio_03_0136__fig136485075917>`. If the script is executed by job scheduling, you can assign values to the parameters based on node attributes, as shown in :ref:`Figure 4 <dataartsstudio_03_0136__fig1236415017593>`.
   -  For Shell scripts, you can enter a parameter and an interactive parameter to transfer the parameters.
   -  For Python scripts, you can enter a parameter and an interactive parameter to transfer the parameters.

   .. _dataartsstudio_03_0136__fig136485075917:

   .. figure:: /_static/images/en-us_image_0000002269195577.png
      :alt: **Figure 3** Configuring script parameters when the script is executed independently

      **Figure 3** Configuring script parameters when the script is executed independently

   .. _dataartsstudio_03_0136__fig1236415017593:

   .. figure:: /_static/images/en-us_image_0000002269115493.png
      :alt: **Figure 4** Configuring script parameters when the script is executed by job scheduling

      **Figure 4** Configuring script parameters when the script is executed by job scheduling
