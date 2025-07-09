:original_name: dataartsstudio_01_7564.html

.. _dataartsstudio_01_7564:

Configuring a Yearly Scheduled Job
==================================

Scenario
--------

This section describes how to configure a job that is scheduled at a specified time of a year.

Procedure
---------

In DataArts Studio, create a job that is scheduled every month and add an empty Dummy node (which does not process data) to the job. You can set a condition expression on the connection line between the Dummy node and its subsequent node to check whether the current time falls in the specified day (for example, June 29, 2023) for scheduling the job. If yes, the subsequent node is executed. Otherwise, the subsequent node is skipped.

#. In the left navigation pane of the DataArts Factory console, choose **Data Development** > **Develop Job**.

#. Set **Scheduling Frequency** to **Every month**.


   .. figure:: /_static/images/en-us_image_0000002270848246.png
      :alt: **Figure 1** Setting Scheduling Frequency to Every month

      **Figure 1** Setting Scheduling Frequency to Every month

#. Right-click the connection line between the Dummy node and its subsequent node and select **Set Condition** to configure a condition expression that is used to determine whether to execute the subsequent node.


   .. figure:: /_static/images/en-us_image_0000002305441189.png
      :alt: **Figure 2** Configuring a condition expression

      **Figure 2** Configuring a condition expression

#. Configure the expression as follows:

   .. code-block::

      #{DateUtil.getMonth(Job.planTime) == 6 ? "true" : "false"}

   The expression is used to obtain the current time and check whether it falls in June. If yes, the subsequent node will be executed; if no, the subsequent node will be skipped.


   .. figure:: /_static/images/en-us_image_0000002305408129.png
      :alt: **Figure 3** Condition expression

      **Figure 3** Condition expression
