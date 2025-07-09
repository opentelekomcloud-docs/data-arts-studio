:original_name: dataartsstudio_01_7523.html

.. _dataartsstudio_01_7523:

Setting the Job Scheduling Time to the Last Day of Each Month
=============================================================

Scenario
--------

When configuring job scheduling, you can set the scheduling time to the last day of each month using either of the two methods provided in the following table.

.. table:: **Table 1** Setting the scheduling time to the last day of each month

   +------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | Method                                                                                                                             | Advantage                                                                                                                                                      | Procedure                                                      |
   +====================================================================================================================================+================================================================================================================================================================+================================================================+
   | Set the scheduling frequency to every day and use a condition expression to determine whether a day is the last day of each month. | This method applies to multiple scenarios. You can compile condition expressions to flexibly schedule jobs, for example, on the last day or 7th of each month. | :ref:`Method 1 <dataartsstudio_01_7523__section9574744142213>` |
   +------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | Set the scheduling frequency to every month and select the last day of each month.                                                 | You can set a specific job scheduling time instead of compiling any statements.                                                                                | :ref:`Method 2 <dataartsstudio_01_7523__section20721666465>`   |
   +------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+

.. _dataartsstudio_01_7523__section9574744142213:

Method 1
--------

In DataArts Studio, create a job that is scheduled every day and add an empty Dummy node (which does not process data) to the job. You can set a condition expression on the connection line between the Dummy node and its subsequent node to check whether the current day is the last day of the current month. If it is the last day, the subsequent nodes are executed. Otherwise, the subsequent nodes are skipped.

#. In the left navigation pane of the DataArts Factory console, choose **Data Development** > **Develop Job**.

#. Set **Scheduling Frequency** to **Every day**.


   .. figure:: /_static/images/en-us_image_0000002270791280.png
      :alt: **Figure 1** Setting Scheduling Frequency to Every day

      **Figure 1** Setting Scheduling Frequency to Every day

#. Right-click the connection line between the Dummy node and its subsequent node and select **Set Condition** to configure a condition expression that is used to determine whether to execute the subsequent node.


   .. figure:: /_static/images/en-us_image_0000002305408021.png
      :alt: **Figure 2** Configuring a condition expression

      **Figure 2** Configuring a condition expression

#. Configure the expression as follows:

   .. code-block::

      #{DateUtil.getDay(DateUtil.addDays(Job.planTime,1)) == 1 ? "true" : "false"}

   The expression is used to obtain the current time and check whether the next day is 1st of a month. If yes, the current day is the last day of the current month, and the subsequent node will be executed; if no, the subsequent node will be skipped.


   .. figure:: /_static/images/en-us_image_0000002270791276.png
      :alt: **Figure 3** Condition expression

      **Figure 3** Condition expression

   For example, if you want a job to be executed on the last day and seventh day of each month, perform the following operation:

   Configure the following expression to check whether the current day is 7th:

   .. code-block::

      #{DateUtil.getDay(Job.planTime) == 7 ? "true" : "false"}

.. _dataartsstudio_01_7523__section20721666465:

Method 2
--------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Click **Scheduling Setup** on the right of the job canvas.

#. Set **Scheduling Type** to **Run periodically**, **Scheduling Frequency** to **Every month**, and **Select Time** to **the last day of each month**.


   .. figure:: /_static/images/en-us_image_0000002305441089.png
      :alt: **Figure 4** Setting the scheduling time to the last day of each month

      **Figure 4** Setting the scheduling time to the last day of each month

   After the scheduling time is configured, the job will be automatically executed on the last day of each month.
