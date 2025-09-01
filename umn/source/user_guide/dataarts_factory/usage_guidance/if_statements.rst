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

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_section14991730115912:

Determining the IF Statement Branch to Be Executed Based on the Execution Status of the Previous Node
-----------------------------------------------------------------------------------------------------

**Scenario**

Generally, you can determine the IF statement branch to be executed based on whether the previous CDM node is successfully executed. For details on how to set IF statements, see :ref:`Figure 1 <dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320>`.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320:

.. figure:: /_static/images/en-us_image_0000002269116645.png
   :alt: **Figure 1** Example job

   **Figure 1** Example job

**Configuration Method**

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**. The DataArts Factory console is displayed.

#. On the **Develop Job** page, create a job, drag a CDM node and two Dummy nodes and drop them on the canvas in the right pane. Click and hold |image1| to connect the CDM node to the Dummy nodes, as shown in :ref:`Figure 1 <dataartsstudio_01_0583__en-us_topic_0000001162343901_en-us_topic_0000001073100734_fig1727424664320>`.

   Set the **Failure Policy** for the CDM node to **Go to the next node**.


   .. figure:: /_static/images/en-us_image_0000002269196749.png
      :alt: **Figure 2** Configuring the failure policy for the CDM node

      **Figure 2** Configuring the failure policy for the CDM node

#. Right-click the connection line and select **Set Condition**. In the **Edit EL Expression** dialog box, enter the IF statement in the text box.

   Each statement branch requires an IF statement. The IF statement is a ternary expression based on the EL expression syntax. If the result of the ternary expression is **true**, subsequent nodes will be connected. Otherwise, subsequent nodes will be skipped.

   In this demo, the **#{Job.getNodeStatus("node_name")}** EL expression is used to obtain the execution status of a specified node. If the execution is successful, **success** is returned; otherwise, **fail** is returned. In this example, the IF statement expressions are as follows:

   -  The IF statement expression for branch A is **#{(Job.getNodeStatus("CDM")) == "success" ?**. "true" : "false"}
   -  The IF statement expression for branch B is **#{(Job.getNodeStatus("CDM")) == "fail" ?**. "true" : "false"}

   After entering the IF statement expression, you can select either **Skip all subsequent nodes** or **Skip the next node** for **Failure Policy**. After the configuration is complete, click **OK** to save the job.


   .. figure:: /_static/images/en-us_image_0000002234077448.png
      :alt: **Figure 3** Configuring a failure policy

      **Figure 3** Configuring a failure policy

#. Click **Test** to test the job and view the execution result on the **Monitor Instance** page.

#. After the job is executed, view the job instance running result on the **Monitor Instance** page. The execution result meets the expectation. If the execution result is **fail**, branch A is skipped and branch B is executed.


   .. figure:: /_static/images/en-us_image_0000002269196757.png
      :alt: **Figure 4** Job execution result

      **Figure 4** Job execution result

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_section191402715452:

Determining the IF Statement Branch to Be Executed Based on the Execution Result of the Previous Node
-----------------------------------------------------------------------------------------------------

**Scenario Description**

Scenario: Use the Hive SQLnode to collect statistics on the number of people whose score is higher than 85, transfer the execution result as a parameter to the next node, compare the result with the number of people who have passed the test, and determine the IF condition branch to be executed.

Analysis: The execution result of the select statement on the Hive SQL node is a two-dimensional array which contains a single field. Therefore, EL expression **#{Loop.dataArray[][]}** or **#{Loop.current[]}** can be used to obtain the value in the two-dimensional array. Currently, only the For Each node supports loop expressions, so the Hive SQL node needs to be connected to a For Each node.

.. note::

   In this scenario, the loop expression cannot be replaced by the StringUtil expression **#{StringUtil.split(StringUtil.split(StringUtil.split(Job.getNodeOutput("Name of the previous node"),"]")[0],"[")[0],"\\\\"")[0]}** because the StringUtil expression returns a string which cannot be compared with the standard data of the int type.

:ref:`Figure 5 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135>` shows the job orchestration.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135:

.. figure:: /_static/images/en-us_image_0000002234237324.png
   :alt: **Figure 5** Example job

   **Figure 5** Example job

Key configurations of the For Each node are as follows:

-  **Dataset**: Enter the execution result of the select statement on the Hive SQL node. Use the **#{Job.getNodeOutput('HIVE')}** expression, where **HIVE** is the name of the previous node.
-  **Subjob Parameter Name**: Enter the parameter defined in the subjob. Transfer the output of the previous node of the main job to the sub-job for use. The variable name is **result**, and its value is a column in the dataset. The EL expression **#{Loop.dataArray[0][0]}** or **#{Loop.current[]}** is used. This example uses **{Loop.dataArray[0][0]}** as an example.

The sub-job selected on the For Each node determines the IF statement branch to be executed based on the subjob parameter transferred from the For Each node. :ref:`Figure 6 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225>` shows the job orchestration.

.. _dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225:

.. figure:: /_static/images/en-us_image_0000002234077436.png
   :alt: **Figure 6** Example sub-job

   **Figure 6** Example sub-job

The IF statement is the key configuration of the subjob. This example uses the expression **${result}** to obtain the value of the job parameter.

.. note::

   Do not use the **#{Job.getParam("job_param_name")}** EL expression because this expression can only obtain the values of the parameters configured in the current job, but cannot obtain the parameter values transferred from the parent job or the global variables configured in the workspace. The expression only works for the current job.

   To obtain the parameter values passed from the parent job and the global variables configured for the workspace, you are advised to use the **${job_param_name}** expression.

**Configuration Method**

Developing a Subjob

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**. The DataArts Factory console is displayed.

#. On the **Develop Job** page, create a data development subjob For Each. Drag four Dummy nodes and drop them on the canvas, click and hold |image2| to connect them, as shown in :ref:`Figure 6 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig517111111225>`.

#. Right-click the connection line and select **Set Condition**. In the **Edit EL Expression** dialog box, enter the IF statement in the text box.

   Each statement branch requires an IF statement. The IF statement is a ternary expression based on the EL expression syntax. If the result of the ternary expression is **true**, subsequent nodes will be connected. Otherwise, subsequent nodes will be skipped.

   -  For the **>5** branch, the IF statement expression is **#{${result} > 5 ? "true" : "false"}**.
   -  For the **=5** branch, the IF statement expression is **#{${result} == 5 ? "true" : "false"}**.
   -  For the **<5** branch, the IF statement expression is **#{${result} < 5 ? "true" : "false"}**.

   After entering the IF statement expression, you can select either **Skip all subsequent nodes** or **Skip the next node** for **Failure Policy**.

   .. note::

      If an expression contains multiple conditions, you can use \|\| to combine them conditions. The following is an example:

      #{(${result} >= 19 \|\| ${result} <=9) ? "true" : "false"}

#. Configure job parameters. Set the parameter name to **result**. This parameter is only used by the For Each node in the main job **testif** to identify subjob parameters. You do not need to set the parameter value.


   .. figure:: /_static/images/en-us_image_0000002269196765.png
      :alt: **Figure 7** Configuring job parameters

      **Figure 7** Configuring job parameters

#. Save the job.

Developing a Job

#. On the **Develop Job** page, create a data development job named **testif**. Drag a HIVE SQL node and a For Each node and drop them on the canvas. Click and hold |image3| to connect the nodes, as shown in :ref:`Figure 5 <dataartsstudio_01_0583__en-us_topic_0000001162343901_fig1639792911135>`.

#. Configure properties for the HIVE SQL node. Reference the following SQL script (there is no special requirement for other properties):

   .. code-block::

      --Obtain the number of people whose scores are higher than 85 from the student_score table.
      SELECT count(*) FROM student_score WHERE score> "85" ;


   .. figure:: /_static/images/en-us_image_0000002234077496.png
      :alt: **Figure 8** HIVE SQL script execution result

      **Figure 8** HIVE SQL script execution result

#. Configure properties for the For Each node.

   -  **Subjob in a Loop**: Select **foreach**, the subjob that has been developed.
   -  **Dataset**: Enter the execution result of the select statement on the Hive SQL node. Use the **#{Job.getNodeOutput('HIVE')}** expression, where **HIVE** is the name of the previous node.
   -  **Subjob Parameter Name**: Enter the parameter defined in the subjob. Transfer the output of the previous node of the main job to the sub-job for use. The variable name is **result** (parameter name of the subjob), and its value is a column in the dataset. The EL expression **#{Loop.dataArray[0][0]}** is used.


   .. figure:: /_static/images/en-us_image_0000002269196781.png
      :alt: **Figure 9** Properties of the For Each node

      **Figure 9** Properties of the For Each node

#. Save the job.

Testing the Main Job

#. Click **Test** above the canvas to test the main job. After the main job is executed, the subjob is automatically invoked through the For Each node and executed.

#. In the navigation pane on the left, choose **Monitor Instance** to view the job execution result.

#. After the job is executed, view the execution result of the subjob **foreach** on the **Monitor Instance** page. The execution result meets the expectation. Currently, the execution result of the Hive SQL statement is **4**. Therefore, the **>5** and **=5** branches are skipped, and the **<5** branch is successfully executed.


   .. figure:: /_static/images/en-us_image_0000002269196741.png
      :alt: **Figure 10** Execution result of the subjob

      **Figure 10** Execution result of the subjob

.. _dataartsstudio_01_0583__section1626375417376:

Configuring the Policy for Executing a Node with Multiple IF Statements
-----------------------------------------------------------------------

If the execution of a node depends on multiple IF statements, the policy for executing the node can be **AND** or **OR**.

If you choose the **OR** policy, the node will be executed if any one of the IF statements is met.

If you choose the **AND** policy, the node will be executed only if all of the IF statements are met.

If you choose neither, the **OR** policy will be used.

.. _dataartsstudio_01_0583__fig1727474115310:

.. figure:: /_static/images/en-us_image_0000002234237348.png
   :alt: **Figure 11** A job with multiple IF statements

   **Figure 11** A job with multiple IF statements

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

#. Drag three DWS SQL operators as parent nodes and one Python operator as a child node to the canvas. Click and hold |image4| to connect the nodes to orchestrate the job shown in :ref:`Figure 11 <dataartsstudio_01_0583__fig1727474115310>`.

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


   .. figure:: /_static/images/en-us_image_0000002234237268.png
      :alt: **Figure 12** How the job runs if Multi-IF Policy is OR

      **Figure 12** How the job runs if Multi-IF Policy is OR

   If :ref:`Multi-IF Policy <dataartsstudio_01_0583__li1065634413613>` is set to **AND**, the **showtables** node is skipped and the job execution is complete.


   .. figure:: /_static/images/en-us_image_0000002234077444.png
      :alt: **Figure 13** How the job runs if Multi-IF Policy is AND

      **Figure 13** How the job runs if Multi-IF Policy is AND

.. |image1| image:: /_static/images/en-us_image_0000002269116637.png
.. |image2| image:: /_static/images/en-us_image_0000002234237300.png
.. |image3| image:: /_static/images/en-us_image_0000002269196709.png
.. |image4| image:: /_static/images/en-us_image_0000002234237340.png
