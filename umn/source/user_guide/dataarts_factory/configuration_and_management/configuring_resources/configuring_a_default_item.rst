:original_name: dataartsstudio_01_04501.html

.. _dataartsstudio_01_04501:

Configuring a Default Item
==========================

This section describes how to configure a default item. You can perform the operations in this section only if you have the permissions of **DARTS** **Administrator** or **Tenant Administrator**.

Scenario
--------

If a parameter is invoked by multiple jobs, you can use this parameter as the default configuration item. In this way, you do not need to set this parameter for each job.

.. table:: **Table 1** Configuration items

   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuration Item                                                                                           | Affected Module                  | Main Usage                                                                                                                                                                                                                                                                    |
   +==============================================================================================================+==================================+===============================================================================================================================================================================================================================================================================+
   | :ref:`Periodic Scheduling <dataartsstudio_01_04501__section758614222215>`                                    | Job scheduling                   | -  Default action on the **current job** when the job it depends on fails                                                                                                                                                                                                     |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Multi-IF Policy <dataartsstudio_01_04501__section1105620164415>`                                       | Job scheduling                   | Policy for executing nodes with multiple IF conditions                                                                                                                                                                                                                        |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Hard and Soft Lock Policy <dataartsstudio_01_04501__section140018355442>`                              | Script/Job development           | Policy for grabbing the lock of a job or script                                                                                                                                                                                                                               |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Script Variable Definition <dataartsstudio_01_04501__section310213518565>`                             | Script development               | Format definition of script variables. Two formats are available: ${} and ${dlf.}.                                                                                                                                                                                            |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Data Export Policy <dataartsstudio_01_04501__section1970845152011>`                                    | Script/Job development           | Policy for downloading or dumping the SQL execution result                                                                                                                                                                                                                    |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | -  All users                                                                                                                                                                                                                                                                  |
   |                                                                                                              |                                  | -  No user                                                                                                                                                                                                                                                                    |
   |                                                                                                              |                                  | -  Only workspace administrator                                                                                                                                                                                                                                               |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Disable Auto Node Name Change <dataartsstudio_01_04501__section67661828112219>`                        | Job Development                  | When a node in a DataArts Studio job is associated with a script or a job of another service, the node name does not change accordingly.                                                                                                                                      |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Use Simple Variable Set <dataartsstudio_01_04501__section12475339019>`                                 | Job development                  | A simple variable set provides a series of custom variables that automatically replace parameters during job scheduling.                                                                                                                                                      |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Notification Policy for Jobs in Failure Ignored Status <dataartsstudio_01_04501__section201662581464>` | O&M and scheduling               | Notification type for jobs whose status is failure ignored                                                                                                                                                                                                                    |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Retry Node upon Timeout <dataartsstudio_01_04501__section687113915618>`                                | Job execution                    | Whether a node will be re-executed if it fails upon timeout                                                                                                                                                                                                                   |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Exclude Waiting Time from Instance Timeout Duration <dataartsstudio_01_04501__section14959925164217>`  | Job execution                    | If you select **Yes**, the waiting time before an instance starts running is excluded from the instance timeout duration.                                                                                                                                                     |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Rules for Splitting MRS JAR Package Parameters <dataartsstudio_01_04501__section105211772476>`         | Job development                  | Rules for splitting string parameters (parameters enclosed by "") in the JAR packages of MRS MapReduce and MRS Spark operators                                                                                                                                                |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Synchronization of Job Version by Waiting Instance <dataartsstudio_01_04501__section2986254123414>`    | O&M and scheduling               | Whether a waiting instance synchronizes the latest job version when it runs                                                                                                                                                                                                   |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Execution Mode for Hive SQL and Spark SQL Statements <dataartsstudio_01_04501__section1545212478426>`  | Script/Job development           | -  **In OBS**: The OBS path is returned to MRS.                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | -  **In the request message body**: The script content is returned to MRS.                                                                                                                                                                                                    |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Whether MRS Resource Queue Is Mandatory <dataartsstudio_01_04501__section146531751579>`                | Job development                  | If you select **Yes**, parameter **MRS Resource Queue** is mandatory.                                                                                                                                                                                                         |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`PatchData Job Priority <dataartsstudio_01_04501__section1149418391843>`                                | O&M - PatchData                  | Priority of a PatchData job. If system resources are insufficient, computing resources are preferentially allocated to jobs with higher priorities. A larger value indicates a higher priority. Priorities can be set only for DLI SQL operators.                             |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Historical Job Instance Cancellation Policy <dataartsstudio_01_04501__section10606125173916>`          | O&M and scheduling               | Days to wait before job instances are canceled. If the wait time of a job instance exceeds the value of this parameter, the instance will be canceled. The minimum value is 2, that is, a job instance can be canceled only after two days. The default value is **60** days. |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Historical Job Instance Alarm Policy <dataartsstudio_01_04501__section166989301817>`                   | O&M and scheduling               | Days in which alarms can be reported for job instances.                                                                                                                                                                                                                       |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | The default value is **7**, that is, alarms can be reported for the job instances created within the last seven days, but not for those created before that.                                                                                                                  |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Default Retry Policy upon Job Operator Failure <dataartsstudio_01_04501__section1048217439191>`        | O&M and scheduling               | Default policy for retrying a failed job operator                                                                                                                                                                                                                             |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Generate Alarm Upon Job Retry Failure <dataartsstudio_01_04501__section132101959182118>`               | O&M and scheduling               | If you select **All jobs**, **Real-time jobs**, or **Batch jobs**, an alarm is generated each time a job fails to be retried.                                                                                                                                                 |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | If you select **Disable**, an alarm is generated only when the maximum number of retries has been reached for the job.                                                                                                                                                        |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Automatic Script Name Transfer During Job Execution <dataartsstudio_01_04501__section5197124710613>`   | Job development (job execution)  | If this function is enabled, set mapreduce.job.name=Script name of the Hive SQL script is automatically transferred to MRS during job execution in the current workspace.                                                                                                     |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Job Dependency Rule <dataartsstudio_01_04501__section45021415123915>`                                  | Job scheduling                   | Jobs can be depended on by jobs in other workspaces (requires the permission to query the job list in the workspace). All default roles in the workspace have this permission. Custom roles must have the job query permission in DataArts Factory.                           |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Script Execution History <dataartsstudio_01_04501__section7536359192017>`                              | Script/Job development           | Which script execution results are displayed                                                                                                                                                                                                                                  |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | -  **Myself**: The script execution history for only myself is displayed.                                                                                                                                                                                                     |
   |                                                                                                              |                                  | -  **All users**: The script execution history for all users is displayed.                                                                                                                                                                                                    |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Identity for Job Tests <dataartsstudio_01_04501__section83901219181110>`                               | Job development (job test)       | Identity for testing jobs.                                                                                                                                                                                                                                                    |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | -  **Public agency or IAM account**: A public agency or IAM account is used to execute jobs.                                                                                                                                                                                  |
   |                                                                                                              |                                  | -  **Personal account**: The user who clicks **Test** is used to execute jobs.                                                                                                                                                                                                |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`SparkSqlJob/Script Default Template Configuration <dataartsstudio_01_04501__section977293342312>`      | Spark SQL script/job development | Whether any parameters can be set for Spark SQL jobs and scripts                                                                                                                                                                                                              |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`HiveSqlJob/Script Default Template Configuration <dataartsstudio_01_04501__section20499113582315>`     | Spark SQL script/job development | Whether any parameters can be set for Hive SQL jobs and scripts                                                                                                                                                                                                               |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Job/Script Change Management <dataartsstudio_01_04501__section375164516215>`                           | Job/Script import and export     | Whether to enable job/script change management for the workspace                                                                                                                                                                                                              |
   |                                                                                                              |                                  |                                                                                                                                                                                                                                                                               |
   |                                                                                                              |                                  | -  **Yes**: Events are recorded for job and script changes. All the changed jobs and scripts can be incrementally exported and imported by time.                                                                                                                              |
   |                                                                                                              |                                  | -  **No**: No events are recorded for job and script changes. Only selected jobs and scripts can be exported and imported.                                                                                                                                                    |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Log Open Mode <dataartsstudio_01_04501__section108941170226>`                                          | Viewing logs                     | Whether to open logs on a new tab or in a pop-up window                                                                                                                                                                                                                       |
   +--------------------------------------------------------------------------------------------------------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_04501__section758614222215:

Configuring Periodic Scheduling
-------------------------------

-  To configure the default action on the **current job** when the job it depends on fails, perform the following operations:

   #. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
   #. Choose **Default Configuration**.

      .. note::

         Three options are available. The default value is **Terminate**.

         -  **Suspend**: The current job is suspended.
         -  **Continue**: The current job continues to be executed.
         -  **Cancel**: The current job is canceled.

   #. Click **Save** to save the settings. This parameter takes effect only for new jobs.

.. _dataartsstudio_01_04501__section1105620164415:

Configuring the Multi-IF Policy
-------------------------------

To configure the policy for executing nodes with multiple IF conditions, perform the following operations:

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.

   .. note::

      The following two options are available:

      -  **OR**: Nodes are executed if an IF condition is met.
      -  **AND**: Nodes are executed if all IF conditions are met.

      For details, see :ref:`Configuring the Policy for Executing a Node with Multiple IF Statements <dataartsstudio_01_0583__section1626375417376>`.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section140018355442:

Configuring the Hard and Soft Lock Policy
-----------------------------------------

The policy determines how you can grab the lock of a job or script. If you use a soft lock, you can grab the lock of a job or script regardless of whether you have the lock. If you use a hard lock, you can only unlock or grab the lock of a job or script for which you have the lock. Operations such as publish, execution, and scheduling are not restricted by locks.

You can configure the hard/soft policy based on your needs.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.

   .. note::

      The default policy is **Soft Lock**.

      -  **Soft lock**: You can lock or unlock jobs or scripts, regardless of whether they are locked by others.
      -  **Hard Lock**: You can lock jobs or scripts only after they have been unlocked by other users. The space administrator and the DARTS Administrator user can lock and unlock jobs or scripts without any limitations.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section310213518565:

Configuring Script Variables
----------------------------

Variables of an SQL script can be in ${} or ${dlf.} format. You can configure either type as needed. The configured variable format applies to SQL scripts, SQL statements in jobs, single-node jobs, and environment variables.

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Click **Default Configuration** and set **Script Variable Definition**.

   .. note::

      The default variable format is **${}**.

      -  **${}**: Identify the definition of the ${} format in the script and parse the field as the variable name. For example, variable name *xxx* is identified from **${**\ *xxx*\ **}**.
      -  **${dlf.}**: Identify the definition of the ${dlf.} format in the script and parse the **dlf.** field as the variable name. Other ${} format definitions are not recognized as variables. For example, variable name **dlf.**\ *xxx* is identified from **${dlf.**\ *xxx*\ **}**.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section1970845152011:

Configuring a Data Export Policy
--------------------------------

By default, all users can download and dump the execution results of SQL scripts. If you do not want all users to have this permission, perform the following steps to configure a data export policy:

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and set **Data Export Policy**.

   .. note::

      The default data export policy is **All User Can**.

      -  **All User Can**: All users can download and dump SQL execution results.
      -  **All User Cannot**: No user can download or dump SQL execution results.
      -  **Only Workspace Manager Can**: Only workspace administrators can download and dump SQL execution results.

#. Click **Save**.

.. _dataartsstudio_01_04501__section67661828112219:

Disabling Auto Node Name Change
-------------------------------

On the **Develop Job** page, when you select a script for a node or associate a node with the function of another cloud service, the node name will be automatically changed to the script name or function name. You can disable this function.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**. Find **Disable Auto Node Name Change** and select job nodes.

   .. note::

      -  You can disable automatic name change for the following nodes: CDM Job, DLI SQL, DWS SQL, MRS Spark SQL, MRS Hive SQL, MRS Presto SQL, MRS HetuEngine, MRS ClickHouse, MRS Impala SQL, Shell, RDS SQL, Subjob, For Each, Doris SQL, or Python.
      -  No job nodes are selected by default.
      -  Names of the selected nodes will not be automatically changed when a script is selected or a function is associated with them.

#. Click **Save**.

.. _dataartsstudio_01_04501__section12475339019:

Use Simple Variable Set
-----------------------

The simple variable set provides a series of customized variables to dynamically replace parameters during task scheduling.

#. In the navigation pane on the **Data Development** page, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and set **Use Simple Variable Set**.

   .. note::

      -  **Yes**: Simple variable sets are supported. A series of customized variables provided by the simple variable set. Customized parameters are automatically replaced with specific values based on the service date, plan time, and parameter value format of task scheduling. In this way, parameters can be dynamically replaced during task scheduling.
      -  **No**: Simple variable sets are not supported.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section201662581464:

Notification Policy for Jobs in Failure Ignored Status
------------------------------------------------------

To configure the notification type for jobs whose status is failure ignored, perform the following steps:

#. In the navigation pane on the **Data Development** page, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and set **Notification Policy for Jobs in Failure Ignored Status**.
#. Select a notification type for jobs whose status is failure ignored.

   .. note::

      -  Jobs whose status is failure ignored are those whose **Policy for Handling Subsequent Nodes If the Current Node Fails** is set to **Go to the next node**. By default, such jobs are deemed successful by the system.

      -  You can configure either of the following notification types for such jobs:

         **Abnormal**

         **Successful** (default)

#. Click **Save**.

.. _dataartsstudio_01_04501__section687113915618:

Setting Retry Node upon Timeout
-------------------------------

You can set this parameter to specify whether a node will be re-executed if it fails upon timeout.

#. In the navigation pane on the **Data Development** page, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Retry Node upon Timeout**.

   .. note::

      -  **No**: A node will not be re-executed if it fails upon timeout.
      -  **Yes**: A node will be re-executed if it fails upon timeout.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section14959925164217:

Exclude Waiting Time from Instance Timeout Duration
---------------------------------------------------

You can specify whether to exclude waiting time from instance timeout duration.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration** and set **Exclude Waiting Time from Instance Timeout Duration**.
#. Select **Yes** or **No**.

   .. note::

      **Yes**: The waiting time before an instance starts running is excluded from the instance timeout duration.

      **No**: The waiting time before an instance starts running is included in the instance timeout duration.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section105211772476:

Rules for Splitting MRS JAR Package Parameters
----------------------------------------------

You can set the rule for splitting the string parameters (enclosed by "") in the JAR package parameters of MRS MapReduce and MRS Spark operators.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration** and set **Rules for Splitting MRS JAR Package Parameters**.
#. Select a rule.

   .. note::

      **Split String Arguments by Space**: For example, **"select \* from table"** is split into four parameters by space: **select**, **\***, **from**, and **table**.

      **Do not split string arguments**: For example, **"select \* from table"** is regarded as one parameter and is not split.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section2986254123414:

Synchronization of Job Version by Waiting Instance
--------------------------------------------------

You can specify whether a waiting instance can synchronize the latest job version.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration** and set **Synchronization of Job Version by Waiting Instance**.
#. Select **Yes** or **No**.

   .. note::

      **Yes**: The waiting instance uses the latest job version.

      **No**: The waiting instance still uses the existing job version.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section1545212478426:

Execution Mode for Hive SQL and Spark SQL Statements
----------------------------------------------------

When Hive SQL and Spark SQL statements are executed, DataArts Studio can place SQL statements in OBS or in the request body.

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Execution Mode for Hive SQL and Spark SQL Statements**.

   .. note::

      **In OBS**: Hive SQL and Spark SQL statements are put in OBS, and the OBS is returned to MRS.

      **In the request message body**: Hive SQL and Spark SQL statements are put in the request message body, and the script content is returned to MRS.

#. Click **Save** to save the settings.

   .. note::

      This configuration supports Hive SQL and Spark SQL scripts, and pipeline and single-task jobs.

.. _dataartsstudio_01_04501__section146531751579:

Whether MRS Resource Queue Is Mandatory
---------------------------------------

You can set whether the **MRS resource queue** is mandatory for configuring an MRS-related job.

.. note::

   This function is available for the following scenarios:

   -  Pipeline job operators: MRS Spark SQL, MRS Flink Job, MRS Hive SQL, MRS Spark Python, and MRS Spark
   -  Real-time processing jobs: Flink Jar and Flink SQL
   -  Batch processing single-task jobs: Spark SQL and Hive SQL
   -  Job import (including the job types listed above)

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Whether MRS Resource Queue Is Mandatory**.

   .. note::

      **Yes**: The **MRS Resource Queue** parameter is mandatory.

      **No**: The **MRS Resource Queue** parameter is not mandatory.

      As shown in the following figure, there are no red asterisks (``*``) before **MRS Resource Queue**, indicating that this parameter is not mandatory.


      .. figure:: /_static/images/en-us_image_0000002269124893.png
         :alt: **Figure 1** Setting MRS Resource Queue

         **Figure 1** Setting MRS Resource Queue

#. Click **Save**.

.. _dataartsstudio_01_04501__section1149418391843:

Setting PatchData Priority
--------------------------

You can set the priority of a PatchData job. When system resources are insufficient, computing resources are preferentially allocated to jobs with higher priorities. A larger number indicates a higher priority. Currently, only the priorities of DLI SQL operators can be set.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and set **PatchData Job Priority**.
#. Set the patch data priority policy.
#. Click **Save** to save the settings.

   .. note::

      The mapping between the **PatchData Job Priority** and **spark.sql.dli.job.priority** of DLI is as follows:

      If **PatchData Job Priority** is set to **1**, **spark.sql.dli.job.priority** of DLI is **1**.

      If **PatchData Job Priority** is set to **2**, **spark.sql.dli.job.priority** of DLI is **3**.

      If **PatchData Job Priority** is set to **3**, **spark.sql.dli.job.priority** of DLI is **5**.

      If **PatchData Job Priority** is set to **4**, **spark.sql.dli.job.priority** of DLI is **8**.

      If **PatchData Job Priority** is set to **5**, **spark.sql.dli.job.priority** of DLI is **10**.

.. _dataartsstudio_01_04501__section10606125173916:

Historical Job Instance Cancellation Policy
-------------------------------------------

You can set the number of retention days for waiting job instances. If the waiting time of a job instance exceeds the configured retention days, the job instance is canceled. The minimum number of retention days is 2, that is, a job instance which is not executed can be canceled after at least two days. The default number of retention days is 60.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set the number of retention days for waiting job instances.
#. Click **Save** to save the settings.

Send Alarm Upon Instance Cancellation If you select **Yes** for this parameter and configure a cancellation notification for a job, an alarm notification will be sent when a historical job instance is canceled upon timeout. If you select **No**, no alarm notification will be sent.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Send Alarm Upon Instance Cancellation**.
#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section166989301817:

Historical Job Instance Alarm Policy
------------------------------------

You can set the number of days during which alarms can be generated for monitored job instances. The default value is seven days. Alarms cannot be sent for job instances beyond the seven-day period.

For example, if you set the value of this parameter to **2**, alarms can be generated for the job instances of yesterday and today, but cannot be generated for the job instances of the day before yesterday and of an earlier time even if the triggering conditions are met.

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and locate **Historical Job Instance Alarm Policy**.
#. Set the number of days during which alarms can be generated for monitored job instances.

   .. note::

      The default value is **7**. Set a value from 1 to 270.

      After you set this parameter, alarms are generated only for the job instances which are created after this parameter is set and not for historical instances.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section1048217439191:

Default Retry Policy upon Job Operator Failure
----------------------------------------------

This policy takes effect only for new job operators in the current workspace. The default policy for the operators in historical jobs is not affected. The default value is **No**.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Default Retry Policy upon Job Operator Failure**.

   .. note::

      If this parameter is set to **Yes**, new job operators can be retried once, and the retry interval is 120 seconds by default.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section132101959182118:

Generate Alarm Upon Job Retry Failure
-------------------------------------

If you enable this function, an alarm is generated each time a job fails to be retried.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Generate Alarm Upon Job Retry Failure**.

   .. note::

      -  If you select **All jobs**, **Real-time jobs**, or **Batch jobs**, an alarm is generated each time a job fails to be retried.
      -  If you select **Disable**, an alarm is generated only when the maximum number of retries has been reached for the job.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section5197124710613:

Automatic Script Name Transfer During Job Execution
---------------------------------------------------

If this function is enabled, **set mapreduce.job.name="Script name"** of the Hive SQL script is automatically transferred to MRS during job execution in the current workspace.

.. note::

   This function takes effect only if the preceding parameter value has not been set for the script. If the parameter value has been set for the script, the value set is preferentially read and transferred to MRS. This function is unavailable for MRS clusters in security mode. To enable this function for such clusters, set them to non-security mode.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.
#. Set **Automatic Script Name Transfer During Job Execution**.

   .. note::

      -  **Yes**: The system automatically transfers the Hive SQL script name to MRS during job execution.
      -  No: The system does not automatically transfer the Hive SQL script name to MRS during job execution.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section45021415123915:

Job Dependency Rule
-------------------

Jobs can be depended on by jobs in other workspaces (requires the permission to query the job list in the workspace). All default roles in the workspace have this permission. Custom roles must have the job query permission in DataArts Factory.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Configure **Job Dependency Rule**.

   .. note::

      -  **Jobs cannot be depended on by jobs in other workspaces**: Jobs in this workspace cannot be depended on by jobs in other workspaces.
      -  **Jobs can be depended on by jobs in other workspaces**: Jobs in this workspace can be depended on by jobs in other workspaces, without requiring the permissions of this workspace.
      -  **Jobs can be depended on by jobs in other workspaces (requires the permission to query the job list in the workspace)**: Jobs in this workspace can be depended on by jobs in other workspaces, requiring the permissions of this workspace. If you do not have the permissions, the system displays a message indicating that you do not have the permission to obtain the job list in workspace *xxx* when you configure job dependencies across workspaces.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section7536359192017:

Script Execution History
------------------------

You can set this parameter to control the permissions to view the script execution history.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Script Execution History**.

   .. note::

      -  **Myself**: The script execution history for only myself is displayed.
      -  **All users**: The script execution history for all users is displayed.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section83901219181110:

Identity for Job Tests
----------------------

After configuring this parameter, you can specify the identity used to test jobs.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration**.
#. Set **Identity for Job Tests**.

   .. note::

      -  **Public agency or IAM account**: A public agency or IAM account is used to execute jobs.

      -  **Personal account**: The user who clicks **Test** is used to execute jobs.

         If no workspace agency or IAM account is available, a personal account is used for job tests.

         If you are using a federated account, you must set this parameter to **Public agency or IAM account**.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section977293342312:

SparkSqlJob/Script Default Template Configuration
-------------------------------------------------

You can set this parameter to determine whether any parameters can be set to overwrite the default parameters of the template.

In the MRS API connection mode, default parameters can be configured for Spark SQL scripts. For proxy connections, this function is not supported.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.
#. Set **SparkSqlJob/Script Default Template Configuration**.

   .. note::

      -  **Yes**: You can set any parameters for jobs and scripts.

      -  **No**: You must select a template for jobs and scripts. If you select **No**, select a default parameter template that has been configured. For details about how to configure a template, see :ref:`Configuring a Template <dataartsstudio_01_1282>`.

         Then go to the **basic information page of the Spark SQL job or Spark SQL script page and click** |image1| **in the upper right corner** to view the configured default program parameters. The preset default parameters are unavailable and cannot be modified.

         You can also customize program parameters, which can replace the template parameters during the execution of Spark SQL jobs or scripts.

.. _dataartsstudio_01_04501__section20499113582315:

HiveSqlJob/Script Default Template Configuration
------------------------------------------------

You can set this parameter to determine whether parameters can be set to overwrite the default parameters of the template.

In the MRS API connection mode, default parameters can be configured for Hive SQL scripts. For proxy connections, this function is not supported.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.
#. Set **HiveSqlJob/Script Default Template Configuration**.

   .. note::

      -  **Yes**: You can set any parameters for jobs and scripts.

      -  **No**: You must select a template for jobs and scripts. If you select **No**, select a default parameter template that has been configured. For details about how to configure a template, see :ref:`Configuring a Template <dataartsstudio_01_1282>`.

         Then go to the **basic information page of the Hive SQL job or Hive SQL script page and click** |image2| **in the upper right corner** to view the configured default program parameters. The preset default parameters are unavailable and cannot be modified.

         You can also customize program parameters, which can replace the template parameters during the execution of Hive SQL jobs or scripts.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section375164516215:

Job/Script Change Management
----------------------------

If you enable this function, you can export job/script changes (addition, modification, and deletion) in a workspace to a .zip file, and import the file to another workspace.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Click **Default Configuration**.
#. Set **Job/Script Change Management**.

   .. note::

      -  **Yes**: Events are recorded for job and script changes. All the changed jobs and scripts can be incrementally exported and imported by time.
      -  **No**: No events are recorded for job and script changes. Only selected jobs and scripts can be exported and imported.

#. Click **Save** to save the settings.

   .. note::

      You can export and import jobs and scripts in the workspace only if you have set **Job/Script Change Management** to **Yes**.

.. _dataartsstudio_01_04501__section108941170226:

Log Open Mode
-------------

You can configure whether to open logs on a new tab or in a pop-up window.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**.
#. Choose **Default Configuration** and locate **Log Open Mode**.
#. Select **New tab** or **Pop-up**.

   .. note::

      -  **New tab**: Logs are opened on a new page.
      -  **Pop-up**: Logs are opened in a pop-up window on the current page.

#. Click **Save** to save the settings.

.. |image1| image:: /_static/images/en-us_image_0000002269204977.png
.. |image2| image:: /_static/images/en-us_image_0000002234245540.png
