:original_name: dataartsstudio_01_0435.html

.. _dataartsstudio_01_0435:

Developing a Job
================

This section describes how to develop and configure a job.

Prerequisites
-------------

-  You have created a job. For details about how to create a job, see :ref:`Creating a Job <dataartsstudio_01_0434>`.
-  You have locked the job. Otherwise, you must click **Lock** so that you can develop the job. A job you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0901__li156131452182514>`.

Compiling Job Nodes
-------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click the name of a batch processing job or real-time processing job in pipeline mode to access the job development page.

#. Drag a desired node to the canvas, move the mouse over the node, and select the |image1| icon and drag it to connect to another node.

   .. note::

      It is recommended that each job contain a maximum of 200 nodes.


   .. figure:: /_static/images/en-us_image_0000001373168901.png
      :alt: **Figure 2** Compiling a job

      **Figure 2** Compiling a job

#. Configure node functions. Right-click a node icon on the canvas and select a function as needed. :ref:`Table 1 <dataartsstudio_01_0435__en-us_topic_0099797007_table13918279378>` lists the available functions.

   .. _dataartsstudio_01_0435__en-us_topic_0099797007_table13918279378:

   .. table:: **Table 1** Node functions

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Configure                         | Goes to the **Node Property** page of the node.                                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Delete                            | Deletes one or more nodes at the same time.                                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  Deleting one node: Right-click the node icon in the canvas and choose **Delete** or press the **Delete** shortcut key.                                                                                                                                                                                                                                                                                                                               |
      |                                   | -  Deleting multiple nodes: Click the icons of the nodes to be deleted in the canvas while holding on **Ctrl**, right-click the blank area of the current job canvas, and choose **Delete** or press the **Delete** shortcut key.                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Copy                              | Copies one or more nodes to any job.                                                                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  Single-node copy: You can either right-click the node icon in the canvas, choose **Copy**, and paste the node to a target location, or click the node icon in the canvas and press **Ctrl+C** and **Ctrl+V** to paste the node to a target location. The copied node carries the configuration information of the original node.                                                                                                                     |
      |                                   | -  Multi-node copy: Click the icons of the nodes to be copied in the canvas while holding on **Ctrl**. Then you can either right-click the blank area of the canvas, choose **Copy**, and paste the nodes to a target location, or press **Ctrl+C** and **Ctrl+V** to paste the nodes to a target location. The copied node carries the configuration information of the original node, but does not contain the connection relationship between nodes. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Test Run                          | Runs the node for a test.                                                                                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Test from Current Node            | This option is available only for batch processing jobs. It tests the current and subsequent nodes.                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add/Delete Connection             | Adds or deletes a connection between two nodes.                                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Edit CDM Job                      | This option is available only for CDM jobs. After selecting a CDM cluster and a job, you can go to the CDM job editing page to modify the job.                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | View Job Log                      | This option is available only for CDM jobs. When a CDM job is running, you can right-click the CDM job node and select **View Job Log** from the shortcut menu to go to the job monitoring page and view logs to help developers demarcate and locate job running exceptions.                                                                                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Edit Script                       | This option is available only for the node associated with a script. Goes to the script editing page and edits the associated script.                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add Note                          | Adds a note to the node. Each node can have multiple notes.                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) Configure line functions. Right-click the line connecting two nodes on the canvas. **Delete** and **Set Condition** are displayed. You can select them as needed.

   -  **Delete**: Deletes the line connecting the nodes.

   -  **Set Condition**: In the displayed dialog box, you can enter a ternary expression using the EL expression syntax. If the result of the ternary expression is **true**, subsequent nodes will be connected. Otherwise, subsequent nodes will be skipped.

      The following figure shows a typical ternary expression. If the execution result of the DQM node is **true**, subsequent nodes will be connected. If the execution result is **false** and the **Failure Policy** is **Skip all subsequent nodes**, the next node A and all nodes following node A will be skipped.

      |image2|

      For details about the EL expression syntax, see :ref:`Expression Overview <dataartsstudio_01_0494>`.

#. Configure node properties by following the instructions in :ref:`Node Overview <dataartsstudio_01_0442>`.

#. Configure node properties Click a node in the canvas. On the displayed **Node Properties** page, configure node properties. For details, see :ref:`Node Overview <dataartsstudio_01_0442>`.

Configuring Basic Job Information
---------------------------------

After you configure the owner and priority for a job, you can search for the job by the owner and priority. The procedure is as follows:

Click the **Basic Info** tab on the right of the canvas to expand the configuration page and configure job parameters, as listed in :ref:`Table 2 <dataartsstudio_01_0435__en-us_topic_0099797007_table723651785>`.

.. _dataartsstudio_01_0435__en-us_topic_0099797007_table723651785:

.. table:: **Table 2** Basic job information

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================================================================================+
   | Owner                             | An owner configured during job creation is automatically matched. This parameter value can be modified.                                                                                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Executor                          | User that executes the job. When you enter an executor, the job is executed by the executor. If the executor is left unspecified, the job is executed by the user who submitted the job for startup.                                                                               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Job Agency                        | After an agency is configured, the job interacts with other services as an agency during job execution.                                                                                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Priority                          | Priority configured during job creation is automatically matched. This parameter value can be modified.                                                                                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Execution Timeout                 | Timeout of the job instance. If this parameter is set to 0 or is not set, this parameter does not take effect. If the notification function is enabled for the job and the execution time of the job instance exceeds the preset value, the system sends a specified notification. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Custom Parameter                  | Set the name and value of the parameter.                                                                                                                                                                                                                                           |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Job Label                         | Configure job labels to manage jobs by category.                                                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                                    |
   |                                   | Click **Add** to add a tag to the job. You can also select a tag configured in :ref:`Managing Job Labels <dataartsstudio_01_0532>`.                                                                                                                                                |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0435__en-us_topic_0099797007_section754991272419:

Configuring Job Parameters
--------------------------

Job parameters can be globally used in any node in jobs. The procedure is as follows:

Click the blank area in the canvas and then the **Parameter Setup** tab on the right, and configure the parameters listed in :ref:`Table 3 <dataartsstudio_01_0435__en-us_topic_0099797007_table20701161192718>`.

.. _dataartsstudio_01_0435__en-us_topic_0099797007_table20701161192718:

.. table:: **Table 3** Job parameter setup

   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Function                          | Description                                                                                                |
   +===================================+============================================================================================================+
   | **Variable Parameter**            |                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add** and enter the variable parameter name and parameter value in the text boxes.                 |
   |                                   |                                                                                                            |
   |                                   | -  Parameter Name                                                                                          |
   |                                   |                                                                                                            |
   |                                   |    Only letters, numbers, hyphens, and underscores (_) are allowed.                                        |
   |                                   |                                                                                                            |
   |                                   | -  Parameter Value                                                                                         |
   |                                   |                                                                                                            |
   |                                   |    -  The string type of parameter value is a character string, for example, **str1**.                     |
   |                                   |    -  The numeric type of parameter value is a number or operation expression.                             |
   |                                   |                                                                                                            |
   |                                   | After the parameter is configured, it is referenced in the format of **$**\ {*parameter name*} in the job. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Modify                            | Change the parameter name or value in the corresponding text boxes.                                        |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Mask                              | If the parameter value is a key, click |image3| to mask the value for security purposes.                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image4| next to the parameter name and value text boxes to delete the job parameter.                |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | **Constant Parameter**            |                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Add                               | Click **Add** and enter the constant parameter name and parameter value in the text boxes.                 |
   |                                   |                                                                                                            |
   |                                   | -  Parameter name                                                                                          |
   |                                   |                                                                                                            |
   |                                   |    Only letters, numbers, hyphens, and underscores (_) are allowed.                                        |
   |                                   |                                                                                                            |
   |                                   | -  Parameter value                                                                                         |
   |                                   |                                                                                                            |
   |                                   |    -  The string type of parameter value is a character string, for example, **str1**.                     |
   |                                   |    -  The numeric type of parameter value is a number or operation expression.                             |
   |                                   |                                                                                                            |
   |                                   | After the parameter is configured, it is referenced in the format of **$**\ {*parameter name*} in the job. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Modify                            | Modify the parameter name and parameter value in text boxes and save the modifications.                    |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+
   | Delete                            | Click |image5| next to the parameter name and value text boxes to delete the job parameter.                |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------+

Testing and Saving the Job
--------------------------

After a job is configured, complete the following operations:

**Batch processing job**

#. Click |image6| to test the job.
#. After the test is completed, click |image7| to save the job configuration information. If the test fails, modify the parameters as prompted and run the test again.

**Processing jobs in real time**

#. Click |image8| to save the job configuration.

.. |image1| image:: /_static/images/en-us_image_0000001322088260.png
.. |image2| image:: /_static/images/en-us_image_0000001322408148.png
.. |image3| image:: /_static/images/en-us_image_0000001321928572.png
.. |image4| image:: /_static/images/en-us_image_0000001321928576.png
.. |image5| image:: /_static/images/en-us_image_0000001321928576.png
.. |image6| image:: /_static/images/en-us_image_0000001322248164.png
.. |image7| image:: /_static/images/en-us_image_0000001373288605.png
.. |image8| image:: /_static/images/en-us_image_0000001373288605.png
