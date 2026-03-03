:original_name: dataartsstudio_01_0720.html

.. _dataartsstudio_01_0720:

Creating a Comparison Job
=========================

Scenario
--------

Data comparison is critical to ensure data consistency in data development and migration. The cross-source data comparison capability is the key to checking consistency of the data before and after migration or processing. This section describes how to create a comparison job in the DataArts Quality module of DataArts Studio to verify consistency between a DLI and DWS connection.

Environment Preparations
------------------------

Create the data sources to compare, that is, create different types of data connections in the Management Center.

Procedure
---------

#. Create different types of data connections.

   a. Create a DLI data connection. On the **Management Center** page, click **Create Data Connection**. In the displayed dialog box, select **DLI** for **Data Connection Type**, enter a connection name, and click **Test**. If the message "Connected." is displayed, click **OK**.

      |image1|

   b. Create a DWS data connection. On the **Management Center** page, click **Create Data Connection**. In the displayed dialog box, select **DWS** for **Data Connection Type**, enter a connection name, set other required parameters, and click **Test**. If the message "Connected." is displayed, click **OK**.

      |image2|

#. Create a comparison job.

   a. On the **DataArts Quality** page, choose **Comparison Jobs** in the navigation pane.

   b. Click **Create**. On the **Create Comparison Job** page, set basic information about the comparison job.


      .. figure:: /_static/images/en-us_image_0000002269116437.png
         :alt: **Figure 1** Configuring basic information

         **Figure 1** Configuring basic information

   c. Click **Next** to go to the **Define Rule** page. Click |image3| on the rule card to configure the rule.

      |image4|

      |image5|

      .. note::

         -  You need to configure information about both the source and destination. For how to configure the source connection, see :ref:`DWS Connection Parameters <dataartsstudio_01_1300>`. For how to configure the destination connection, see :ref:`DLI Connection Parameters <dataartsstudio_01_1301>`.
         -  When configuring **Alarm Condition**, **${1_1}** indicates the number of rows in the source table, and **${2_1}** indicates the number of rows in the destination table. In the preceding figure, the alarm condition **${1_1}!=${2_1}** indicates that an alarm is generated when the number of rows in the source table is inconsistent with that in the destination table.

   d. Click **Next** and set subscription parameters.

      |image6|

      .. note::

         If you enable notification, **Alarm triggered** indicates that a notification is sent to the SMN topic when an alarm is generated for the job, and **Run successfully** indicates that a notification is sent to the SMN topic when no alarm is generated for the job.

   e. Click **Next** and set scheduling parameters.

      |image7|

      .. note::

         **Once** indicates that the job needs to be manually executed, and **On schedule** indicates that the job is executed automatically based on your configuration. The configuration in the preceding figure indicates that the job is automatically executed every 15 minutes on Oct 27, 2020.

   f. Click **Submit**.

#. View the comparison job.

   a. In the comparison job list, locate the created job and click **Run** in the **Operation** column.

   b. On the displayed **O&M** page, locate the row that contains the comparison job and click **Details** in the **Operation** column to view the running results and logs.

      |image8|

Analyzing the Comparison Result
-------------------------------

In the running result, the left pane displays the execution result of the rule for source table rows, and the right pane displays the execution result of the rule for destination table rows.

The error rate indicates the difference between the number of rows of the source and destination tables. If the error rate is 0, the source and destination tables have the same number of rows.

|image9|

.. |image1| image:: /_static/images/en-us_image_0000002234077224.png
.. |image2| image:: /_static/images/en-us_image_0000002269196517.png
.. |image3| image:: /_static/images/en-us_image_0000002234237088.png
.. |image4| image:: /_static/images/en-us_image_0000002234237080.png
.. |image5| image:: /_static/images/en-us_image_0000002234237064.png
.. |image6| image:: /_static/images/en-us_image_0000002269196497.png
.. |image7| image:: /_static/images/en-us_image_0000002269116425.png
.. |image8| image:: /_static/images/en-us_image_0000002234077228.png
.. |image9| image:: /_static/images/en-us_image_0000002269116445.png
