:original_name: dataartsstudio_01_0584.html

.. _dataartsstudio_01_0584:

Obtaining the Output of an SQL Node
===================================

This section describes how to obtain the output of an SQL node and apply the output to subsequent nodes or judgment in job development.

Scenario
--------

When you use EL expression **#{Job.getNodeOutput("Name of the previous node")}** to obtain the output of the previous node, the output is a two-dimensional array, for example, **[["Dean",...,"08"],...,["Smith",...,"53"]]**. To obtain the values in the array, use either of the methods provided in :ref:`Table 1 <dataartsstudio_01_0584__table8346195375220>`.

.. _dataartsstudio_01_0584__table8346195375220:

.. table:: **Table 1** Methods for obtaining output values

   +-----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                                                                                              | Key Configuration                                                                                                                                                                                                                                   | Application Scenario Requirements                                                                                                                                                                                                                                 |
   +=====================================================================================================+=====================================================================================================================================================================================================================================================+===================================================================================================================================================================================================================================================================+
   | :ref:`Obtaining Output Value Using StringUtil <dataartsstudio_01_0584__section14854144844313>`      | If the output of the SQL node contains only one field, for example **[["11"]]**, you can use the StringUtil EL expression with an embedded object to split the two-dimensional array and obtain the field value in the output of the previous node. | This method is easy to use but has the following requirements on application scenarios:                                                                                                                                                                           |
   |                                                                                                     |                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                   |
   |                                                                                                     | #{StringUtil.split(StringUtil.split(StringUtil.split(Job.getNodeOutput("**Name of the previous node**"),"]")[0],"[")[0],"\\\\"")[0]}                                                                                                                | -  The output of the previous SQL node contains only one field, for example, **[["11"]]**.                                                                                                                                                                        |
   |                                                                                                     |                                                                                                                                                                                                                                                     | -  The output value is a string. The application scenario must support the string data type. For example, if the IF condition needs to be used to judge the size of the output value, the string type is not supported. In this case, this method cannot be used. |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Output Values Using the For Each Node <dataartsstudio_01_0584__section23728149243>` | Use the For Each node to cyclically obtain the values in the two-dimensional array in the dataset.                                                                                                                                                  | This method is applicable to more scenarios, though jobs need to be split into main jobs and subjobs.                                                                                                                                                             |
   |                                                                                                     |                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                   |
   |                                                                                                     | -  For Each node dataset: #{Job.getNodeOutput('**Name of the previous node**')}                                                                                                                                                                     |                                                                                                                                                                                                                                                                   |
   |                                                                                                     | -  Subjob parameters of the For Each node: #{Loop.current[**Index**]}                                                                                                                                                                               |                                                                                                                                                                                                                                                                   |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0584__section14854144844313:

Obtaining Output Value Using StringUtil
---------------------------------------

**Scenario**

The StringUtil EL expression with an embedded object is used to split the two-dimensional array result and obtain the output field value of the previous node, which is a string.

In this example, the MRS Hive SQL node returns a two-dimensional array that contains a single field. The data sent by the Kafka Client node is defined as the StringUtil EL expression with an embedded object. You can use this expression to split the two-dimensional array and obtain the output field value of the MRS Hive SQL node.

.. note::

   To make it easy to view the obtained value, this example uses the Kafka Client node. In practice, you can select a subsequent node type as needed. By using a StringUtil EL expression with an embedded object on the node, you can obtain the data value returned by the previous node.

.. _dataartsstudio_01_0584__fig1785564894317:

.. figure:: /_static/images/en-us_image_0000002269116113.png
   :alt: **Figure 1** Example job

   **Figure 1** Example job

The key configuration of the Kafka Client node is the **Sent Content** parameter. Set it as follows:

.. code-block::

   #{StringUtil.split(StringUtil.split(StringUtil.split(Job.getNodeOutput("count95"),"]")[0],"[")[0],"\\"")[0]}

**Configuration Method**

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**.

#. Create table **student_score**. Create a temporary Hive SQL script, select a Hive connection and database, paste the following SQL statement, and run the script. After the script is successfully executed, delete it.

   .. code-block::

      CREATE TABLE `student_score` (`name` String COMMENT '', `score` INT COMMENT '');
      INSERT INTO
          student_score
      VALUES
          ('ZHAO', '90'),
          ('QIAN', '88'),
          ('SUN', '93'),
          ('LI', '94'),
          ('ZHOU', '85'),
          ('WU', '79'),
          ('ZHENG', '87'),
          ('WANG', '97'),
          ('FENG', '83'),
          ('CEHN', '99');

#. .. _dataartsstudio_01_0584__li19298135016154:

   Create the Hive SQL script to be invoked by the MRS Hive SQL node. Create a Hive SQL script named **count95**, select a Hive connection and database, paste the following SQL statement, and submit a version.

   .. code-block::

      --Obtain the number of students whose scores are higher than 95 from the student_score table.--
      SELECT count(*) FROM student_score WHERE score> "95" ;

#. On the **Develop Job** page, create a data development job. Drag an MRS Hive SQL node and a Kafka Client node and drop them on the canvas. Click and hold |image1| to connect the nodes, as shown in :ref:`Figure 1 <dataartsstudio_01_0584__fig1785564894317>`.

#. Configuring parameters for an MRS Hive SQL node Select the **count95** script submitted in :ref:`4 <dataartsstudio_01_0584__li19298135016154>` for **SQL script** and select a Hive connection and database.


   .. figure:: /_static/images/en-us_image_0000002269196257.png
      :alt: **Figure 2** Configuring parameters for an MRS Hive SQL node

      **Figure 2** Configuring parameters for an MRS Hive SQL node

#. Configure parameters for the Kafka Client node. Set **Sent Content** to **#{StringUtil.split(StringUtil.split(StringUtil.split(Job.getNodeOutput("count95"),"]")[0],"[")[0],"\\\\"")[0]}** and select a Kafka connection and a topic name.


   .. figure:: /_static/images/en-us_image_0000002234077004.png
      :alt: **Figure 3** Configuring parameters for the Kafka Client node

      **Figure 3** Configuring parameters for the Kafka Client node

#. After the node configuration is complete, click **Test**. After the job test is successful, right-click the Kafka Client node to view its log. You can find that the two-dimensional array **[["2"]]** returned by the MRS Hive SQL node has been converted to **2**.

   .. note::

      You can set **Sent Content** of the Kafka Client node to **#{Job.getNodeOutput("count95")}** and run the job. Then you can view the log of the Kafka Client node to verify that the result returned by the MRS Hive SQL node is two-dimensional array **[["2"]]**.


   .. figure:: /_static/images/en-us_image_0000002269196209.png
      :alt: **Figure 4** Check the Kafka Client node logs.

      **Figure 4** Check the Kafka Client node logs.

.. _dataartsstudio_01_0584__section23728149243:

Obtaining Output Values Using the For Each Node
-----------------------------------------------

**Scenario**

You can use the For Each node and the EL expression #{Loop.current[0]} with a Loop embedded object to cyclically obtain the output values of the previous node.

In this example, the MRS Hive SQL node returns a two-dimensional array that contains multiple fields. You can use the For Each node which cyclically invokes the subjobs of the Kafka Client node and set **Sent Content** of the Kafka Client node to **#{Loop.current[]}** to obtain the output values of the MRS Hive SQL node.

.. note::

   To make it easy to view the obtained values, this example uses the Kafka Client node as the subjob node of the For Each node. In practice, you can select a subjob node type as needed. By using an EL expression with an embedded Loop object on the node, you can obtain the values returned by the previous node of the For Each node.

Orchestrate the main job shown in :ref:`Figure 5 <dataartsstudio_01_0584__en-us_topic_0000001162343901_fig1639792911135>`. Key configurations of the For Each node are as follows:

-  **Dataset**: Enter the execution result of the select statement on the Hive SQL node. Use the **#{Job.getNodeOutput("select95")}** expression, where **select95** is the name of the previous node.
-  **Subjob Parameter Name**: Enter the parameter name defined in the subjob. Transfer the parameter value defined in the main job to the subjob. Set the subjob parameter names to **name** and **score**, whose values are those in the first and second columns in the dataset, respectively. EL expressions **#{Loop.current[0]}** and **#{Loop.current[1]}** are used.

.. _dataartsstudio_01_0584__en-us_topic_0000001162343901_fig1639792911135:

.. figure:: /_static/images/en-us_image_0000002269116181.png
   :alt: **Figure 5** Example main job

   **Figure 5** Example main job

For the subjobs selected for the For Each node, you must set their parameter names so that the main job can identify the parameter definitions.

.. _dataartsstudio_01_0584__en-us_topic_0000001162343901_fig517111111225:

.. figure:: /_static/images/en-us_image_0000002234236804.png
   :alt: **Figure 6** Example subjob

   **Figure 6** Example subjob

**Configuration Method**

Developing a Subjob

#. Log in to the DataArts Studio console, locate the target DataArts Studio instance, and click **Access** on the instance card.

#. Click the **Workspaces** tab. In the workspace list, locate the target workspace and click **DataArts Factory**.

#. On the **Develop Job** page, create a data development subjob named **EL_test_slave**. Select a Kafka Client node, configure job parameters, and orchestrate the job shown in :ref:`Figure 6 <dataartsstudio_01_0584__en-us_topic_0000001162343901_fig517111111225>`.

   Set the parameter name to **name** and **score**. This parameter is only used by the For Each node in the main job to identify subjob parameters. You do not need to set the parameter value.

#. Configure parameters for the Kafka Client node. Set **Sent Content** to **${name}: ${score}** and select a Kafka connection and a topic name.

   .. note::

      Do not use the **#{Job.getParam("job_param_name")}** EL expression because this expression can only obtain the values of the parameters configured in the current job, but cannot obtain the parameter values transferred from the parent job or the global variables configured in the workspace. The expression only works for the current job.

      To obtain the parameter values passed from the parent job and the global variables configured for the workspace, you are advised to use the **${job_param_name}** expression.


   .. figure:: /_static/images/en-us_image_0000002234076984.png
      :alt: **Figure 7** Configuring parameters for the Kafka Client node

      **Figure 7** Configuring parameters for the Kafka Client node

#. Submit the subjob after the configuration is complete.

Developing a Main Job

#. Go to the **Develop Script** page.

#. Create table **student_score**. Create a temporary Hive SQL script, select a Hive connection and database, paste the following SQL statement, and run the script. After the script is successfully executed, delete it.

   .. code-block::

      CREATE TABLE `student_score` (`name` String COMMENT '', `score` INT COMMENT '');
      INSERT INTO
          student_score
      VALUES
          ('ZHAO', '90'),
          ('QIAN', '88'),
          ('SUN', '93'),
          ('LI', '94'),
          ('ZHOU', '85'),
          ('WU', '79'),
          ('ZHENG', '87'),
          ('WANG', '97'),
          ('FENG', '83'),
          ('CEHN', '99');

#. .. _dataartsstudio_01_0584__li16477457163015:

   Create the Hive SQL script to be invoked by the MRS Hive SQL node. Create a Hive SQL script named **select95**, select a Hive connection and database, paste the following SQL statement, and submit a version.

   .. code-block::

      --Display the names and scores of students whose scores are higher than 95 in the student_score table.--
      SELECT * FROM student_score WHERE score> "95" ;

#. On the **Develop Job** page, create a data development job named **EL_test_master**. Drag a HIVE SQL node and a For Each node and drop them on the canvas. Click and hold |image2| to connect the nodes, as shown in :ref:`Figure 5 <dataartsstudio_01_0584__en-us_topic_0000001162343901_fig1639792911135>`.

#. Configure parameters for the MRS Hive SQL node. Select the **select95** script submitted in :ref:`3 <dataartsstudio_01_0584__li16477457163015>` for **SQL script** and select a Hive connection and database.


   .. figure:: /_static/images/en-us_image_0000002269116161.png
      :alt: **Figure 8** Configuring parameters for an MRS Hive SQL node

      **Figure 8** Configuring parameters for an MRS Hive SQL node

#. Configure properties for the For Each node.

   -  **Subjob in a Loop**: Select **EL_test_slave**, the subjob that has been developed.
   -  **Dataset**: Enter the execution result of the select statement on the Hive SQL node. Use the **#{Job.getNodeOutput("select95")}** expression, where **select95** is the name of the previous node.
   -  **Subjob Parameter Name**: Enter the parameter name defined in the subjob. Transfer the parameter value defined in the main job to the subjob. Set the subjob parameter names to **name** and **score**, whose values are those in the first and second columns in the dataset, respectively. EL expressions **#{Loop.current[0]}** and **#{Loop.current[1]}** are used.


   .. figure:: /_static/images/en-us_image_0000002269116149.png
      :alt: **Figure 9** Configuring properties for the For Each node

      **Figure 9** Configuring properties for the For Each node

#. Save the job.

Testing the Main Job

#. Click **Test** above the main job **EL_test_master** canvas to test the job. After the main job is executed, the subjob **EL_test_slave** is cyclically invoked through the For Each node and executed.

#. In the navigation pane on the left, choose **Monitor Instance** to view the job execution result.

#. After the job is executed, view the cyclic execution result of the subjob **EL_test_slave** on the **Monitor Instance** page.


   .. figure:: /_static/images/en-us_image_0000002234076948.png
      :alt: **Figure 10** Execution result of the subjob

      **Figure 10** Execution result of the subjob

#. View the log of the cyclic execution of subjob **EL_test_slave**. The log shows that the output values of the previous node of the For Each node was obtained through the For Each node and the EL expression with a Loop embedded object.


   .. figure:: /_static/images/en-us_image_0000002269116221.png
      :alt: **Figure 11** Viewing the log

      **Figure 11** Viewing the log

.. |image1| image:: /_static/images/en-us_image_0000002234236776.png
.. |image2| image:: /_static/images/en-us_image_0000002234076960.png
