:original_name: dataartsstudio_01_1823.html

.. _dataartsstudio_01_1823:

Developing a Real-Time Processing Single-Task MRS Flink SQL Job
===============================================================

This section describes how to develop and configure a job.

For details about how to develop a real-time processing Flink SQL job in single-task mode, see sections :ref:`Developing an SQL Script <dataartsstudio_01_1823__section037832452814>`, :ref:`Configuring Job Parameters <dataartsstudio_01_1823__en-us_topic_0099797007_section754991272419>`, :ref:`Saving a Job <dataartsstudio_01_1823__section1462324142616>`, and :ref:`Templates <dataartsstudio_01_1823__section2246103584414>`.

Prerequisites
-------------

-  You have created a job by referring to :ref:`Creating a Job <dataartsstudio_01_0434>`.
-  You have locked the job. Otherwise, you must click **Lock** so that you can develop the job. A job you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0913>`.

.. _dataartsstudio_01_1823__section037832452814:

Developing an SQL Script
------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click the name of a single-task job to access the job development page.

#. On the right of the SQL editor, click **Basic Info** to configure basic information of the job. :ref:`Table 1 <dataartsstudio_01_1823__table44429421624>` provides the basic information about the single-task MRS Flink SQL job.

   .. _dataartsstudio_01_1823__table44429421624:

   .. table:: **Table 1** Basic job information

      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                           | Description                                                                                                                                                                                                                                                                                                   |
      +=====================================================+===============================================================================================================================================================================================================================================================================================================+
      | Owner                                               | An owner configured during job creation is automatically matched. This parameter value can be modified.                                                                                                                                                                                                       |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Executor                                            | This parameter is available when **Scheduling Identities** is set to **Yes**.                                                                                                                                                                                                                                 |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | User that executes the job. When you enter an executor, the job is executed by the executor. If the executor is left unspecified, the job is executed by the user who submitted the job for startup.                                                                                                          |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | .. note::                                                                                                                                                                                                                                                                                                     |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     |    You can configure execution users only after you apply for the whitelist membership. To enable it, contact customer service or technical support.                                                                                                                                                          |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Agency                                          | This parameter is available when **Scheduling Identities** is set to **Yes**.                                                                                                                                                                                                                                 |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | After an agency is configured, the job interacts with other services as an agency during job execution.                                                                                                                                                                                                       |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Priority                                            | Priority configured during job creation is automatically matched. This parameter value can be modified.                                                                                                                                                                                                       |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execution Timeout                                   | Timeout of the job instance. If this parameter is set to 0 or is not set, this parameter does not take effect. If the notification function is enabled for the job and the execution time of the job instance exceeds the preset value, the system sends a specified notification, and the job keeps running. |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exclude Waiting Time from Instance Timeout Duration | Whether to exclude the wait time from the instance execution timeout duration                                                                                                                                                                                                                                 |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | If you select this option, the time to wait before an instance starts running is excluded from the timeout duration. You can modify this setting in :ref:`Default Configuration > Exclude Waiting Time from Instance Timeout Duration <dataartsstudio_01_04501__section14959925164217>`.                      |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | If you do not select this option, the time to wait before an instance starts running is included in the timeout duration.                                                                                                                                                                                     |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Parameter                                    | Set the name and value of the parameter.                                                                                                                                                                                                                                                                      |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Tag                                             | Configure job tags to manage jobs by category.                                                                                                                                                                                                                                                                |
      |                                                     |                                                                                                                                                                                                                                                                                                               |
      |                                                     | Click **Add** to add a tag to the job. You can also select a tag configured in :ref:`Managing Job Tags <dataartsstudio_01_0532>`.                                                                                                                                                                             |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Description                                     | Description of the job                                                                                                                                                                                                                                                                                        |
      +-----------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Attributes of the real-time processing single-task MRS Flink SQL job

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Property                          | Description                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================+
      | **Flink SQL properties**          |                                                                                                                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Flink Job Name                    | Enter the Flink job name.                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                           |
      |                                   | The name is automatically generated in *Workspace-Job name* format.                                                                                                                                       |
      |                                   |                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    It can contain only letters, digits, hyphens (-), and underscores. A maximum of 64 characters are allowed, and Chinese characters are not allowed.                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Cluster                       | Select an MRS cluster.                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    Currently, jobs with a single Flink SQL node support MRS 3.2.0-LTS.1 and later versions.                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Program Parameter                 | Set the job running parameters. This parameter is displayed only after an MRS cluster is selected.                                                                                                        |
      |                                   |                                                                                                                                                                                                           |
      |                                   | (Optional) Configure optimization parameters such as threads, memory, and vCPUs for the job to optimize resource usage and improve job execution performance.                                             |
      |                                   |                                                                                                                                                                                                           |
      |                                   | .. caution::                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    CAUTION:                                                                                                                                                                                               |
      |                                   |    You can query historical checkpoints and select a specified checkpoint to start a real-time Flink SQL job. To make a Flink checkpoint take effect, configure the following two parameters:             |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    .. _dataartsstudio_01_1823__fig107281810162613:                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    **Figure 1** Configuring program parameters                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    -  Checkpoint interval:                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       **-yD: execution.checkpointing.interval=1000**                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    -  Number of reserved checkpoints:                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       **-yD: state.checkpoints.num-retained=10**                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       When querying the checkpoint list, enter parameter **-s** and click the parameter value text box. The parameter value will be automatically displayed.                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    This parameter is mandatory if the cluster version is MRS 1.8.7 or later than MRS 2.0.1.                                                                                                               |
      |                                   |                                                                                                                                                                                                           |
      |                                   | Click **Select Template** and select a parameter template. You can also select multiple templates. For details about how to create templates, see :ref:`Configuring a Template <dataartsstudio_01_1282>`. |
      |                                   |                                                                                                                                                                                                           |
      |                                   | For details about the parameters of MRS Flink jobs, see **Managing an Existing Cluster** > **Job Management** > **Running a Flink Job** in *MapReduce Service (MRS) User Guide*.                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Flink Job Parameter               | Set the parameters for the Flink job.                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                           |
      |                                   | Variables required for executing the Flink job. These variables are specified by the functions in the Hive script. Multiple parameters are separated by spaces.                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MRS Resource Queue                | Select a created MRS resource queue.                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                           |
      |                                   | This parameter is mandatory if :ref:`Whether MRS Resource Queue Is Mandatory <dataartsstudio_01_04501__section146531751579>` is set to **Yes**.                                                           |
      |                                   |                                                                                                                                                                                                           |
      |                                   | Select a queue you configured in the queue permissions of DataArts Security. If you set multiple resource queues for this node, the resource queue you select here has the highest priority.              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rerun Policy                      | -  Rerun from the previous checkpoint                                                                                                                                                                     |
      |                                   | -  Rerun the job                                                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Input Data Path                   | Set the input data path. You can select an HDFS or OBS path.                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Output Data Path                  | Set the output data path. You can select an HDFS or OBS path.                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Advanced Settings

      +---------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                       | Mandatory             | Description                                                                                                                                                  |
      +=================================+=======================+==============================================================================================================================================================+
      | Job Status Polling Interval (s) | Yes                   | Set the interval at which the system checks whether the job is complete. The interval can range from 30s to 60s, or 120s, 180s, 240s, or 300s.               |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       | During job execution, the system checks the job status at the configured interval.                                                                           |
      +---------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Wait Time               | Yes                   | Set the timeout interval for the job. If the job is not complete within the timeout interval and retry is enabled, the job will be executed again.           |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       | .. note::                                                                                                                                                    |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |    If the job is in starting state and fails to start, it will fail upon timeout.                                                                            |
      +---------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Retry upon Failure              | Yes                   | Whether to re-execute the job if it fails                                                                                                                    |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       | -  **Yes**: The job will be re-executed if it fails. Configure the following parameters:                                                                     |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |    -  Retry upon Timeout                                                                                                                                     |
      |                                 |                       |    -  **Maximum Retries**                                                                                                                                    |
      |                                 |                       |    -  **Retry Interval (seconds)**                                                                                                                           |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       | -  **No**: The job will not be re-executed if it fails. This is the default setting.                                                                         |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |    .. note::                                                                                                                                                 |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |       If retry is configured for a job node and the timeout duration is configured, the system allows you to retry a node when the node execution times out. |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |       If a node is not re-executed when it fails upon timeout, you can go to the **Default Configuration** page to modify this policy.                       |
      |                                 |                       |                                                                                                                                                              |
      |                                 |                       |       **Retry upon Timeout** is displayed only when **Retry upon Failure** is set to **Yes**.                                                                |
      +---------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Enter one or more SQL statements in the SQL editor.

   .. note::

      -  SQL statements are separated by semicolons (**;**). If semicolons are used in other places but not used to separate SQL statements, escape them with backslashes (**\\**). The following is an example:

         .. code-block::

            select 1;
            select * from a where b="dsfa\;";  --example 1\;example 2.

      -  The script cannot be larger than 16 MB.

      -  The system date obtained by using an SQL statement is different from that obtained by using the database tool. The query result is stored in the database in the YYYY-MM-DD format, but the query result displayed on the page is in the converted format.

      -  You can click **Check Syntax** to check the syntax of Flink SQL jobs. Above the editor, click **Check Syntax** to verify the semantics of SQL statements. After the check is complete, you can view the check result in the lower part of the page.

      -  When viewing the script execution result, you can double-click a field in any row to view the result details. You can copy the field name.

      -  You can control display of the script execution history by setting **Script Execution History** in **Default Configuration** to **Myself** or **All users**.

   To facilitate script development, DataArts Factory provides the following capabilities:

   -  The script editor supports the following shortcut keys, which improve the script development efficiency:

      -  **F8**: Run a script.
      -  **F9**: Stop running a script.
      -  **Ctrl** + **/**: Comment out or uncomment the line or code block where the cursor resides.
      -  **Ctrl** + **Z**: Undo an action.
      -  **Ctrl** + **F**: Search for information.
      -  **Ctrl** + **Shift** + **R**: Replace
      -  **Ctrl** + **X**: Cut
      -  **Ctrl** + **S**: Save a script.
      -  **Alt** + mouse dragging: Select columns to edit a block.
      -  **Ctrl** + mouse click: Select multiple lines to edit or indent them together.
      -  **Ctrl** + **→** (or **←**): Move the cursor rightwards (or leftwards) by word.
      -  **Ctrl** + **Home** or **Ctrl** + **End**: Navigate to the beginning or end of the current file.
      -  **Home** or **End**: Navigate to the beginning or end of the current line.
      -  **Ctrl** + **Shift** + **L**: Double-click all the same character strings and add cursors to them to implement batch modification.
      -  **Ctrl** + **D**: Delete a line.
      -  **Shift** + **Ctrl** + **U**: Unlock a script.
      -  **Ctrl** + **Alt** + **K**: Select the word where the cursor resides.
      -  **Ctrl** + **B**: Format
      -  **Ctrl** + **Shift** + **Z**: Redo
      -  **Ctrl** + **Enter**: Execute the selected line or content.
      -  **Ctrl** + **Alt** + **F**: Flag
      -  **Ctrl** + **Shift** + **K**: Search for the previous one.
      -  **Ctrl** + **K**: Search for the next one.
      -  **Ctrl** + **Backspace**: Delete the word to the left of the cursor.
      -  **Ctrl** + **Delete**: Delete the word to the right of the cursor.
      -  **Alt** + **Backspace**: Delete all content from the beginning of the line to the cursor.
      -  **Alt** + **Delete**: Delete all content from the cursor to the end of the line.
      -  **Alt** + **Shift**\ ``-``\ **Left**: Select all content from the beginning of the line to the cursor.
      -  **Alt** + **Shift**\ ``-``\ **Right**: Select all content from the cursor to the end of the line.

   -  Script parameters

      Enter script parameters in the SQL statement and click **Parameter Setup** in the right pane of the editor and then click **Update from Script**. You can also directly configure parameters and constants for the job script.

      In the following script example, *str1* indicates the parameter name. It can contain only letters, digits, hyphens (-), underscores (_), greater-than signs (>), and less-than signs (<), and can contain a maximum of 16 characters. The parameter name must be unique.

      .. code-block::

         select ${str1} from data;

#. (Optional) In the upper part of the editor, click **Format** to format SQL statements.

#. Above the editor, click **Save** to save the job and submit it.

.. _dataartsstudio_01_1823__en-us_topic_0099797007_section754991272419:

Configuring Job Parameters
--------------------------

Click **Parameters** on the right of the editor and set the parameters described in :ref:`Table 4 <dataartsstudio_01_1823__en-us_topic_0099797007_table20701161192718>`.

.. _dataartsstudio_01_1823__en-us_topic_0099797007_table20701161192718:

.. table:: **Table 4** Job parameters

   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                                     | Description                                                                                                                                                                                     |
   +==============================================================================+=================================================================================================================================================================================================+
   | **Variables**                                                                |                                                                                                                                                                                                 |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                                                                          | Click **Add** and enter the variable parameter name and parameter value in the text boxes.                                                                                                      |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | -  Parameter name                                                                                                                                                                               |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              |    Only letters, numbers, periods (.), hyphens (-), and underscores (_) are allowed.                                                                                                            |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | -  Parameter value                                                                                                                                                                              |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              |    -  The string type of parameter value is a character string, for example, **str1**.                                                                                                          |
   |                                                                              |    -  The numeric type of parameter value is a number or operation expression.                                                                                                                  |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | After the parameter is configured, it is referenced in the format of **$**\ {*parameter name*} in the job.                                                                                      |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Edit Parameter Expression                                                    | Click |image1| next to the parameter value text box. In the displayed dialog box, edit the parameter expression. For more expressions, see :ref:`Expression Overview <dataartsstudio_01_0494>`. |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                                                                       | Change the parameter name or value in the corresponding text boxes.                                                                                                                             |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mask                                                                         | If the parameter value is a key, click |image2| to mask the value for security purposes.                                                                                                        |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                                                                       | Click |image3| next to the parameter name and value text boxes to delete the job parameter.                                                                                                     |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Constant Parameter**                                                       |                                                                                                                                                                                                 |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add                                                                          | Click **Add** and enter the constant parameter name and parameter value in the text boxes.                                                                                                      |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | -  Parameter name                                                                                                                                                                               |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              |    Only letters, numbers, periods (.), hyphens (-), and underscores (_) are allowed.                                                                                                            |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | -  Parameter value                                                                                                                                                                              |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              |    -  The string type of parameter value is a character string, for example, **str1**.                                                                                                          |
   |                                                                              |    -  The numeric type of parameter value is a number or operation expression.                                                                                                                  |
   |                                                                              |                                                                                                                                                                                                 |
   |                                                                              | After the parameter is configured, it is referenced in the format of **$**\ {*parameter name*} in the job.                                                                                      |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Edit Parameter Expression                                                    | Click |image4| next to the parameter value text box. In the displayed dialog box, edit the parameter expression. For more expressions, see :ref:`Expression Overview <dataartsstudio_01_0494>`. |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                                                                       | Modify the parameter name and parameter value in text boxes and save the modifications.                                                                                                         |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                                                                       | Click |image5| next to the parameter name and value text boxes to delete the job parameter.                                                                                                     |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Workspace Environment Variables**                                          |                                                                                                                                                                                                 |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | View the variables and constants that have been configured in the workspace. |                                                                                                                                                                                                 |
   +------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Click the **Parameter Preview** tab and configure the parameters listed in :ref:`Table 5 <dataartsstudio_01_1823__table1036167182419>`.

.. _dataartsstudio_01_1823__table1036167182419:

.. table:: **Table 5** Job parameter preview

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                          | Description                                                                                                                                                      |
   +===================================+==================================================================================================================================================================+
   | Current Time                      | This parameter is displayed only when **Scheduling Type** is set to **Run once**. The default value is the current time.                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Event Triggering Time             | This parameter is displayed only when **Scheduling Type** is set to **Event-based**. The default value is the time when an event is triggered.                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduling Period                 | This parameter is displayed only when **Scheduling Type** is set to **Run periodically**. The default value is the scheduling period.                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Start Time                        | This parameter is displayed only when **Scheduling Type** is set to **Run periodically**. The value is the configured job execution time.                        |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Start Time                        | This parameter is displayed only when **Scheduling Type** is set to **Run periodically**. The value is the time when the periodic job scheduling starts.         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subsequent Instances              | Number of job instances scheduled.                                                                                                                               |
   |                                   |                                                                                                                                                                  |
   |                                   | -  The default value is **1** when **Scheduling Type** is set to **Run once**.                                                                                   |
   |                                   |                                                                                                                                                                  |
   |                                   | -  The default value is **1** when **Scheduling Type** is set to **Event-based**.                                                                                |
   |                                   |                                                                                                                                                                  |
   |                                   | -  When **Scheduling Type** is set to **Run periodically**:                                                                                                      |
   |                                   |                                                                                                                                                                  |
   |                                   |    If the number of instances exceeds 10, a maximum of 10 instances can be displayed, and the system displays message "A maximum of 10 instances are supported." |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   In **Parameter Preview**, if a job parameter has a syntax error, the system displays a message.

   If a parameter depends on the data generated during job execution, such data cannot be simulated and displayed in **Parameter Preview**.

.. _dataartsstudio_01_1823__section1462324142616:

Saving a Job
------------

After configuring the job, perform the following operations:

#. Click **Start** to execute the job. When viewing the script execution result, you can double-click a field in any row to view the result details. You can copy the field name.

   .. note::

      A maximum of 1,000 records can be displayed in the execution result. The size of the execution result cannot exceed 3 MB. If the size exceeds 3 MB, the result will be truncated.

#. After the job is executed, click |image6| to save the job configuration.

   After the job is saved, a version is automatically generated and displayed in **Versions**. The version can be rolled back. If you save a job multiple times within a minute, only one version is recorded. If the intermediate data is important, you can click **Save new version** to save and add a version.

.. _dataartsstudio_01_1823__section2246103584414:

Templates
---------

When developing a real-time processing, single-task Flink SQL job, you can use a public script template. For details about how to create a template, see :ref:`Configuring a Template <dataartsstudio_01_1282>`. For details about how to use a script template, see :ref:`Using Script Templates and Parameter Templates <dataartsstudio_01_1582>`.

.. |image1| image:: /_static/images/en-us_image_0000002234237164.png
.. |image2| image:: /_static/images/en-us_image_0000002234077316.png
.. |image3| image:: /_static/images/en-us_image_0000002269116521.png
.. |image4| image:: /_static/images/en-us_image_0000002269116529.png
.. |image5| image:: /_static/images/en-us_image_0000002269196601.png
.. |image6| image:: /_static/images/en-us_image_0000002234079692.png
