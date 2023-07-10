:original_name: dataartsstudio_01_0583.html

.. _dataartsstudio_01_0583:

IF Statements
=============

When developing and orchestrating jobs in DataArts Factory, you can use IF statements to determine the branch to execute.

This section describes how to use IF statements in the following scenarios:

-  :ref:`Determining the IF Statement Branch to Be Executed Based on the Execution Status of the Previous Node <dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_section14991730115912>`
-  :ref:`Determining the IF Statement Branch to Be Executed Based on the Execution Result of the Previous Node <dataartsstudio_01_0583__en-us_topic_0000001162343901_section191402715452>`
-  :ref:`Configuring the Policy for Executing a Node with Multiple IF Statements <dataartsstudio_01_0583__section1626375417376>`

IF statements use EL expressions. You can select EL expressions and follow the instruction in this section to develop jobs.

For details about how to use EL expressions, see :ref:`EL Expressions <dataartsstudio_01_0494>`.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_section14991730115912:

Determining the IF Statement Branch to Be Executed Based on the Execution Status of the Previous Node
-----------------------------------------------------------------------------------------------------

**Scenario**

Generally, you can determine the IF statement branch to be executed based on whether the previous CDM node is successfully executed. For details on how to set IF statements, see :ref:`Figure 1 <dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320>`.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320:

.. figure:: /_static/images/en-us_image_0000001321928516.png
   :alt: **Figure 1** Example job

   **Figure 1** Example job

**Configuration Method**

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**. The DataArts Factory console is displayed.

#. On the **Develop Job** page, create a job, drag a CDM node and two Dummy nodes and drop them on the canvas in the right pane. Click and hold |image1| to connect the CDM node to the Dummy nodes, as shown in :ref:`Figure 1 <dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320>`. Set the **Failure Policy** for the CDM node to **Go to the next node**.

#. Right-click the connection line and select **Set Condition**. In the **Edit EL Expression** dialog box, enter the IF statement in the text box.

   Each statement branch requires an IF statement. The IF statement is a ternary expression based on the EL expression syntax. If the result of the ternary expression is **true**, subsequent nodes will be connected. Otherwise, subsequent nodes will be skipped.

   In this demo, the **#{Job.getNodeStatus("node_name")}** EL expression is used to obtain the execution status of a specified node. If the execution is successful, **success** is returned; otherwise, **fail** is returned. In this example, the IF statement expressions are as follows:

   -  The IF statement expression for branch A is **#{(Job.getNodeStatus("CDM")) == "success" ?**. "true" : "false"}
   -  The IF statement expression for branch B is **#{(Job.getNodeStatus("CDM")) == "fail" ?**. "true" : "false"}

   After entering the IF statement expression, you can select either **Skip all subsequent nodes** or **Skip the next node** for **Failure Policy**. After the configuration is complete, click **OK** to save the job.


   .. figure:: /_static/images/en-us_image_0000001322088204.png
      :alt: **Figure 2** Configuring a failure policy

      **Figure 2** Configuring a failure policy

#. Click **Test** to test the job and view the execution result on the **Monitor Instance** page.

#. After the job is executed, view the job instance running result on the **Monitor Instance** page. The execution result meets the expectation. If the execution result is **fail**, branch A is skipped and branch B is executed.


   .. figure:: /_static/images/en-us_image_0000001373288553.png
      :alt: **Figure 3** Job execution result

      **Figure 3** Job execution result

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_section191402715452:

Determining the IF Statement Branch to Be Executed Based on the Execution Result of the Previous Node
-----------------------------------------------------------------------------------------------------

**Scenario Description**

Scenario: Use the execution result of the select statement on the HIVE SQL node as a parameter to determine the IF statement branch to be executed.

The execution result of the select statement on the HIVE SQL node is a two-dimensional array. To obtain the values in the array, use the EL expression **#{Loop.dataArray[][]}**. Currently, only the For Each node supports this expression. Therefore, you need to connect the HIVE SQL node to a For Each node. :ref:`Figure 4 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135>` shows the job orchestration.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135:

.. figure:: /_static/images/en-us_image_0000001322088208.png
   :alt: **Figure 4** Example job

   **Figure 4** Example job

Key configurations of the For Each node are as follows:

-  **Dataset**: Enter the execution result of the select statement on the HIVE SQL node. Use the **#{Job.getNodeOutput('HIVE')}** expression, where **HIVE** is the name of the previous node.
-  **Job Running Parameter**: Enter the parameter defined in the sub-job. Transfer the output of the previous node of the main job to the sub-job for use. The variable name is **result**, and its value is a column in the dataset. The EL expression **#{Loop.dataArray[0][0]}** is used.

The sub-job selected on the For Each node determines the IF statement branch to be executed based on the job running parameter transferred from the For Each node. :ref:`Figure 5 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225>` shows the job orchestration.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225:

.. figure:: /_static/images/en-us_image_0000001322248104.png
   :alt: **Figure 5** Example sub-job

   **Figure 5** Example sub-job

The IF statement is the key configuration of the subjob. This example uses the expression **${result}** to obtain the value of the job parameter.

.. note::

   Do not use the **#{Job.getParam("job_param_name")}** EL expression because this expression can only obtain the values of the parameters configured in the current job, but cannot obtain the parameter values transferred from the parent job or the global variables configured in the workspace. The expression only works for the current job.

   To obtain the parameter values passed from the parent job and the global variables configured for the workspace, you are advised to use the **${job_param_name}** expression.

**Configuration Method**

Developing a Subjob

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**. The DataArts Factory console is displayed.

#. On the **Develop Job** page, create a data development subjob named **foreach**. Drag four Dummy nodes and drop them on the canvas, click and hold |image2| to connect them, as shown in :ref:`Figure 5 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225>`.

#. Right-click the connection line and select **Set Condition**. In the **Edit EL Expression** dialog box, enter the IF statement in the text box.

   Each statement branch requires an IF statement. The IF statement is a ternary expression based on the EL expression syntax. If the result of the ternary expression is **true**, subsequent nodes will be connected. Otherwise, subsequent nodes will be skipped.

   -  For the **>5** branch, the IF statement expression is **#{${result} > 5 ? "true" : "false"}**.
   -  For the **=5** branch, the IF statement expression is **#{${result} == 5 ? "true" : "false"}**.
   -  For the **<5** branch, the IF statement expression is **#{${result} < 5 ? "true" : "false"}**.

   After entering the IF statement expression, you can select either **Skip all subsequent nodes** or **Skip the next node** for **Failure Policy**.

#. Configure job parameters. Set the parameter name to **result**. This parameter is only used by the For Each node in the main job **testif** to identify subjob parameters. You do not need to set the parameter value.


   .. figure:: /_static/images/en-us_image_0000001373408237.png
      :alt: **Figure 6** Configuring job parameters

      **Figure 6** Configuring job parameters

#. Save the job.

Developing a Job
----------------

#. On the **Develop Job** page, create a data development job named **testif**. Drag a HIVE SQL node and a For Each node and drop them on the canvas. Click and hold |image3| to connect the nodes, as shown in :ref:`Figure 4 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135>`.

#. Configure properties for the HIVE SQL node. Reference the following SQL script (there is no special requirement for other properties):

   .. code-block::

      SELECT count(*) FROM student // Count from the student table. The script execution result is a two-dimensional array.


   .. figure:: /_static/images/en-us_image_0000001322248112.png
      :alt: **Figure 7** HIVE SQL script execution result

      **Figure 7** HIVE SQL script execution result

#. Configure properties for the For Each node.

   -  **Subjob in a Loop**: Select **foreach**, the subjob that has been developed.
   -  **Dataset**: Enter the execution result of the select statement on the HIVE SQL node. Use the **#{Job.getNodeOutput('HIVE')}** expression, where **HIVE** is the name of the previous node.
   -  **Job Running Parameter**: Enter the parameter defined in the sub-job. Transfer the output of the previous node of the main job to the sub-job for use. The variable name is **result** (parameter name of the subjob), and its value is a column in the dataset. The EL expression **#{Loop.dataArray[0][0]}** is used.


   .. figure:: /_static/images/en-us_image_0000001373288549.png
      :alt: **Figure 8** Properties of the For Each node

      **Figure 8** Properties of the For Each node

#. Save the job.

Testing the Main Job

#. Click **Test** above the main job canvas to test the job. After the main job is executed, the subjob is automatically invoked through the For Each node and executed.

#. In the navigation pane on the left, choose **Monitor Instance** to view the job execution result.

#. After the job is executed, view the execution result of the subjob **foreach** on the **Monitor Instance** page. The execution result meets the expectation. Currently, the execution result of the Hive SQL statement is **1**. Therefore, the **>5** and **=5** branches are skipped, and the **<5** branch is successfully executed.


   .. figure:: /_static/images/en-us_image_0000001373168849.png
      :alt: **Figure 9** Execution result of the subjob

      **Figure 9** Execution result of the subjob

.. _dataartsstudio_01_0583__section1626375417376:

Configuring the Policy for Executing a Node with Multiple IF Statements
-----------------------------------------------------------------------

If the execution of a node depends on multiple IF statements, the policy for executing the node can be **AND** or **OR**.

If you choose the **OR** policy, the node will be executed if any one of the IF statements is met.

If you choose the **AND** policy, the node will be executed only if all of the IF statements are met.

If you choose neither, the **OR** policy will be used.

.. _dataartsstudio_01_0583__fig1727474115310:

.. figure:: /_static/images/en-us_image_0000001373288557.png
   :alt: **Figure 10** A job with multiple IF statements

   **Figure 10** A job with multiple IF statements

**Configuration Method**

Configure the execution policy.

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**. The DataArts Factory console is displayed.

#. On the DataArts Factory console, choose **Configuration** > **Configure** > **Default Configuration**.

#. .. _dataartsstudio_01_0583__li1065634413613:

   Select **AND** or **OR** for **Multi-IF Policy**.

#. Click **Save**.

Develop a job.

#. On the **Develop Job** page, create a data development job.

#. Drag three DWS SQL operators as parent nodes and one Python operator as a child node to the canvas. Click and hold |image4| to connect the nodes to orchestrate the job shown in :ref:`Figure 10 <dataartsstudio_01_0583__fig1727474115310>`.

#. Right-click the connection line and select **Set Condition**. In the **Edit EL Expression** dialog box, enter the IF statement in the text box.

   Each statement branch requires an IF statement. The IF statement is a ternary expression based on the EL expression syntax.

   -  The IF statement expression for the test1 node is **#{(Job.getNodeStatus("test1")) == "success" ?** **"true" : "false"},**
   -  The IF statement expression for the test2 node is **#{(Job.getNodeStatus("test2")) == "success" ?** **"true" : "false"},**
   -  The IF statement expression for the test3 node is **#{(Job.getNodeStatus("test3")) == "success" ?** **"true" : "false"},**

   The expression of each node is determined using the IF statement based on the execution status of the previous node.

   After entering the IF statement expression, you can select either **Skip all subsequent nodes** or **Skip the next node** for **Failure Policy**.

Test the job.

#. Click **Save** above the canvas to save the job.

#. Click **Test** above the canvas to test the job.

   If **test1** is executed successfully, the corresponding IF statement is true.

   If **test2** is executed successfully, the corresponding IF statement is true.

   If **test3** fails to be executed, the corresponding IF statement is false.

   If :ref:`Multi-IF Policy <dataartsstudio_01_0583__li1065634413613>` is set to **OR**, the **showtables** node is executed and the job execution is complete.


   .. figure:: /_static/images/en-us_image_0000001373408225.png
      :alt: **Figure 11** How the job runs if Multi-IF Policy is OR

      **Figure 11** How the job runs if Multi-IF Policy is OR

   If :ref:`Multi-IF Policy <dataartsstudio_01_0583__li1065634413613>` is set to **AND**, the **showtables** node is skipped and the job execution is complete.


   .. figure:: /_static/images/en-us_image_0000001373168845.png
      :alt: **Figure 12** How the job runs if Multi-IF Policy is AND

      **Figure 12** How the job runs if Multi-IF Policy is AND

.. |image1| image:: /_static/images/en-us_image_0000001322408088.png
.. |image2| image:: /_static/images/en-us_image_0000001321928520.png
.. |image3| image:: /_static/images/en-us_image_0000001373088033.png
.. |image4| image:: /_static/images/en-us_image_0000001373088045.png
