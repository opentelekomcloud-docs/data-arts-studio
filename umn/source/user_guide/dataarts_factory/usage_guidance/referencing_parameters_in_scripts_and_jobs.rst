:original_name: dataartsstudio_01_7524.html

.. _dataartsstudio_01_7524:

Referencing Parameters in Scripts and Jobs
==========================================

This section describes how to reference parameters in scripts and jobs, application scope of the referenced parameters, and whether EL expressions and simple variable sets are supported, helping you better understand how to use workspace-level, script-level, and job-level parameters.

.. note::

   Parameters can be set in environment variables, job parameters, and script parameters, but their application scopes are different. If there is a conflict when parameters in environment variables, job parameters, and script parameters of the same name, the calling priority is: **job parameters > environment variables > script parameters**.

.. table:: **Table 1** Methods of using parameters

   +---------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Type                            | Scenario                                                                                                               | Scope             | Calling Method                                                                                                                  | Example                                         |
   +=================================+========================================================================================================================+===================+=================================================================================================================================+=================================================+
   | Environment variables/constants | When configuring job parameters, you can extract a parameter that belongs to multiple jobs as an environment variable. | Current workspace | ${*Environment variable*}                                                                                                       | EL expression: #{DateUtil.getDay(Job.planTime)} |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   | ${*Environment constant*}                                                                                                       | Simple variable set: ${yyyymmdd±N}              |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   | For details about the configuration method, see :ref:`Environment Variable <dataartsstudio_01_7524__section22181399319>`.       |                                                 |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Job variables/constants         | Job parameters can be used in any node in jobs.                                                                        | Current job       | ${*Job variable*}                                                                                                               | EL expression: #{DateUtil.now()}                |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   | ${*Job constant*}                                                                                                               | Simple variable set: ${yyyymm±N}                |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   | For details about the configuration method, see :ref:`Configuring Job Parameters <dataartsstudio_01_7524__section56401130635>`. |                                                 |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Script parameters               | Set the name and value of a custom field.                                                                              | Current script    | ${*Script parameter*}                                                                                                           | Example script parameters:                      |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   | For details about the configuration method, see :ref:`Script Parameter <dataartsstudio_01_7524__section04082466318>`.           | ${time}                                         |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   |                                                                                                                                 | ${yyyymmddhh24miss}                             |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   |                                                                                                                                 | ${job_id}                                       |
   |                                 |                                                                                                                        |                   |                                                                                                                                 |                                                 |
   |                                 |                                                                                                                        |                   |                                                                                                                                 | ${instance_id}                                  |
   +---------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+

.. note::

   Variables of an SQL script can be in ${} or ${dlf.} format. You can configure either type as needed. The configured variable format applies to SQL scripts, SQL statements in jobs, single-node jobs, and environment variables. For details about how to configure the script variable format, see :ref:`Configuring Script Variables <dataartsstudio_01_04501__section310213518565>`.

   The default variable format is **${}**.

.. _dataartsstudio_01_7524__section22181399319:

Environment Variable
--------------------

Variables and constants can be defined in environment variables. Environment variables take effect in current workspace.

-  The value of a variable (such as **workspace name**) varies depending on the workspace. When exporting a variable from a workspace and import it to another workspace, you must reconfigure its value.
-  The value of a constant in different workspaces is the same. When importing a constant to another workspace, you do not need to reconfigure its value.


.. figure:: /_static/images/en-us_image_0000002270790368.png
   :alt: **Figure 1** Environment Variable

   **Figure 1** Environment Variable

The specific application is as follows:

An environment variable has been added. The parameter name is **sdqw** and the parameter value is **wqewqewqe**.

#. Open a created job and drag a **Create OBS** node from the node library to the canvas.

#. On the **Node Properties** tab page, configure the node properties.


   .. figure:: /_static/images/en-us_image_0000002270790352.png
      :alt: **Figure 2** Create OBS

      **Figure 2** Create OBS

#. Click **Save** and then **Monitor** to monitor the running status of the job.

.. _dataartsstudio_01_7524__section56401130635:

Configuring Job Parameters
--------------------------

Parameters and constants can be defined in job parameters. Job parameters take effect in current job.

-  The value of a parameter varies depending on the job. You need to reconfigure the parameter.

-  The value of a constant in different jobs is the same. When importing a constant to another job, you do not need to reconfigure its value.


   .. figure:: /_static/images/en-us_image_0000002305440145.png
      :alt: **Figure 3** Job parameter.

      **Figure 3** Job parameter.

   After a job parameter is defined, it can be referenced by a job node.


   .. figure:: /_static/images/en-us_image_0000002270847218.png
      :alt: **Figure 4** Using a Job Parameter Configuration

      **Figure 4** Using a Job Parameter Configuration

.. _dataartsstudio_01_7524__section04082466318:

Script Parameter
----------------

-  Script parameters take effect in current script and it can be used in the following ways.

   -  For SQL scripts, you can directly enter parameters in the script editor (not supported for Flink SQL scripts). During job scheduling, you can assign values to parameters through node attributes, as shown in :ref:`2 <dataartsstudio_01_7524__li14638161911311>`.

   -  For Shell scripts, you can enter a parameter and an interactive parameter in the upper part of the editor to transfer the parameters.

   -  Python scripts support parameter transfer.

   -  For SQL scripts, you can directly enter parameters in the script editor (not supported for Flink SQL scripts). When executing a script independently, you can configure parameters in the lower part of the editor shown in :ref:`Figure 5 <dataartsstudio_01_7524__fig35061784103>`.

      .. _dataartsstudio_01_7524__fig35061784103:

      .. figure:: /_static/images/en-us_image_0000002305407093.png
         :alt: **Figure 5** Configuring script parameters when executing a script independently

         **Figure 5** Configuring script parameters when executing a script independently

#. Developing a Python Script During script development, the script expression must contain variables. For example, if the variable in the SQL statement is DATE, set this parameter to ${DATE} in the script. In the job parameter configuration, you can compile the statement expression of the script parameter Date in :ref:`2 <dataartsstudio_01_7524__li14638161911311>`.

   On the **script development** page, enter development statements in the editor, as shown in the following figure.

   .. code-block::

      INSERT INTO B FROM (SELECT * FROM A WHERE DATE = ${DATE})


   .. figure:: /_static/images/en-us_image_0000002270847230.png
      :alt: **Figure 6** Developing a script

      **Figure 6** Developing a script

   After the dws_030903 script is compiled, save and submit the latest version of the script.

#. .. _dataartsstudio_01_7524__li14638161911311:

   Develop batch jobs. When developing a job, you need to configure node attribute parameters.

   In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Job**.


   .. figure:: /_static/images/en-us_image_0000002270847222.png
      :alt: **Figure 7** Configuring script parameters when the script is executed by job scheduling

      **Figure 7** Configuring script parameters when the script is executed by job scheduling

   .. note::

      -  If the associated SQL script uses a parameter, the parameter name is displayed (**DATA** for example). Set the parameter value in the text box next to the parameter name. The parameter value can be :ref:`an EL expression <dataartsstudio_01_0494>`.
      -  If the associated SQL script or script parameters change, you can click |image1| to synchronize the changes or click |image2| to edit the changes.
      -  All nodes involving scripts, such as SQL scripts, shell scripts, and Python scripts, can use this method to reference script variables.

Simple Variable Set
-------------------

The simple variable set provides a series of customized variables. Customized parameters are automatically replaced with specific values based on the service date, plan time, and parameter value format of task scheduling. In this way, parameters can be dynamically replaced during task scheduling. For details about the simple variable set, see :ref:`Simple Variable Set <dataartsstudio_01_0556>`.

.. |image1| image:: /_static/images/en-us_image_0000002270847198.png
.. |image2| image:: /_static/images/en-us_image_0000002305440177.png
